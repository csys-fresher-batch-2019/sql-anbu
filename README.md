# FLIGHTTICKET BOOKING APPLICATION

## Features

~ Application provides the searching facilities based on various factor flight schedule.
~ It monitors the transactions through online.
```sql
create table booking(
customer_name varchar2(50) not null,
age number not null,
address varchar2(50) not null,
mobile_number number unique,
flight_name varchar2(50) not null,
boarding_point varchar2(50) not null,
destination_point varchar2(50) not null,
online_payment varchar2(20) not null,
constraint pm check(online_payment in
('g-pay','pay-tm'))

);
insert into booking(customer_name,age,address,mobile_number,flight_name,boarding_point,destination_point,online_payment)values('vijay',21,'xyz123',9894636915,'airindia','chennai','coimbatore','g-pay');
insert into booking(customer_name,age,address,mobile_number,flight_name,boarding_point,destination_point,online_payment)values('vijay',23,'xygdz123',746356916,'airindia','coimbatore','chennai','pay-tm');

select *from booking;

```
