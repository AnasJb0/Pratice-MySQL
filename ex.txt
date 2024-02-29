Enter password: ******************
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 51
Server version: 8.0.19 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show datbases ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'datbases' at line 1
mysql> show databases ;
+--------------------+
| Database           |
+--------------------+
| centre_formation   |
| hollywood          |
| information_schema |
| isgi               |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| test1              |
| test2              |
| test3              |
+--------------------+
11 rows in set (0.00 sec)

mysql> use sakila ;
Database changed
mysql> show tables ;
+----------------------------+
| Tables_in_sakila           |
+----------------------------+
| actor                      |
| actor_copy                 |
| actor_info                 |
| address                    |
| category                   |
| city                       |
| country                    |
| customer                   |
| customer_list              |
| film                       |
| film_actor                 |
| film_category              |
| film_list                  |
| film_text                  |
| inventory                  |
| language                   |
| nicer_but_slower_film_list |
| payment                    |
| rental                     |
| sales_by_film_category     |
| sales_by_store             |
| staff                      |
| staff_list                 |
| store                      |
+----------------------------+
24 rows in set (0.00 sec)

mysql> desc film ;
+----------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
| Field                | Type                                                                | Null | Key | Default           | Extra                                         |
+----------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
| film_id              | smallint unsigned                                                   | NO   | PRI | NULL              | auto_increment                                |
| title                | varchar(128)                                                        | NO   | MUL | NULL              |                                               |
| description          | text                                                                | YES  |     | NULL              |                                               |
| release_year         | year                                                                | YES  |     | NULL              |                                               |
| language_id          | tinyint unsigned                                                    | NO   | MUL | NULL              |                                               |
| original_language_id | tinyint unsigned                                                    | YES  | MUL | NULL              |                                               |
| rental_duration      | tinyint unsigned                                                    | NO   |     | 3                 |                                               |
| rental_rate          | decimal(4,2)                                                        | NO   |     | 4.99              |                                               |
| length               | smallint unsigned                                                   | YES  |     | NULL              |                                               |
| replacement_cost     | decimal(5,2)                                                        | NO   |     | 19.99             |                                               |
| rating               | enum('G','PG','PG-13','R','NC-17')                                  | YES  |     | G                 |                                               |
| special_features     | set('Trailers','Commentaries','Deleted Scenes','Behind the Scenes') | YES  |     | NULL              |                                               |
| last_update          | timestamp                                                           | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
+----------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
13 rows in set (0.00 sec)

mysql> select film_id , title
    -> where title like 'dr%';
ERROR 1054 (42S22): Unknown column 'film_id' in 'field list'
mysql> select title
    -> where title like 'dr%';
ERROR 1054 (42S22): Unknown column 'title' in 'field list'
mysql> select film
    -> where title like 'dr%';
ERROR 1054 (42S22): Unknown column 'film' in 'field list'
mysql> select * from film
    -> where title like 'dr%';
