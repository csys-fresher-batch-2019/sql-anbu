# AIRLINE MANAGEMENT SYSTEM

## CITY INFO
```SQL

CREATE TABLE CITY
(CNAME VARCHAR2(15) NOT NULL,
STATE VARCHAR2(15), 
COUNTRY VARCHAR(30),
PRIMARY KEY(CNAME));
-- Insering values
INSERT INTO CITY (CNAME, STATE, COUNTRY) VALUES('ALEN','Kent','United States');
INSERT INTO CITY (CNAME, STATE, COUNTRY) VALUES ('ALEN','Chandigarh','India');
INSERT INTO CITY (CNAME, STATE, COUNTRY) VALUES ('ALEN','Texas','United States');
```

| CNAME      | STATE      | COUNTRY       |
|------------|------------|---------------|
| ALEN       | Kent       | United States |
| ALEN       | TAMILNADU  |  INDIA        |
| ALEN       | Texas      | United States |

## AIRPORT INFO
```SQL
CREATE TABLE AIRPORT
(AP_NAME VARCHAR2(100) NOT NULL,
STATE VARCHAR2(15), 
COUNTRY VARCHAR(30),
CNAME VARCHAR2(15),
PRIMARY KEY(AP_NAME),
FOREIGN KEY(CNAME) REFERENCES CITY(CNAME) ON DELETE CASCADE);
-- Insering values
INSERT INTO AIRPORT (AP_NAME, STATE, COUNTRY, CNAME) VALUES('Los International Airport','Kent','United States','Los');
INSERT INTO AIRPORT (AP_NAME, STATE, COUNTRY, CNAME) VALUES('Chandigarh International Airport','Chandigarh','India','Chandigarh');
INSERT INTO AIRPORT (AP_NAME, STATE, COUNTRY, CNAME) VALUES('Dk International Airport','Texas','United States','Aus');
```
| AP_NAME                          | STATE      | COUNTRY       | CNAME      |
|----------------------------------|------------|---------------|------------|
| Los International Airport        | Kent       | United States | Los        |
| Chandigarh International Airport | Chandigarh | India         | Chandigarh |
| Dk International Airport         | Texas      | United States | Aus        |

## AIRLINE INFO
```SQL

CREATE TABLE AIRLINE
(AIRLINEID VARCHAR(3) NOT NULL,
AL_NAME VARCHAR2(50),
THREE_DIGIT_CODE VARCHAR(3),
PRIMARY KEY(AIRLINEID));
-- Insering values
INSERT INTO AIRLINE (AIRLINEID, AL_NAME, THREE_DIGIT_CODE) VALUES('AA','American Airlines','001');
INSERT INTO AIRLINE (AIRLINEID, AL_NAME, THREE_DIGIT_CODE) VALUES('AI','Air India','098');
INSERT INTO AIRLINE (AIRLINEID, AL_NAME, THREE_DIGIT_CODE) VALUES('LH','Kf', '220');
```
| AIRLINEID | AL_NAME           | THREE_DIGIT_CODE |
|-----------|-------------------|------------------|
| AA        | American Airlines | 001              |
| AI        | Air India         | 098              |
| LH        | Kf                | 220              |


## PASSENGER INFO
```SQL

CREATE TABLE PASSENGER
(PASSPORTNO VARCHAR(10) NOT NULL,
FNAME VARCHAR2(20),
M VARCHAR(1),
LNAME VARCHAR2(20),
ADDRESS VARCHAR2(100),
PHONE INT,
AGE INT,
SEX VARCHAR(1),
PRIMARY KEY(PASSPORTNO));
--iNSERTING VALUES
INSERT INTO PASSENGER(PASSPORTNO,FNAME,M,LNAME,ADDRESS,PHONE,AGE,SEX)
VALUES('A1234568','ALEN','M','SMITH','2230 NORTH, NY',8080367290,30,'M');

INSERT INTO PASSENGER(PASSPORTNO,FNAME,M,LNAME,ADDRESS,PHONE,AGE,SEX)
VALUES('B9876541','ALEN','V','SMITH','3456 NORTH, INDIA',8080367280,26,'F');

INSERT INTO PASSENGER(PASSPORTNO,FNAME,M,LNAME,ADDRESS,PHONE,AGE,SEX)
VALUES('C2345698','ALEN','A','SMITH','7820 NORTH, OH',8082267280,30,'F');
```
| PASSPORTNO | FNAME | M | LNAME | ADDRESS           | PHONE      | AGE | SEX |
|------------|-------|---|-------|-------------------|------------|-----|-----|
| A1234568   | ALEN  | M | SMITH |  2230 NORTH, NY   | 8080367290 | 30  | M   |
| B9876541   | ALEN  | V | SMITH | 3456 NORTH, INDIA | 8080367280 | 26  | F   |
| C2345698   | ALEN  | A | SMITH | 7820 NORTH, OH    | 8082267280 | 30  | F   |

