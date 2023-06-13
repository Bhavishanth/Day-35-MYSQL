1Q. 1. Movie should have multiple media

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
