---
title: "Test data builders or SQL files? What's the best way to populate database data?"
layout: post
---

As soon as you start writing integration tests that require a database, a question arises: _how to populate the data_. 

There are two common ways for that. First, to write SQL queries, put them .sql files, and execute them before the tests. This way, once the test starts, the database is populated. The other way is to create test data builders, use them to create all the data you need, and rely on your existing repositories and data access objects to persist them before the test runs.

Which approach is better? I tend to favor test data builders instead of raw SQLs. Because:

* **Easier to understand.** Interpreting 10 very long INSERT statements with 40 columns and lots of random data is harder than 10 lines of `new AccountBuilder().forCustomer(“John”).build()`.

* **Easier to vary data.** If you need three tests to exercise three different branches in the code, it's much easier to have three tests, each with `new AccountBuilder().variation1();`, `new AccountBuilder().variation2();`, `new AccountBuilder().variation3();` than having 3 separate SQL files with lots of duplication, or worse, a single and long SQL file with all the different cases. From personal experience, this is the one that hurts the most.

* **Easier to evolve.** Test data builders are more resilient towards schema changes. If a new column is added, you need to update the test data builder and that's it. Tests won't break. In a SQL file, you might be forced to change all the SQL queries.

* **More explicit.** SQL files tend to become mystery guests, test data builders don't.

* **Simpler to manage.** With the SQL files approach, you may lose control of what data is actually in the database during the test. It's not uncommon to see integration test suites executing hundreds of SQL files before the tests start. Not a single developer knows what's there anymore.

* **More reusable.** Test data builders are easier to be reused across different test suites, modules, and teams.

That being said, I'm not here to convince you that test data builders are a golden bullet. If you believe SQL files are still the right solution, go for it! :)

