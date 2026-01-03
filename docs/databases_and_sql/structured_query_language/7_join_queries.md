Up until now, our database life has been somewhat lonely. We've been dutifully querying single tables, filtering rows, and perhaps aggregating a few numbers. But the real power of the Relational Model isn't in the tables themselves; it's in the *relationships* between them.

Data in the wild is messy and scattered. You don't put the customer's home address in the same row as their order history, because that leads to redundancy and madness. You normalize.  You split things apart.

**JOIN**s are how we put them back together.

To guide us through this chapter, let's imagine databases for a modest Fantasy RPG. We have two primary tables: `Heroes` and `Quests`.

**Table Heroes**

| hero_id | name | class |
|:---|:---|:---|
|1|Aragorn|Ranger|
|2|Gandalf|Wizard|
|3|Gimli|Fighter|
|4|Frodo|Rogue|
|5|Boromir|Fighter|

**Table Quests**

| quest_id | quest_name | assigned_hero_id |
|:---|:---|:---|
|101|Destroy Ring|4|
|102|Protect Ring|1|
|103|Fly Eagles|2|
|104|Polish Axe|NULL|

## 7.1 INNER JOIN
The `INNER JOIN` is the bread and butter of SQL relationships. When you hear someone simply say "join," this is usually what they mean.

An inner join looks at two tables and says, "Show me the rows that match in *both*." It is the intersection. If a hero has no quest, they are invisible here. If a quest has no hero, it is also invisible.

!!! note "The Keyword `INNER`"

    The keyword `INNER` is actually optional in most SQL dialects. Typing `JOIN` is equivalent to `INNER JOIN`. We'll be explicit here for clarity.

### The Syntax

```sql
SELECT Heroes.name, Quests.quest_name
FROM Heroes
INNER JOIN Quests
ON Heroes.hero_id = Quests.assigned_hero_id;
```

We specify the first table in the `FROM` clause, "join" the second table, and then **crucially**, we provide the glue using the `ON` keyword. This tells the database exactly *how* these two concepts relate.

![inner join](./images/inner_join.svg)

### The Result

| name | quest_name |
|:---|:---|
|Frodo|Destroy Ring|
|Aragorn|Protect Ring|
|Gandalf|Fly Eagles|

Notice who is missing? **Gimli** and **Boromir** are gone because they aren't assigned a quest. The "**Polish Axe**" quest is gone because it has no hero assignment (`NULL`). The `INNER JOIN` is strict; it demands mutual participation.

## 7.2 LEFT JOIN
Sometimes, strictness is not what we want. Sometimes we want a list of *all* our heroes, regardless of whether they are currently employed on a quest. We want to see the intersection, but we also want ot keep everything from the "left" side of the statement.

This is the `LEFT JOIN` (or `LEFT OUTER JOIN`).

### The Syntax
```sql
SELECT Heroes.name, Quests.quest_name
FROM Heroes
LEFT JOIN Quests
ON Heroes.hero_id = Quests.assigned_hero_id;
```

Here, `Heroes` is the "left" table because it appears first (to the left of the `JOIN` keyword). `Quests` is the "right" table.

### Visualizing The LEFT JOIN

![left join](./images/left_join.svg)

### The Result

| name | quest_name |
|:---|:---|
|Frodo|Destroy Ring|
|Aragorn|Protect Ring|
|Gandalf|Fly Eagles|
|Gimli|NULL|
|Boromir|NULL|

The database still matches rows where it can. But for Gimli and Boromir, who have no match in the `Quests` table, the database doesn't discard them. Instead, it fills the gaps with `NULL`.

!!! abstract "The Void of NULL"

    When you perform outer joins, you are inviting `NULL`s into your life. You must be prepared to handle them. If you try to perform logic like `WHERE quest_name = 'Polish Axe'`, Gimli and Boromir will vanish again because `NULL` does not equal anything (not even itself).