+---------+----------------------+----------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+-----------------------------------------------+---------------------+
| film_id | title                | description                                                                                                    | release_year | language_id | original_language_id | rental_duration | rental_rate | length | replacement_cost | rating | special_features                              | last_update         |
+---------+----------------------+----------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+-----------------------------------------------+---------------------+
|     249 | DRACULA CRYSTAL      | A Thrilling Reflection of a Feminist And a Cat who must Find a Frisbee in An Abandoned Fun House               |         2006 |           1 |                 NULL |               7 |        0.99 |    176 |            26.99 | G      | Commentaries                                  | 2006-02-15 05:03:42 |
|     250 | DRAGON SQUAD         | A Taut Reflection of a Boy And a Waitress who must Outgun a Teacher in Ancient China                           |         2006 |           1 |                 NULL |               4 |        0.99 |    170 |            26.99 | NC-17  | Deleted Scenes,Behind the Scenes              | 2006-02-15 05:03:42 |
|     251 | DRAGONFLY STRANGERS  | A Boring Documentary of a Pioneer And a Man who must Vanquish a Man in Nigeria                                 |         2006 |           1 |                 NULL |               6 |        4.99 |    133 |            19.99 | NC-17  | Trailers,Behind the Scenes                    | 2006-02-15 05:03:42 |
|     252 | DREAM PICKUP         | A Epic Display of a Car And a Composer who must Overcome a Forensic Psychologist in The Gulf of Mexico         |         2006 |           1 |                 NULL |               6 |        2.99 |    135 |            18.99 | PG     | Trailers,Commentaries,Behind the Scenes       | 2006-02-15 05:03:42 |
|     253 | DRIFTER COMMANDMENTS | A Epic Reflection of a Womanizer And a Squirrel who must Discover a Husband in A Jet Boat                      |         2006 |           1 |                 NULL |               5 |        4.99 |     61 |            18.99 | PG-13  | Trailers,Behind the Scenes                    | 2006-02-15 05:03:42 |
|     254 | DRIVER ANNIE         | A Lacklusture Character Study of a Butler And a Car who must Redeem a Boat in An Abandoned Fun House           |         2006 |           1 |                 NULL |               4 |        2.99 |    159 |            11.99 | PG-13  | Trailers,Deleted Scenes,Behind the Scenes     | 2006-02-15 05:03:42 |
|     255 | DRIVING POLISH       | A Action-Packed Yarn of a Feminist And a Technical Writer who must Sink a Boat in An Abandoned Mine Shaft      |         2006 |           1 |                 NULL |               6 |        4.99 |    175 |            21.99 | NC-17  | Trailers,Deleted Scenes                       | 2006-02-15 05:03:42 |
|     256 | DROP WATERFRONT      | A Fanciful Documentary of a Husband And a Explorer who must Reach a Madman in Ancient China                    |         2006 |           1 |                 NULL |               6 |        4.99 |    178 |            20.99 | R      | Trailers,Commentaries                         | 2006-02-15 05:03:42 |
|     257 | DRUMLINE CYCLONE     | A Insightful Panorama of a Monkey And a Sumo Wrestler who must Outrace a Mad Scientist in The Canadian Rockies |         2006 |           1 |                 NULL |               3 |        0.99 |    110 |            14.99 | G      | Commentaries,Deleted Scenes,Behind the Scenes | 2006-02-15 05:03:42 |
|     258 | DRUMS DYNAMITE       | A Epic Display of a Crocodile And a Crocodile who must Confront a Dog in An Abandoned Amusement Park           |         2006 |           1 |                 NULL |               6 |        0.99 |     96 |            11.99 | PG     | Trailers                                      | 2006-02-15 05:03:42 |
+---------+----------------------+----------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+-----------------------------------------------+---------------------+
10 rows in set (0.23 sec)

mysql> select film
    -> where title like '%dr';
ERROR 1054 (42S22): Unknown column 'film' in 'field list'
mysql> select * from film
    -> where title like 'dr%';
