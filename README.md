## Databasics

Fork this repository into your own github profile.

Before closing the homework assignment issue:

- Update this README as follows:
  - [ ] For each question (just after or below the question itself) include the SQL you wrote to generate the answer
  - [ ] For each question (just after or below the question itself) include the *answer* to the question asked.

- Also:
  - [ ] Commit the updated `store.sqlite3` database file
  - [ ] Include a link to your forked repo in the comments when closing the issue.


NOTE: To run sqlite with this database: `sqlite3 store.sqlite3`

NOTE: You may want to keep a backup of the `store.sqlite3` file in case you damage the file. *OR* you can use the command `git checkout store.sqlite3` to undo any changes to the database file since the fork or your last commit.

## Explorer Mode

- [ ] How many users are there?
<!-- select count(*) from users -->
<!-- ----------
50         -->
- [ ] What are the 5 most expensive items?
<!-- select title, price from items order by price desc limit 5; -->
<!-- title                price     
-------------------  ----------
Small Cotton Gloves  9984      
Small Wooden Comput  9859      
Awesome Granite Pan  9790      
Sleek Wooden Hat     9390      
Ergonomic Steel Car  9341       -->
- [ ] What's the cheapest book? (Does that change for "category is exactly 'book'" versus "category contains 'book'"?)
<!-- select price, title from items where category = "Books" order by price limit 1; -->
<!-- price       title                  
----------  -----------------------
1496        Ergonomic Granite Chair -->
- [ ] Who lives at "6439 Zetta Hills, Willmouth, WY"? Do they have another address?
<!-- select users.first_name, users.last_name from users, addresses where users.id = addresses.user_id and addresses.street = "6439 Zetta Hills"; -->
<!-- first_name  last_name
----------  ---------- -->
<!-- Corrine     Little   -->
<!-- select addresses.street from addresses, users where users.id = addresses.user_id and first_name="Corrine" and last_name = "Little";
street          
----------------
6439 Zetta Hills
54369 Wolff Forg -->
- [ ] Correct Virginie Mitchell's address to "New York, NY, 10108".
<!-- update addresses set city = "New York", state = "NY", zip = "10108" where user_id = (select id from users where first_name = "Virginie" and last_name = "Mitchell"); -->
<!-- select street, city, state, zip from addresses where user_id = 39;
street               city        state       zip       
-------------------  ----------  ----------  ----------
12263 Jake Crossing  New York    NY          10108     
83221 Mafalda Canyo  New York    NY          10108 -->
- [ ] How much would it cost to buy one of each tool?
<!-- select sum(price) from items where  category = "Tools";
sum(price)
----------
7383       -->
- [ ] How many total items did we sell?
<!-- select sum(quantity) from orders; -->
<!-- sum(quantity)
-------------
2125         -->
- [ ] How much was spent on books?
<!-- select sum(orders.quantity * items.price) from items, orders where items.id = orders.item_id;
sum(orders.quantity * items.price)
----------------------------------
10045128      -->
- [ ] Simulate buying an item by inserting a User for yourself and an Order for that User.
<!-- sqlite> insert into users values(NULL, "Adam", "Fronczak", "Fronczak.Adam@gmail.com"); -->

## Adventure Mode

- [ ] What item was ordered most often? Grossed the most money?
- [ ] What user spent the most?
- [ ] What were the top 3 highest grossing categories?
