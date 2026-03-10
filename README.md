1.Create Database
CREATE DATABASE imdb;

SHOW DATABASES;

USE imdb;

#output

![image alt] (https://github.com/sanika233/PAT-Task-7/blob/68965ec02f52f88eb378a9611196b27c49f0c7e8/Screenshot%202026-03-09%20234639.png)

2. Create Movies Table

CREATE TABLE movies(
movie_id INT AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(200),
release_year INT
);

DESC movies;

#output
![image alt] (https://github.com/sanika233/PAT-Task-7/blob/7540155ed9484218ffadb6f4ecc1a229435ca8fd/Create%20Movies%20Table.png)

3. Create Media Table (Movie → Multiple Media)

CREATE TABLE media(
media_id INT AUTO_INCREMENT PRIMARY KEY,
movie_id INT,
media_type VARCHAR(50),
media_url VARCHAR(255),
FOREIGN KEY(movie_id) REFERENCES movies(movie_id)
);

SHOW TABLES;
#output
![image alt] (https://github.com/sanika233/PAT-Task-7/blob/3f92c3d3c05c45cfcf6fe0999265278dd114ba47/3Create%20Media%20Table%20(Movie%20%E2%86%92%20Multiple%20Media).png)


4. Create Genre Tables (Many-to-Many)

CREATE TABLE genres(
genre_id INT AUTO_INCREMENT PRIMARY KEY,
genre_name VARCHAR(100)
);
SHOW TABLES;

CREATE TABLE movie_genre(
movie_id INT,
genre_id INT,
PRIMARY KEY(movie_id,genre_id),
FOREIGN KEY(movie_id) REFERENCES movies(movie_id),
FOREIGN KEY(genre_id) REFERENCES genres(genre_id)
);

SHOW TABLES ;
SELECT * FROM genres;
SELECT * FROM movie_genre;


5. Create Users and Reviews Tables

CREATE TABLE users(
user_id INT AUTO_INCREMENT PRIMARY KEY,
username VARCHAR(100)
);

SHOW TABLES ;

CREATE TABLE reviews(
review_id INT AUTO_INCREMENT PRIMARY KEY,
movie_id INT,
user_id INT,
rating INT,
review TEXT,
FOREIGN KEY(movie_id) REFERENCES movies(movie_id),
FOREIGN KEY(user_id) REFERENCES users(user_id)
);


#output

![image alt](https://github.com/sanika233/PAT-Task-7/blob/bb40e03f81bb90e49f56b9bc43c1f616025ea903/Create%20Genre%20%2C%20Users%20and%20Reviews%20Tables.png)


6. 