## TICKET INFO

```SQL
CREATE TABLE TICKET
(DATE_OF_BOOKING DATE NOT NULL,
SOURCE VARCHAR(3) NOT NULL,
DESTINATION VARCHAR(3) NOT NULL,
CLASS VARCHAR2(15) NOT NULL,
PRICE INT,
PRIMARY KEY(DATE_OF_BOOKING, SOURCE, DESTINATION, CLASS));
-- INSERTING VALUES 
INSERT INTO TICKET(DATE_OF_BOOKING, SOURCE, DESTINATION, CLASS, PRICE) 
VALUES('11-MAY-16','BOM','DFW','ECONOMY',95000);

INSERT INTO TICKET(DATE_OF_BOOKING, SOURCE, DESTINATION, CLASS, PRICE) 
VALUES('11-JUN-16','JFK','BOM','ECONOMY',100000);

INSERT INTO TICKET(DATE_OF_BOOKING, SOURCE, DESTINATION, CLASS, PRICE) 
VALUES('21-AUG-16','IAH','DEL','BUSINESS',200000);
```
| DATE_OF_BOOKING | SOURCE | DESTINATION | CLASS    | PRICE  |
|-----------------|--------|-------------|----------|--------|
| 11-MAY-16       | BOM    | DFW         | ECONOMY  | 95000  |
| 11-JUN-16       | JFK    | BOM         | BUSINESS | 100000 |
| 21-AUG-16       | IAH    | DEL         | BUSINESS | 200000 |




 ## Feature 4:Reservation Information
   ``` sql
       
   create table reservation_info(ticket_num number,
                                 p_id number not null,
                                 no_of_tickets number not null,
                                 constraint check_no_tickets check(no_of_tickets>0),
                                 constraint primary_key_tic_num primary key(ticket_num),
                                 constraint foreign_key_p_id foreign key(p_id) references passenger_info(p_id)
                                 );
                                 
                      
                      insert into reservation_info values(12345,1002,,1);                     
                      insert into reservation_info values(12346,1001,1);                     
                      insert into reservation_info values(12347,1004,1);                     
                      insert into reservation_info values(12348,1003,1);
                      
                      
                      select * from reservation_info;
                      
   
   ```
   
  
 ## Reservation_Info 
 
   ```sql
| ticket_num | p_id |  |no_of_tickets |
|------------|------|-----------------|
| 12345      | 1002 |     1           |
| 12346      | 1001 |     1           |
| 12347      | 1004 |     1           |
| 12348      | 1003 |     1           |
```
### seat availability

```sql
create table seat_availability(bus_id number not null,
                                        available_seats number not null,
                                        constraint foreign_k_bus_id foreign key(flight_id) references flight_info (flight_id),
                                        constraint check_no_of_seats check(available_seats>=0)
                                        );
                                        
                         insert into seat_availability values(100,49);
                         insert into seat_availability values(101,39); 
                         insert into seat_availability values(102,39);
                         insert into seat_availability values(103,44); 
                         insert into seat_availability values(104,50);
                         
                          select * from seat_availability;
                        
   
| flight_id | available_seats |
|-----------|-----------------|
| 100       | 49              |
| 101       | 39              |
| 102       | 39              |
| 103       | 44              |
| 104       | 50              |

```