+---------+----------------------+----------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+-----------------------------------------------+---------------------+
| film_id | title                | description                                                                                                    | release_year | language_id | original_language_id | rental_duration | rental_rate | length | replacement_cost | rating | special_features                              | last_update         |
+---------+----------------------+----------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+-----------------------------------------------+---------------------+
|     249 | DRACULA CRYSTAL      | A Thrilling Reflection of a Feminist And a Cat who must Find a Frisbee in An Abandoned Fun House               |         2006 |           1 |                 NULL |               7 |        0.99 |    176 |            26.99 | G      | Commentaries                                  | 2006-02-15 05:03:42 |
|     250 | DRAGON SQUAD         | A Taut Reflection of a Boy And a Waitress who must Outgun a Teacher in Ancient China                           |         2006 |           1 |                 NULL |               4 |        0.99 |    170 |            26.99 | NC-17  | Deleted Scenes,Behind the Scenes              | 2006-02-15 05:03:42 |
|     251 | DRAGONFLY STRANGERS  | A Boring Documentary of a Pioneer And a Man who must Vanquish a Man in Nigeria                                 |         2006 |           1 |                 NULL |               6 |        4.99 |    133 |            19.99 | NC-17  | Trailers,Behind the Scenes                    | 2006-02-15 05:03:42 |
|     252 | DREAM PICKUP         | A Epic Display of a Car And a Composer who must Overcome a Forensic Psychologist in The Gulf of Mexico         |         2006 |           1 |                 NULL |               6 |        2.99 |    135 |            18.99 | PG     | Trailers,Commentaries,Behind the Scenes       | 2006-02-15 05:03:42 |
|     253 | DRIFTER COMMANDMENTS | A Epic Reflection of a Womanizer And a Squirrel who must Discover a Husband in A Jet Boat                      |         2006 |           1 |                 NULL |               5 |        4.99 |     61 |            18.99 | PG-13  | Trailers,Behind the Scenes                    | 2006-02-15 05:03:42 |
|     254 | DRIVER ANNIE         | A Lacklusture Character Study of a Butler And a Car who must Redeem a Boat in An Abandoned Fun House           |         2006 |           1 |                 NULL |               4 |        2.99 |    159 |            11.99 | PG-13  | Trailers,Deleted Scenes,Behind the Scenes     | 2006-02-15 05:03:42 |
|     255 | DRIVING POLISH       | A Action-Packed Yarn of a Feminist And a Technical Writer who must Sink a Boat in An Abandoned Mine Shaft      |         2006 |           1 |                 NULL |               6 |        4.99 |    175 |            21.99 | NC-17  | Trailers,Deleted Scenes                       | 2006-02-15 05:03:42 |
|     256 | DROP WATERFRONT      | A Fanciful Documentary of a Husband And a Explorer who must Reach a Madman in Ancient China                    |         2006 |           1 |                 NULL |               6 |        4.99 |    178 |            20.99 | R      | Trailers,Commentaries                         | 2006-02-15 05:03:42 |
|     257 | DRUMLINE CYCLONE     | A Insightful Panorama of a Monkey And a Sumo Wrestler who must Outrace a Mad Scientist in The Canadian Rockies |         2006 |           1 |                 NULL |               3 |        0.99 |    110 |            14.99 | G      | Commentaries,Deleted Scenes,Behind the Scenes | 2006-02-15 05:03:42 |
|     258 | DRUMS DYNAMITE       | A Epic Display of a Crocodile And a Crocodile who must Confront a Dog in An Abandoned Amusement Park           |         2006 |           1 |                 NULL |               6 |        0.99 |     96 |            11.99 | PG     | Trailers                                      | 2006-02-15 05:03:42 |
+---------+----------------------+----------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+-----------------------------------------------+---------------------+
10 rows in set (0.00 sec)

mysql> DESC FILM;
+----------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
| Field                | Type                                                                | Null | Key | Default           | Extra                                         |
+----------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
| film_id              | smallint unsigned                                                   | NO   | PRI | NULL              | auto_increment                                |
| title                | varchar(128)                                                        | NO   | MUL | NULL              |                                               |
| description          | text                                                                | YES  |     | NULL              |                                               |
| release_year         | year                                                                | YES  |     | NULL              |                                               |
| language_id          | tinyint unsigned                                                    | NO   | MUL | NULL              |                                               |
| original_language_id | tinyint unsigned                                                    | YES  | MUL | NULL              |                                               |
| rental_duration      | tinyint unsigned                                                    | NO   |     | 3                 |                                               |
| rental_rate          | decimal(4,2)                                                        | NO   |     | 4.99              |                                               |
| length               | smallint unsigned                                                   | YES  |     | NULL              |                                               |
| replacement_cost     | decimal(5,2)                                                        | NO   |     | 19.99             |                                               |
| rating               | enum('G','PG','PG-13','R','NC-17')                                  | YES  |     | G                 |                                               |
| special_features     | set('Trailers','Commentaries','Deleted Scenes','Behind the Scenes') | YES  |     | NULL              |                                               |
| last_update          | timestamp                                                           | NO   |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
+----------------------+---------------------------------------------------------------------+------+-----+-------------------+-----------------------------------------------+
13 rows in set (0.00 sec)

mysql> select * from film
    -> where title like 'c%'and '%tion';
Empty set, 1 warning (0.08 sec)

mysql> select * from film
    -> WHERE lenght(title) = 3;
ERROR 1305 (42000): FUNCTION sakila.lenght does not exist
mysql> select * from film
    -> select titre from film
    -> where title like '_on%';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'select titre from film
where title like '_on%'' at line 2
mysql> select titre from film
    -> where title like '_on%';
ERROR 1054 (42S22): Unknown column 'titre' in 'field list'
mysql> select * from film
    -> where title like '_on%';
