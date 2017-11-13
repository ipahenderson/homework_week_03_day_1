# SQL Homework

The Dominion Cinema are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1. Return ALL the data in the 'movies' table.

SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:30
 2 | The Incredible Hulk                 | 2008 | 14:10
 3 | Iron Man 2                          | 2010 | 18:40
 4 | Thor                                | 2011 | 15:40
 5 | Captain America: The First Avenger  | 2011 | 21:00
 6 | Avengers Assemble                   | 2012 | 15:00
 7 | Iron Man 3                          | 2013 | 13:05
 8 | Thor: The Dark World                | 2013 | 13:20
 9 | Batman Begins                       | 2005 | 22:20
10 | Captain America: The Winter Soldier | 2014 | 13:05
11 | Guardians of the Galaxy             | 2014 | 13:15
12 | Avengers: Age of Ultron             | 2015 | 16:55
13 | Ant-Man                             | 2015 | 18:00
14 | Captain America: Civil War          | 2016 | 16:25
15 | Doctor Strange                      | 2016 | 13:20
16 | Guardians of the Galaxy 2           | 2017 | 21:55
(16 rows)

2. Return ONLY the name column from the 'people' table

name          
------------------------
Fraser  Black
Benjamin  Bowen
Fraser  Brown
Brian Connelly
Mark  Conroy
Alex  Constantinou
Krisztian Der
Malcolm Finlayson
Alistair  Guthrie
Anna  Lanigan
Matthew Manson
Eleni Margariti
Catriona  Meriel
Jardine Miller
Philip  Mitchell
Sophie  Mullins
Eliot Short
Andrew  Wright
Katarina  Zemplenyiova
Andrew
Andrew
Iain Henderson
(22 rows)

3. Oops! Someone at CodeClan spelled Ian's name wrong! Change it to reflect the proper spelling (change 'Iain Henderson' to 'Ian Henderson').

UPDATE people
SET name = 'Ian Henderson'
WHERE name = 'Iain Henderson';

id |     name      
----+---------------
10 | Ian Henderson
(1 row)

4. Return ONLY your name from the 'people' table.

SELECT * FROM people
WHERE people.name = 'Ian Henderson';

id |     name      
----+---------------
10 | Ian Henderson
(1 row)

5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

DELETE FROM movies WHERE title = 'Batman Begins';

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:30
 2 | The Incredible Hulk                 | 2008 | 14:10
 3 | Iron Man 2                          | 2010 | 18:40
 4 | Thor                                | 2011 | 15:40
 5 | Captain America: The First Avenger  | 2011 | 21:00
 6 | Avengers Assemble                   | 2012 | 15:00
 7 | Iron Man 3                          | 2013 | 13:05
 8 | Thor: The Dark World                | 2013 | 13:20
10 | Captain America: The Winter Soldier | 2014 | 13:05
11 | Guardians of the Galaxy             | 2014 | 13:15
12 | Avengers: Age of Ultron             | 2015 | 16:55
13 | Ant-Man                             | 2015 | 18:00
14 | Captain America: Civil War          | 2016 | 16:25
15 | Doctor Strange                      | 2016 | 13:20
16 | Guardians of the Galaxy 2           | 2017 | 21:55
(15 rows)



6. Create a new entry in the 'people' table with the name of one of the instructors.

INSERT INTO people (name) VALUES ('Keith  Douglas');

id |      name      
----+----------------
23 | Keith  Douglas
(1 row)


7. Craig Morton, has decided to hijack our movie evening, Remove him from the table of people.

DELETE FROM people WHERE name = 'Craig Morton';


8. Somehow the list of people includes two people named 'Andrew'. Change these entries to the proper names ('Jeff 4', 'Jeff 5')

UPDATE people
SET name = 'Andrew 21'
WHERE id = 21;

UPDATE people
SET name = 'Andrew 22'
WHERE id = 22;

 id |          name  
----+------------------------
 21 | Andrew 21
 22 | Andrew 22
(2 rows)

9. The cinema has just heard that they will be holding an exclusive midnight showing of 'Guardians of the Galaxy 2'!! Create a new entry in the 'movies' table to reflect this.

INSERT INTO movies (title, year, show_time) VALUES ('Guardians of the Galaxy 2', 2017, '00:00');

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:30
 2 | The Incredible Hulk                 | 2008 | 14:10
 3 | Iron Man 2                          | 2010 | 18:40
 4 | Thor                                | 2011 | 15:40
 5 | Captain America: The First Avenger  | 2011 | 21:00
 6 | Avengers Assemble                   | 2012 | 15:00
 7 | Iron Man 3                          | 2013 | 13:05
 8 | Thor: The Dark World                | 2013 | 13:20
10 | Captain America: The Winter Soldier | 2014 | 13:05
11 | Guardians of the Galaxy             | 2014 | 13:15
12 | Avengers: Age of Ultron             | 2015 | 16:55
13 | Ant-Man                             | 2015 | 18:00
14 | Captain America: Civil War          | 2016 | 16:25
15 | Doctor Strange                      | 2016 | 13:20
16 | Guardians of the Galaxy 2           | 2017 | 21:55
17 | Guardians of the Galaxy 2           | 2017 | 00:00
(16 rows)



10. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 18:55 to 21:30

UPDATE movies
SET show_time = '21:30'
WHERE title = 'Guardians of the Galaxy';

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:30
 2 | The Incredible Hulk                 | 2008 | 14:10
 3 | Iron Man 2                          | 2010 | 18:40
 4 | Thor                                | 2011 | 15:40
 5 | Captain America: The First Avenger  | 2011 | 21:00
 6 | Avengers Assemble                   | 2012 | 15:00
 7 | Iron Man 3                          | 2013 | 13:05
 8 | Thor: The Dark World                | 2013 | 13:20
10 | Captain America: The Winter Soldier | 2014 | 13:05
12 | Avengers: Age of Ultron             | 2015 | 16:55
13 | Ant-Man                             | 2015 | 18:00
14 | Captain America: Civil War          | 2016 | 16:25
15 | Doctor Strange                      | 2016 | 13:20
16 | Guardians of the Galaxy 2           | 2017 | 21:55
17 | Guardians of the Galaxy 2           | 2017 | 00:00
11 | Guardians of the Galaxy             | 2014 | 21:30
(16 rows)


## Research

1. Research how to delete multiple entries from your table in a single command.

DELETE FROM movies WHERE title IN('Ant-Man', 'Thor');

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:30
 2 | The Incredible Hulk                 | 2008 | 14:10
 3 | Iron Man 2                          | 2010 | 18:40
 5 | Captain America: The First Avenger  | 2011 | 21:00
 6 | Avengers Assemble                   | 2012 | 15:00
 7 | Iron Man 3                          | 2013 | 13:05
 8 | Thor: The Dark World                | 2013 | 13:20
10 | Captain America: The Winter Soldier | 2014 | 13:05
12 | Avengers: Age of Ultron             | 2015 | 16:55
14 | Captain America: Civil War          | 2016 | 16:25
15 | Doctor Strange                      | 2016 | 13:20
16 | Guardians of the Galaxy 2           | 2017 | 21:55
17 | Guardians of the Galaxy 2           | 2017 | 00:00
11 | Guardians of the Galaxy             | 2014 | 21:30
(14 rows)
