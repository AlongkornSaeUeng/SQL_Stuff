# SQL_Stuff

#1 Window Function / Termial / Subqueries / Join / With clause

/* I already create database (.db file) from console so no code is shown */
.open restaurant.db
.mode box
  
/*left join customers table with point table (use pid as key)*/
select * from customers
  left join point
    on customers.pid = point.pid;

/* average point in point column */
select avg(point) from point;

/* unique count the id that have point */
select count(pid) as member_with_point from point;

/* let sub 1 be customers that only have city as BKK and sub 2 be branch table*/
with sub1 as(
  select * from customers where city = "BKK"
)
, sub2 as(
  select * from branch
)
  
/*join table sub1 and sub2 with city as a key*/
select * 
  from sub1 
  join sub2 
    on sub1.city = sub2.city;

/* Select city in brach table */
select 
  (select city ) from branch;

/* Show promo coloumn */
select * from promo;

/* Filter the only the branch that accept promo column */
select * from promo where promo_c = "Yes";

/* Print the only the branch that accept promo column */
select city from branch join (select * from promo where promo_c = "Yes") as sub on branch.bid = sub.bid;

Result of the code
https://replit.com/@RubyRotary/bootcampbatch08sqlrestaurant
