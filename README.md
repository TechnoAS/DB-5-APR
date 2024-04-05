# DB-5-APR
/*CREATE TABLE orchestras (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    rating DECIMAL(3,2),
    city_origin VARCHAR(100),
    country_origin VARCHAR(100),
    year INT
);

--CREATE TABLE concerts (
    id INT PRIMARY KEY,
    city VARCHAR(100),
    country VARCHAR(100),
    year INT,
    rating DECIMAL(3,2),
    orchestra_id INT,
    FOREIGN KEY (orchestra_id) REFERENCES orchestras(id)
);

--CREATE TABLE members (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    position VARCHAR(100),
    wage DECIMAL(10,2),
    experience INT,
    orchestra_id INT,
    FOREIGN KEY (orchestra_id) REFERENCES orchestras(id)
);
*/
/*
    • insert some arbitrary rows and values in members table that can perform this queries
    • Write a nested query Selects the name of all orchestras that have the same city of origin as any city in which any orchestra performed in 2013.
    • Write a nested query selects the name and positions of all orchestra members that have above 10 yrs of experience and do not belongs to orchestra with a rating below 8.0.
    • Show the name and position of orchestra members who earn more than the average wage of all violinists .
    • Show the name of orchestras that ware created after “CHAMBER ORCHESTRA” and have a rating above 7.5.
    • Show the name and numbers of members for each orchestra that has more members than the average membership of all orchestras in table

*/

--INSERT INTO orchestras VALUES(1, 'Symphony Orchestra', 8.5, 'New York', 'USA', 1891);
/*INSERT INTO orchestras VALUES(2, 'Chamber Orchestra', 7.0, 'London', 'UK', 1901);
INSERT INTO orchestras VALUES(3, 'Philharmonic Orchestra', 9.0, 'Vienna', 'Austria', 1842);
INSERT INTO orchestras VALUES(4, 'Concert Orchestra', 7.6, 'Berlin', 'Germany', 1921);
INSERT INTO orchestras VALUES(5, 'Youth Orchestra', 8.2, 'Sydney', 'Australia', 1975);
*/
--SELECT * FROM orchestras
/*
INSERT INTO concerts VALUES(1, 'New York', 'USA', 2013, 8.5, 1);
INSERT INTO concerts VALUES(2, 'London', 'UK', 2012, 7.0, 2);
INSERT INTO concerts VALUES(3, 'Vienna', 'Austria', 2014, 9.0, 3);
INSERT INTO concerts VALUES(4, 'Berlin', 'Germany', 2013, 7.6, 4);
INSERT INTO concerts VALUES(5, 'Sydney', 'Australia', 2015, 8.2, 5);
*/
--SELECT * FROM concerts
/*
INSERT INTO members VALUES(1, 'John Doe', 'Violinist', 5000, 15, 1);
INSERT INTO members VALUES(2, 'Jane Smith', 'Cellist', 4500, 12, 1);
INSERT INTO members VALUES(3, 'Alice Johnson', 'Violinist', 5500, 20, 3);
INSERT INTO members VALUES(4, 'Bob Williams', 'Pianist', 6000, 10, 3);
INSERT INTO members VALUES(5, 'lana rhodes', 'Violinist', 4000, 8, 2);
INSERT INTO members VALUES(6, 'David Davis', 'Cellist', 4800, 11, 4);
INSERT INTO members VALUES(7, 'Eva Martin', 'Violinist', 5300, 14, 5);
INSERT INTO members VALUES(8, 'Frank Thompson', 'Pianist', 6200, 9, 5);
*/
--SELECT * FROM members

--SELECT name FROM orchestras WHERE city_origin IN( SELECT city FROM concerts where year = 2013);
--SELECT name,position FROM members WHERE experience >10 AND orchestra_id NOT IN( SELECT id FROM orchestras where rating < 8.0);

--SELECT name,position FROM members WHERE experience >10 AND orchestra_id NOT IN( SELECT id FROM orchestras where rating < 8.0);
--SELECT name,position FROM members WHERE wage >(SELECT avg(wage) FROM members where position = 'Violinist');

/*SELECT o.name 
FROM orchestras o
WHERE o.year > (
    SELECT o2.year 
    FROM orchestras o2
    WHERE o2.name = 'Chamber Orchestra'
) AND o.rating > 7.5;
*/
