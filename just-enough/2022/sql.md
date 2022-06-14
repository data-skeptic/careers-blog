I took a databases course in college.  I think I got an A.  I had no idea how to use SQL.  If you don't either, this guide is meant to be a simple crash course to give you just enough information to be dangerous.

Structured query language or SQL is a really simple language that anyone can learn.  It's not just for technical professionals.  I've interacted with many finance, marketing, and other non-engineering professionals who look a small amount of SQL knowledge as the lever to accellerate their careers.

Most of the database you encounter will be set up by someone else.  They made decisions about what backend software to use (eg. MS SQL Server, Postgres, AWS RDS, Snowflake, MySql, etc.) and how structure the data.  Someone will have to show you how to get connected and start making queries.  This guide is meant to be a gentle introduction once you're connected and ready to start asking questions.  How you connect to the database and what kind you connect to will vary, but the basics of SQL are fairly universal!  Any relevant differences are noted inline.

### Getting Started

The database is ground truth, or at least as close to it as a company or organization has.  If you know how to ask questions directly, then you can inform all your key business decisions with a dadta-driven approach.

Business analytics has matured a lot in the last decade.  Even small companies typically provide some data warehousing and dashboarding tools for internal employees to inspect the data.  These systems have many pros and a few cons.  When properly configured, such tools give a filtered, aggregated representation of the underlying data.  A large retailer captures the full grain transaction log of their stores.  Few team members will care about the raw logs and the overwhelming size of data to be processed.  The results are stored in a data warehouse.  If you try really hard, you're likely to find a bug in the way something is calculated in the data warehouse, but for the most part, it is basically another source of truth, accessible through the same language, SQL.

### SQL is easy to learn

Let's learn it by example in a few queries.

```
SELECT *

FROM daily_sales_by_hour

WHERE created_at > '2014-05-14'

LIMIT 10
```

This query highlights four of the main commands of SQL, from which there's around 6-12 useful commands depending on who you ask.

`SELECT` is how all queries for data begin.  It's followed by a list of columns you'd like returned, or `*` for all columns.

`FROM` follows the `SELECT` and lists the tables you are interested in extracting data from.  In this example, it's just the `daily_sales_by_hour` table.  Tables can be named anything.  Many are named poorly.  You're often expected to infer the contents from the name alone.  Luckily, `daily_sales_by_hour`, is not a bad name!

The `WHERE` clause comes next and provides optional filtering.  In this example, we're looking for anything after May 14th.  Dates can be a pain!  If they aren't set up correctly in the development process, the problem will fester and reappear in surprising new ways.  Be prepared to double check every time you work with a date.  Is it a `DATETIME` or is it a string in which dates are stored?  A deep dive on database dates might be another great post.

Finally `LIMIT` is an optional parameter telling the database we only want `10` records to be returned.  Without this, directly querying some databases may start to return millions or billions or rows to you.  You might even get an angry call from a database administrator.  Always use `LIMIT`.  Oh, and if you're on Microsoft SQL Server, you may need to ask for `SELECT top 10 *` instead of using a `LIMIT`.

Hopefully you have an intuitive grasp of the basic query above and would be comfortable manipulating it, provided you had access to the same database and a means of querying it.  SQL is learned in the trenches.  Have a friend write you a query like the one above and start manipulating it iteratively.  Prior to that, let's take on the next example.

```
    SELECT store_id

    , SUM(revenue) as total_revenue

    , COUNT(DISTINCT customer_id) as customers

    FROM daily_sales_by_hour

    WHERE sales_date == '2014-05-14'

    GROUP BY store_id
```

The key new command here is the `GROUP BY` which asks the database do pre-aggregate the data for us and return a summarized result.  After the command, we list the columns which will map to unique rows in the output.  Here we are going to summarize by `store_id`.  If that wasn't unique enough it could be a list like `GROUP BY store_id, country_code`.

Also new are `SUM` and `COUNT` as well as the aliasing syntax (e.g. `as total_revenue`) which define what to name these generated columns when they are returned in the final dataset.  `SUM(revenue)` should be self explanatory. I also want to get a total number of customers in the result.  I presume that the same customer might have multiple purchases in the same hour.  Thus, counting the `DISTINCT customer_id` would de-dupe multiple purchases.  More often than not, `COUNT(*)` will be fine for your needs.

Last query is a fancier version of the one above