+---------+------------------------+---------------------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+--------------------------------------------------------+---------------------+
| film_id | title                  | description                                                                                                               | release_year | language_id | original_language_id | rental_duration | rental_rate | length | replacement_cost | rating | special_features                                       | last_update         |
+---------+------------------------+---------------------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+--------------------------------------------------------+---------------------+
|      85 | BONNIE HOLOCAUST       | A Fast-Paced Story of a Crocodile And a Robot who must Find a Moose in Ancient Japan                                      |         2006 |           1 |                 NULL |               4 |        0.99 |     63 |            29.99 | G      | Deleted Scenes                                         | 2006-02-15 05:03:42 |
|     172 | CONEHEADS SMOOCHY      | A Touching Story of a Womanizer And a Composer who must Pursue a Husband in Nigeria                                       |         2006 |           1 |                 NULL |               7 |        4.99 |    112 |            12.99 | NC-17  | Deleted Scenes,Behind the Scenes                       | 2006-02-15 05:03:42 |
|     173 | CONFESSIONS MAGUIRE    | A Insightful Story of a Car And a Boy who must Battle a Technical Writer in A Baloon                                      |         2006 |           1 |                 NULL |               7 |        4.99 |     65 |            25.99 | PG-13  | Behind the Scenes                                      | 2006-02-15 05:03:42 |
|     174 | CONFIDENTIAL INTERVIEW | A Stunning Reflection of a Cat And a Woman who must Find a Astronaut in Ancient Japan                                     |         2006 |           1 |                 NULL |               6 |        4.99 |    180 |            13.99 | NC-17  | Commentaries                                           | 2006-02-15 05:03:42 |
|     175 | CONFUSED CANDLES       | A Stunning Epistle of a Cat And a Forensic Psychologist who must Confront a Pioneer in A Baloon                           |         2006 |           1 |                 NULL |               3 |        2.99 |    122 |            27.99 | PG-13  | Trailers,Commentaries,Deleted Scenes,Behind the Scenes | 2006-02-15 05:03:42 |
|     176 | CONGENIALITY QUEST     | A Touching Documentary of a Cat And a Pastry Chef who must Find a Lumberjack in A Baloon                                  |         2006 |           1 |                 NULL |               6 |        0.99 |     87 |            21.99 | PG-13  | Commentaries,Behind the Scenes                         | 2006-02-15 05:03:42 |
|     177 | CONNECTICUT TRAMP      | A Unbelieveable Drama of a Crocodile And a Mad Cow who must Reach a Dentist in A Shark Tank                               |         2006 |           1 |                 NULL |               4 |        4.99 |    172 |            20.99 | R      | Commentaries,Deleted Scenes                            | 2006-02-15 05:03:42 |
|     178 | CONNECTION MICROCOSMOS | A Fateful Documentary of a Crocodile And a Husband who must Face a Husband in The First Manned Space Station              |         2006 |           1 |                 NULL |               6 |        0.99 |    115 |            25.99 | G      | Deleted Scenes,Behind the Scenes                       | 2006-02-15 05:03:42 |
|     179 | CONQUERER NUTS         | A Taut Drama of a Mad Scientist And a Man who must Escape a Pioneer in An Abandoned Mine Shaft                            |         2006 |           1 |                 NULL |               4 |        4.99 |    173 |            14.99 | G      | Commentaries,Deleted Scenes,Behind the Scenes          | 2006-02-15 05:03:42 |
|     180 | CONSPIRACY SPIRIT      | A Awe-Inspiring Story of a Student And a Frisbee who must Conquer a Crocodile in An Abandoned Mine Shaft                  |         2006 |           1 |                 NULL |               4 |        2.99 |    184 |            27.99 | PG-13  | Trailers,Commentaries                                  | 2006-02-15 05:03:42 |
|     181 | CONTACT ANONYMOUS      | A Insightful Display of a A Shark And a Monkey who must Face a Database Administrator in Ancient India                    |         2006 |           1 |                 NULL |               7 |        2.99 |    166 |            10.99 | PG-13  | Commentaries                                           | 2006-02-15 05:03:42 |
|     182 | CONTROL ANTHEM         | A Fateful Documentary of a Robot And a Student who must Battle a Cat in A Monastery                                       |         2006 |           1 |                 NULL |               7 |        4.99 |    185 |             9.99 | G      | Commentaries                                           | 2006-02-15 05:03:42 |
|     183 | CONVERSATION DOWNHILL  | A Taut Character Study of a Husband And a Waitress who must Sink a Squirrel in A MySQL Convention                         |         2006 |           1 |                 NULL |               4 |        4.99 |    112 |            14.99 | R      | Commentaries                                           | 2006-02-15 05:03:42 |
|     241 | DONNIE ALLEY           | A Awe-Inspiring Tale of a Butler And a Frisbee who must Vanquish a Teacher in Ancient Japan                               |         2006 |           1 |                 NULL |               4 |        0.99 |    125 |            20.99 | NC-17  | Trailers,Commentaries,Behind the Scenes                | 2006-02-15 05:03:42 |
|     368 | GONE TROUBLE           | A Insightful Character Study of a Mad Cow And a Forensic Psychologist who must Conquer a A Shark in A Manhattan Penthouse |         2006 |           1 |                 NULL |               7 |        2.99 |     84 |            20.99 | R      | Deleted Scenes,Behind the Scenes                       | 2006-02-15 05:03:42 |
|     429 | HONEY TIES             | A Taut Story of a Waitress And a Crocodile who must Outrace a Lumberjack in A Shark Tank                                  |         2006 |           1 |                 NULL |               3 |        0.99 |     84 |            29.99 | R      | Trailers,Commentaries,Deleted Scenes                   | 2006-02-15 05:03:42 |
|     529 | LONELY ELEPHANT        | A Intrepid Story of a Student And a Dog who must Challenge a Explorer in Soviet Georgia                                   |         2006 |           1 |                 NULL |               3 |        2.99 |     67 |            12.99 | G      | Trailers,Commentaries,Deleted Scenes,Behind the Scenes | 2006-02-15 05:03:42 |
|     590 | MONEY HAROLD           | A Touching Tale of a Explorer And a Boat who must Defeat a Robot in Australia                                             |         2006 |           1 |                 NULL |               3 |        2.99 |    135 |            17.99 | PG     | Trailers,Commentaries                                  | 2006-02-15 05:03:42 |
|     591 | MONSOON CAUSE          | A Astounding Tale of a Crocodile And a Car who must Outrace a Squirrel in A U-Boat                                        |         2006 |           1 |                 NULL |               6 |        4.99 |    182 |            20.99 | PG     | Commentaries,Behind the Scenes                         | 2006-02-15 05:03:42 |
|     592 | MONSTER SPARTACUS      | A Fast-Paced Story of a Waitress And a Cat who must Fight a Girl in Australia                                             |         2006 |           1 |                 NULL |               6 |        2.99 |    107 |            28.99 | PG     | Commentaries,Behind the Scenes                         | 2006-02-15 05:03:42 |
|     593 | MONTEREY LABYRINTH     | A Awe-Inspiring Drama of a Monkey And a Composer who must Escape a Feminist in A U-Boat                                   |         2006 |           1 |                 NULL |               6 |        0.99 |    158 |            13.99 | G      | Trailers,Commentaries                                  | 2006-02-15 05:03:42 |
|     594 | MONTEZUMA COMMAND      | A Thrilling Reflection of a Waitress And a Butler who must Battle a Butler in A Jet Boat                                  |         2006 |           1 |                 NULL |               6 |        0.99 |    126 |            22.99 | NC-17  | Trailers                                               | 2006-02-15 05:03:42 |
|     625 | NONE SPIKING           | A Boring Reflection of a Secret Agent And a Astronaut who must Face a Composer in A Manhattan Penthouse                   |         2006 |           1 |                 NULL |               3 |        0.99 |     83 |            18.99 | NC-17  | Trailers,Commentaries                                  | 2006-02-15 05:03:42 |
|     690 | POND SEATTLE           | A Stunning Drama of a Teacher And a Boat who must Battle a Feminist in Ancient China                                      |         2006 |           1 |                 NULL |               7 |        2.99 |    185 |            25.99 | PG-13  | Trailers,Commentaries,Behind the Scenes                | 2006-02-15 05:03:42 |
|     819 | SONG HEDWIG            | A Amazing Documentary of a Man And a Husband who must Confront a Squirrel in A MySQL Convention                           |         2006 |           1 |                 NULL |               3 |        0.99 |    165 |            29.99 | PG-13  | Trailers,Deleted Scenes                                | 2006-02-15 05:03:42 |
|     820 | SONS INTERVIEW         | A Taut Character Study of a Explorer And a Mad Cow who must Battle a Hunter in Ancient China                              |         2006 |           1 |                 NULL |               3 |        2.99 |    184 |            11.99 | NC-17  | Commentaries,Behind the Scenes                         | 2006-02-15 05:03:42 |
|     983 | WON DARES              | A Unbelieveable Documentary of a Teacher And a Monkey who must Defeat a Explorer in A U-Boat                              |         2006 |           1 |                 NULL |               7 |        2.99 |    105 |            18.99 | PG     | Behind the Scenes                                      | 2006-02-15 05:03:42 |
|     984 | WONDERFUL DROP         | A Boring Panorama of a Woman And a Madman who must Overcome a Butler in A U-Boat                                          |         2006 |           1 |                 NULL |               3 |        2.99 |    126 |            20.99 | NC-17  | Commentaries                                           | 2006-02-15 05:03:42 |
|     985 | WONDERLAND CHRISTMAS   | A Awe-Inspiring Character Study of a Waitress And a Car who must Pursue a Mad Scientist in The First Manned Space Station |         2006 |           1 |                 NULL |               4 |        4.99 |    111 |            19.99 | PG     | Commentaries                                           | 2006-02-15 05:03:42 |
|     986 | WONKA SEA              | A Brilliant Saga of a Boat And a Mad Scientist who must Meet a Moose in Ancient India                                     |         2006 |           1 |                 NULL |               6 |        2.99 |     85 |            24.99 | NC-17  | Trailers,Commentaries                                  | 2006-02-15 05:03:42 |
+---------+------------------------+---------------------------------------------------------------------------------------------------------------------------+--------------+-------------+----------------------+-----------------+-------------+--------+------------------+--------+--------------------------------------------------------+---------------------+
30 rows in set (0.09 sec)

