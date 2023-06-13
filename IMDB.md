1. Movie should have multiple media

CREATE TABLE MOVIE (
  id INT NOT NULL,
  mov_title TEXT NOT NULL,
  mov_year INT NOT NULL,
  duration_min INT NOT NULL,
  language TEXT NOT NULL
);

INSERT INTO MOVIE VALUES (1, 'Avatar', 2009, 162, 'English');
INSERT INTO MOVIE VALUES (2, 'The Avengers', 2012, 160, 'English');
INSERT INTO MOVIE VALUES (3, 'Jurassic World', 2015, 124, 'English');
INSERT INTO MOVIE VALUES (4, 'Furious 7', 2015, 137, 'English');
INSERT INTO MOVIE VALUES (5, 'Iron Man 3', 2013, 130, 'English');

-- create Movie_media
CREATE TABLE Movie_media (
  med_id INT NOT NULL,
  mov_id INT NOT NULL,
  actor_name TEXT NOT NULL,
  director TEXT NOT NULL,
  music TEXT NOT NULL
);

INSERT INTO Movie_media VALUES (101, 1, 'Sam Worthington', 'James Cameron', 'James Horner');
INSERT INTO Movie_media VALUES (102, 2, 'Robert Downey Jr.', 'Joss Whedon', 'Alan Silvestri');
INSERT INTO Movie_media VALUES (103, 3, 'Chris Pratt', 'Colin Trevorrow', 'Michael Giacchino');
INSERT INTO Movie_media VALUES (104, 4, 'Vin Diesel', 'James Wan', 'Brian Tyler');
INSERT INTO Movie_media VALUES (105, 5, 'Robert Downey Jr.', 'Shane Black', 'Brian Tyler');

-- fetch 
SELECT * FROM Movie 
LEFT JOIN Movie_media 
ON 
Movie.id=Movie_media.mov_id;

2. Movie can belongs to multiple Genres

CREATE TABLE MOVIE (
  id INT NOT NULL,
  mov_title TEXT NOT NULL,
  mov_year INT NOT NULL,
  duration_min INT NOT NULL,
  language TEXT NOT NULL
);

INSERT INTO MOVIE VALUES (1, 'Avatar', 2009, 162, 'English');
INSERT INTO MOVIE VALUES (2, 'The Avengers', 2012, 160, 'English');
INSERT INTO MOVIE VALUES (3, 'Jurassic World', 2015, 124, 'English');
INSERT INTO MOVIE VALUES (4, 'Furious 7', 2015, 137, 'English');
INSERT INTO MOVIE VALUES (5, 'Iron Man 3', 2013, 130, 'English');

CREATE TABLE genres (
  gen_id int NOT NULL,
  mov_id INT NOT NULL,
  gen_title TEXT NOT NULL
);

-- insert
INSERT INTO genres VALUES (1001, 1, 'Fantasy');
INSERT INTO genres VALUES (1002, 2, 'Fantasy');
INSERT INTO genres VALUES (1003, 3, 'Adventure');
INSERT INTO genres VALUES (1004, 4, 'Action');
INSERT INTO genres VALUES (1005, 5, 'Sci-Fi');


-- fetch 
SELECT * FROM Movie 
INNER JOIN genres 
ON 
Movie.id=genres.mov_id;

3. Movie can have multiple reviews and Review can belongs to a user.

CREATE TABLE MOVIE (
  id INT NOT NULL,
  mov_title TEXT NOT NULL,
  mov_year INT NOT NULL,
  duration_min INT NOT NULL,
  language TEXT NOT NULL
);

INSERT INTO MOVIE VALUES (1, 'Avatar', 2009, 162, 'English');
INSERT INTO MOVIE VALUES (2, 'The Avengers', 2012, 160, 'English');
INSERT INTO MOVIE VALUES (3, 'Jurassic World', 2015, 124, 'English');
INSERT INTO MOVIE VALUES (4, 'Furious 7', 2015, 137, 'English');
INSERT INTO MOVIE VALUES (5, 'Iron Man 3', 2013, 130, 'English');

-- create Rating
CREATE TABLE Rating (
  id INT NOT NULL,
  mov_id INT NOT NULL,
  rev_stars INT NOT NULL,
  num_o_users_rate INT NOT NULL
);

INSERT INTO Rating VALUES (301, 1, 8.40, 263575);
INSERT INTO Rating VALUES (302, 2, 7.90, 20207);
INSERT INTO Rating VALUES (303, 3, 8.30, 202778);
INSERT INTO Rating VALUES (304, 4, 8.20, 484746);
INSERT INTO Rating VALUES (305, 5, 9.00, 563575);

-- fetch 
SELECT * FROM Movie 
INNER JOIN Rating 
ON 
Movie.id=Rating.mov_id;

4. Artist can have multiple skills

-- create ACTOR
CREATE TABLE ACTOR (
  id int NOT NULL,
  act_name TEXT NOT NULL
);

-- insert
INSERT INTO ACTOR VALUES (0001, 'Sam Worthington');
INSERT INTO ACTOR VALUES (0002, 'Robert Downey Jr.');
INSERT INTO ACTOR VALUES (0003, 'Chris Pratt');
INSERT INTO ACTOR VALUES (0004, 'Vin Diesel');
INSERT INTO ACTOR VALUES (0005, 'Robert Downey Jr.');

-- create act_skills
CREATE TABLE act_skills (
  act_id int NOT NULL,
  Skills TEXT NOT NULL
);

INSERT INTO act_skills VALUES (0001, 'Actor, Car_Racer');
INSERT INTO act_skills VALUES (0002, 'Actor, Singer, Filmmaker, Politician');
INSERT INTO act_skills VALUES (0003, 'Actor, Dancer');
INSERT INTO act_skills VALUES (0004, 'Actor, Singer, Dancer');
INSERT INTO act_skills VALUES (0005, 'Actor, Producer');

-- fetch 
SELECT * FROM Actor 
INNER JOIN act_skills 
ON 
Actor.id=act_skills.act_id;

5. Artist can perform multiple role in a single film.

CREATE TABLE MOVIE (
  id INT NOT NULL,
  mov_title TEXT NOT NULL,
  mov_year INT NOT NULL,
  duration_min INT NOT NULL,
  language TEXT NOT NULL
);

INSERT INTO MOVIE VALUES (1, 'Avatar', 2009, 162, 'English');
INSERT INTO MOVIE VALUES (2, 'The Avengers', 2012, 160, 'English');
INSERT INTO MOVIE VALUES (3, 'Jurassic World', 2015, 124, 'English');
INSERT INTO MOVIE VALUES (4, 'Furious 7', 2015, 137, 'English');
INSERT INTO MOVIE VALUES (5, 'Iron Man 3', 2013, 130, 'English');
-- create roll 
CREATE TABLE roll ( mov_id INT NOT NULL, actor TEXT NOT NULL, roll_1 TEXT NOT NULL, roll_2 TEXT NOT NULL );

INSERT INTO roll VALUES (5, 'Robert Downey Jr.', 'Billionaire', 'MK42');

-- fetch SELECT * FROM Movie LEFT JOIN roll ON Movie.id=roll.mov_id;
