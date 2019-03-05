# Homework 3

* Assigned: 7 Mar 2019
* Due: 4 Apr 2019 at 10am
* worth 3.75% of your grade

In this assignment it's time to get real!  You'll first flex your SQL
muscles and re-perform [HW2](http://github.com/w4111/hw2)'s analyses by
writing SQL and reflecting on the experience.  
You will then perform some normalization.


# 1. SQL, the sequel
For the first part of the assignment, you will finish that on instabase. Follow the instructions on [instabase](https://www.instabase.com/ewu/w4111-public/fs/Instabase%20Drive/HW3)


# 2. Normalization

**(14 points total)** 


Some warmup questions:

1. (2 points) **Q2.1**: You have a relation `R(A,B,C)` and functional dependencies 
  `C->A, A->B`

  * What are all the non-trivial functional dependencies in the closure
    that have  only one attribute on the right side?
  * What are all the keys of `R`?

1. (3 points) **Q2.2**: You have a relation `S(A, B, C, D)` and functional dependencies 
  `AB->C, BC->D, CD->A, and AD->B`

  * What are all the non-trivial functional dependencies in the closure
    that have  only one attribute on the right side?
  * What are all the keys of `S`?

Now for a real application. 
The Iowa dataset has the following un-normalized schema:


        CREATE TABLE iowa (
            date date,
            convenience_store character varying(128),
            store integer,
            name character varying(128),
            address character varying(128),
            city character varying(128),
            zipcode text,
            store_location character varying(128),
            county_number integer,
            county character varying(128),
            category integer,
            category_name character varying(128),
            vendor_no integer,
            vendor character varying(128),
            item text,
            description character varying(128),
            pack integer,
            liter_size integer,
            state_btl_cost double precision,
            btl_price double precision,
            bottle_qty integer,
            total double precision
        );


You can verify this by opening the sqlite3 prompt, and typing

        .schema iowa

Suppose we have the functional dependencies:

        store -> convenience_store, address, name, city, zipcode, store_location
                county_number, county
        vendor_no -> vendor
        category -> category_name
        item -> category, liter_size, description, state_btl_cost btl_price
        date, store, vendor_no, item -> pack, bottle_qty, total


1. (2 points) **Q2.3**: What are the keys in 'iowa'?

1. (3 points) **Q2.4**: Decompose `iowa` into 3NF (Third Normal Form).  Write a few sentences to justify
  why you chose the tables you did.  

1. (2 points) **Q2.5**: Is your schema redundancy and anomaly free?  Justify your answer in
   a few sentences.

1. (2 points) **Q2.6**: We want to ensure that an order cannot purchase more than 10
   bottles (`bottle_qty`).  Can you enforce this using functional 
   dependencies?  Justify your answer

1. (1 point) **Q2.7**: Let's verify whether `store` indeed determines the store name.   How many distinct `name` values 
   exist for `store` number `2508` in the `iowa` dataset?  Solve this by running a SQL query.

1. (1 point) **Q2.8**: In class, we discussed that functional dependencies (and constraints in general) cannot be
  determined just by looking at data in the database.  
  Argue in one or two sentences whether or not `store -> name` is should actually be a functional dependency and why.  




# X.  For Giggles (Optional)

**(0 points total)**

If you are still interested in this dataset, it turns out that you _can_ normalize the store data!
The state of iowa has released a dataset of all liquor stores as a dataset available at
https://data.iowa.gov/Economy/Iowa-Liquor-Stores/ykb6-ywnd

This dataset provides us information about store attributes so we could factor those out of the iowa dataset.



# Submission

[Gradescope](https://www.gradescope.com/)