mysql> show tables ;
+----------------------------+
| Tables_in_sakila           |
+----------------------------+
| actor                      |
| actor_copy                 |
| actor_info                 |
| address                    |
| category                   |
| city                       |
| country                    |
| customer                   |
| customer_list              |
| film                       |
| film_actor                 |
| film_category              |
| film_list                  |
| film_text                  |
| inventory                  |
| language                   |
| nicer_but_slower_film_list |
| payment                    |
| rental                     |
| sales_by_film_category     |
| sales_by_store             |
| staff                      |
| staff_list                 |
| store                      |
+----------------------------+
24 rows in set (0.00 sec)

mysql> desc custumer ;
ERROR 1146 (42S02): Table 'sakila.custumer' doesn't exist
mysql> desc customer ;
+-------------+-------------------+------+-----+-------------------+-----------------------------------------------+
| Field       | Type              | Null | Key | Default           | Extra                                         |
+-------------+-------------------+------+-----+-------------------+-----------------------------------------------+
| customer_id | smallint unsigned | NO   | PRI | NULL              | auto_increment                                |
| store_id    | tinyint unsigned  | NO   | MUL | NULL              |                                               |
| first_name  | varchar(45)       | NO   |     | NULL              |                                               |
| last_name   | varchar(45)       | NO   | MUL | NULL              |                                               |
| email       | varchar(50)       | YES  |     | NULL              |                                               |
| address_id  | smallint unsigned | NO   | MUL | NULL              |                                               |
| active      | tinyint(1)        | NO   |     | 1                 |                                               |
| create_date | datetime          | NO   |     | NULL              |                                               |
| last_update | timestamp         | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED on update CURRENT_TIMESTAMP |
+-------------+-------------------+------+-----+-------------------+-----------------------------------------------+
9 rows in set (0.00 sec)

mysql> select customer_id , first_name
    -> from customer
    -> where first_name = 'tommy';
+-------------+------------+
| customer_id | first_name |
+-------------+------------+
|         459 | TOMMY      |
+-------------+------------+
1 row in set (0.10 sec)

mysql> from customer
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from customer' at line 1
mysql> select customer_id , first_name
    -> from customer
    -> where first_name = 'torres' or first_name = 'jessie';
+-------------+------------+
| customer_id | first_name |
+-------------+------------+
|         215 | JESSIE     |
|         533 | JESSIE     |
+-------------+------------+
2 rows in set (0.00 sec)

mysql>