```
    SELECT t2.store_name

    , SUM(t1.revenue) as total_revenue

    , COUNT(DISTINCT t1.customer_id) as customers

    FROM daily_sales_by_hour t1

    JOIN stores t2

      ON t1.store_id = t2.store_id

    WHERE t1.sales_date == '2014-05-14'

    GROUP BY t2.store_name
```

In this version, I introduce a `JOIN` in order to query data from multiple tables.  You almost always want to join on an integer value where one is the primary key of one of the tables.  After `JOIN` comes `ON` which expresses the relationship which must hold true for the matching rows to be included in the resultset.  If a record existed in `daily_sales_by_hour` for a non-existent `store_id` (typo?, historical?, fraud?), then that row in the first table would be ignored.  If you wanted to include missing rows, it would be a `LEFT JOIN`.  In the case of a missing store, the value of `NULL` would appear for the missing row.

There's also `RIGHT JOIN` and `FULL OUTER JOIN` but you're not going to need those.

This last query also introduces table aliasing (`t1` and `t2`) and an explicit mention of which table to get each referenced column from.  This isn't strictly required.  If a column only exists in one place, the database will figure that out.  But if it exists in *two* places, it will throw an error.  For this an many other hygenic reasons, it's best to always alias your column references when using a `JOIN`.

I will now introduce a few more broad concepts to tie up this introduction.

### Schema

A database is a collection of tables and sometimes other artifacts and metadata.  The tables are ordered rows sharing the same column names, types, and properties.  This structure is called the database **schema**.   Invariably, your first time accessing a large database requiring multiple joins to get results will be intimidating.  Your first instincts might be to criticise the database's schema.

Sometimes these criticisms are warranted.  In my observation, more often then not, they're an indicator of naiveté.  It's best to try and work with the schema first, before trying to re-write it.  On any sizable project, they're likely to be multiple SQL experts eager to take on a challenge about what query couldn't possibly be expressed for the given database.  Ask for help in the form of a challenge and one of three things will happen.  1) You'll be issued a query that does what you need, 2) an acknowledgement and discussion of the level of effort to fix will ensue, or 3) some sort of data transformation will be proposed.

### ETL

Export, transform, and load, are the three main verbs used to describe most data pipelines (whether or not their design is sa good match for the acronym or not!)  Data comes from somewhere and must be extracted.  Perhaps its extracted from a CRM, ERP, API, vendor, or partner system.  For discussion purposes, think of it as data from retail stores being periodically downloaded to the mothership.

The data is extracted and centralized to the cloud in it's raw, transactional form.  That data is important to store, but also not the end of the line.  Many business uses will need some form of aggregation or processing.  We call those efforts the **transform** portion of the data pipeline.

The transformed data needs to land somewhere, in some database that can be accessed by only the people and processes that should have access to it.  That step is the **load** step.

A causal SQL user is unlikely to ever write an ETL code.  That task is typically performed by a data engineer.  Yet, an intermediate or advanced business user might be the one defining the transformational logic in a query, which the team has to implement in a scalable, automated fashion.

### Beyond the Basics

This post was meant to be a crash course for a SQL noob.  The 3 example queries I provided demonstrated the things you will get you about 97% of the way there.  Knowing your own schema and how to `JOIN` tables is the muscle you need to exercise most.  Do this with an eye towards critical thinking and double checking your intuitions will be a recipe for success.

At some point you should also learn about temporary tables and how to create both temporary and regular tables.  It's often very handy to come up with some complex, hard to read query and wish the result could be snapshotted in time prior to the next step in some analysis.  It can!  The results of a query can be saved as a table.  How to do so varies by your sql backend.

There are other advanced concepts you might hear legend of as you pursue a little SQL in your life.  For example, stored procedures.  These seem to be very popular for MS SQL Server users and no one else.  It's a neat way to formalize some series of queries.  Look into what's possible on your setup and decide if you're a stored procedures person or not.

A little simpler, but sometimes messier, are inline functions.  While `SUM` and `COUNT` are universal, other options exist depending on what database backend you're using.  Inline functions that don't require `GROUP BY` such as `sin(x)` might be available.  Some databases even allow ways to create user defined functions.  There's efforts to do some pretty advanced things like machine learning from "inside" the database.

### Summing it up

If you want to be a data driven professional, you need data driven answers.  Depending on your seniority, that might mean relying and analytic's profession to handle your requests for data, or having direct access to the database to get your answers first hand.  Either way, the query is generally the easy part.  Asking the right question and knowing how to interpret the result are the challenges you will really need to face.


