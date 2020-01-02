```SQL
CREATE TABLE CITY
(CNAME VARCHAR2(15) NOT NULL,
STATE VARCHAR2(15), 
COUNTRY VARCHAR(30),
PRIMARY KEY(CNAME));
-- Insering values
INSERT INTO CITY (CNAME, STATE, COUNTRY) VALUES('LoS','Kent','United States');
INSERT INTO CITY (CNAME, STATE, COUNTRY) VALUES ('Chandigarh','Chandigarh','India');
INSERT INTO CITY (CNAME, STATE, COUNTRY) VALUES ('AUSI','Texas','United States');


| CNAME      | STATE      | COUNTRY       |
|------------|------------|---------------|
| LoS        | Kent       | United States |
| Chandigarh | Chandigarh | India         |
| AUSI       | Texas      | United States |

```
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
| AP_NAME                          | STATE      | COUNTRY       | CNAME      |
|----------------------------------|------------|---------------|------------|
| Los International Airport        | Kent       | United States | Los        |
| Chandigarh International Airport | Chandigarh | India         | Chandigarh |
| Dk International Airport         | Texas      | United States | Aus        |
```

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

| AIRLINEID | AL_NAME           | THREE_DIGIT_CODE |
|-----------|-------------------|------------------|
| AA        | American Airlines | 001              |
| AI        | Air India         | 098              |
| LH        | Kf                | 220              |
```


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

| PASSPORTNO | FNAME | M | LNAME | ADDRESS           | PHONE      | AGE | SEX |
|------------|-------|---|-------|-------------------|------------|-----|-----|
| A1234568   | ALEN  | M | SMITH |  2230 NORTH, NY   | 8080367290 | 30  | M   |
| B9876541   | ALEN  | V | SMITH | 3456 NORTH, INDIA | 8080367280 | 26  | F   |
| C2345698   | ALEN  | A | SMITH | 7820 NORTH, OH    | 8082267280 | 30  | F   |
```
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

| DATE_OF_BOOKING | SOURCE | DESTINATION | CLASS    | PRICE  |
|-----------------|--------|-------------|----------|--------|
| 11-MAY-16       | BOM    | DFW         | ECONOMY  | 95000  |
| 11-JUN-16       | JFK    | BOM         | BUSINESS | 100000 |
| 21-AUG-16       | IAH    | DEL         | BUSINESS | 200000 |




SELECT *FROM CITY,AIRPORT,AIRLINE,PASSENGER,TICKET;/