## 7.3 RIGHT JOIN
If `LEFT JOIN` keeps everything from the first table, you can probably guess what `RIGHT JOIN` does. It keeps everything from the *second* table (the one on the right of the keyword).

### The Syntax
```sql
SELECT Heroes.name, Quests.quest_name
FROM Heroes
RIGHT JOIN Quests
ON Heroes.hero_id = Quests.assigned_hero_id;
```

### Visualizing the Right Join

![right join](./images/right_join.svg)

### The Result

| name | quest_name |
|:---|:---|
|Frodo|Destroy Ring|
|Aragorn|Protect Ring|
|Gandalf|Fly Eagles|
|NULL|Polish Axe|

Now the tables have turned. Gimli and Boromir are gone (they are on the left, and didn't match). But the "Polish Axe" quest (which had no hero) appears, with a `NULL` for the hero name.

!!! not "Opinionated Note"

    In the wild, you will see `LEFT JOIN` constantly, but `RIGHT JOIN` rarely. Why? Because we read left-to-right. It is cognitively easier to structure a query as "Start with the main thing (Customers), then attach their details (Orders)" rather than "Start with details (Orders) and attach the main thing (Customers) via a Right Join."

    If you find yourself writing a `RIGHT JOIN`, consider simply flipping the order of your tables and using a `LEFT JOIN` instead. Your teammates will thank you.

## 7.4 FULL OUTER JOIN

Sometimes you want it all. You want the heroes with quests, the heroes *without* quests, and the quests *without* heroes. You want the full picture, warts and all.

This is the `FULL OUTER JOIN`. It effectively combines the results of a left join and a right join.

### The Syntax
```sql
SELECT Heroes.name, Quests.quest_name
FROM Heroes
FULL OUTER JOIN Quests
ON Heroes.hero_id = Quests.assigned_hero_id;
```

### Visualizing the FULL OUTER JOIN

![full outer join](./images/full_outer_join.svg)

### The Result

| name | quest_name |
|:---|:---|
|Frodo|Destroy Ring|
|Aragorn|Protect Ring|
|Gandlaf|Fly Eagles|
|Gimli|NULL|
|Boromir|NULL|
|NULL|Polish Axe|

!!! warning

    Not all database engines support `FULL OUTER JOIN` directly (looking at you, MySQL). In those environments, you often have to simulate this by `UNION`-ing a left and right join together.

## 7.5 SELF JOIN
This is where things get a little metaphysical. What if the relationship isn't between two different tables, but between a table and *itself*?

Imagine our `Heroes` table has a column `mentor_id`. This ID refers to another hero in the *same* table. Gandalf might mentor Aragorn.

To query this, we need to join `Heroes` to `Heroes`. But we have a problem: we can't refer to the table `Heroes` twice in the query without ambiguity. If we say `WHERE Heroes.id`, which one do we mean? The mentor or the student?

We solve this with **table aliases**. We treat the single table as if it were two distinct copies.

### The Syntax
```sql
SELECT
    Student.name AS Student_Name,
    Mentor.name AS Mentor_Name
FROM Heroes AS Student
LEFT JOIN Heroes AS Mentor
ON Student.mentor_id = Mentor.hero_id;
```

We alias the first instance as `Student` and the second as `Mentor`. Now the database engine can keep them straight. We use a `LEFT JOIN` here just in case a hero has no mentor (we don't want them to disappear from the list).

## 7.6 CROSS JOIN
Finally, we arrive at the chaotic evil of the join family: the `CROSS JOIN`.

Every join so far has used an `ON` clause to match specific rows. THe Cross Join does not care about matching. It takes every single row from the first table and pairs it with *every single row* from the second table. This is known mathematically as the **Cartesian Product**.

### The Syntax
```sql
SELECT Heroes.name, Quests.quest_name
FROM Heroes
CROSS JOIN Quests;
```

Notice there is no `ON` clause.

### The Math
If you have 5 Heroes and 4 Quests, a cross join will produce 20 rows (5 x 4).

That doesn't sound too bad, right?

!!! warning "The Explosion"

    Be terrified of the cross join on large tables.

    If table A has 100,000 rows and table B has 100,000 rows, a cross join produces 10,000,000,000 (10 billion) rows. This query will likely crash your database server or run until the heat death of the universe.

### When to use it?
It sounds useless, but it has niche uses. For example, if you wanted to generate a "checklist" of every hero attempting every quest for a simulation, or generating a matrix of clothing sizes (S, M, L) against colors (Red, Blue, Green).

But mostly? You probably forgot to type `ON` clause in your inner join.

## Quiz

<quiz>
Which SQL keyword is technically optional when writing an `INNER JOIN` query?
- [ ] `SELECT`
- [ ] `ON`
- [ ] `JOIN`
- [x] `INNER`

</quiz>

<quiz>
In a `LEFT JOIN` between `Heroes` (left) and `Quests` (right), what happens to a Hero who has NO assigned quest?
- [ ] The query returns an error.
- [ ] They are excluded from the results entirely.
- [x] They appear int he results, with `NULL` values for the Quests column.
- [ ] They appear in the results, with the Quest columns repeating the previous row's data.

</quiz>

<quiz>
`NULL` values in a join result are equal to each other (e.g., `NULL = NULL` is true).
- [ ] True
- [x] False

</quiz>

<quiz>
Which JOIN type would you use if you wanted to see a complete list of ALL Heroes and ALL Quests, regardless of whether they are matched together?
- [ ] `LEFT JOIN`
- [x] `FULL OUTER JOIN`
- [ ] `INNER JOIN`
- [ ] `CROSS JOIN`

</quiz>

<quiz>
When performing a self join (joining a table to itself), what SQL feature is absolutely necessary to avoid ambiguity?
- [x] Table aliases
- [ ] The `OUTER` keyword
- [ ] A primary key
- [ ] A `WHERE` clause instead of `ON`

</quiz>

<quiz>
If Table A has 10 rows and Table B has 10 rows, how many rows will a `CROSS JOIN` produce?
- [ ] 0
- [ ] 20
- [x] 100
- [ ] 10

</quiz>

<quiz>
Why is the `RIGHT JOIN` considered 'opinionated' or less commonly used than `LEFT JOIN`?
- [x] It goes against the natural left-to-right reading order of English.
- [ ] It is not supported by standard SQL.
- [ ] It returns fewer columns.
- [ ] It is less performant (slower) than a left join.

</quiz>

<quiz>
In the 'Fantasy RPG' example, if `Heroes` is the left table and `Quests` is the right able, which join would drop the 'Polish Axe' qeust (which has no hero) from the results?
- [x] `LEFT JOIN`
- [ ] `RIGHT JOIN`
- [ ] `FULL OUTER JOIN`
- [ ] `CROSS JOIN`

</quiz>

<quiz>
What mathematical term describes the result of a `CROSS JOIN`?
- [ ] Differences
- [ ] Union
- [ ] Intersection
- [x] Cartesian Product

</quiz>

<quiz>
A `FULL OUTER JOIN` is supported natively by every single SQL database engine.
- [ ] True
- [x] False

</quiz>

<!-- mkdocs-quiz results -->

## Summary
This chapter moved beyond the isolation of single-table queries to explore the true power of the relational model: JOINs. We examined how to reconstruct fragmented data using the strict intersection of `INNER JOIN`, the asymmetric inclusion of `LEFT` and `RIGHT JOIN`s, and the comprehensive scope of `FULL OUTER JOIN`. This chapter also introduced `SELF JOIN`s for handling recursive relationships within a single table and the `CROSS JOIN`, which generates a Cartesian product of all possible combinations.

## Lab
Please complete Chapter 7 labs from the companion [GitHub Repository](https://github.com/mckenzie-andrew/odea-labs){target="_blank"}. 