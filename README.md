1.Create Database
CREATE DATABASE imdb;

SHOW DATABASES;

USE imdb;

#output

![image alt](https://github.com/sanika233/PAT-Task-7/blob/68965ec02f52f88eb378a9611196b27c49f0c7e8/Screenshot%202026-03-09%20234639.png)

2. Create Movies Table

CREATE TABLE movies(
movie_id INT AUTO_INCREMENT PRIMARY KEY,
title VARCHAR(200),
release_year INT
);

DESC movies;

#output
![image alt](https://github.com/sanika233/PAT-Task-7/blob/7540155ed9484218ffadb6f4ecc1a229435ca8fd/Create%20Movies%20Table.png)

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
![image alt](https://github.com/sanika233/PAT-Task-7/blob/3f92c3d3c05c45cfcf6fe0999265278dd114ba47/3Create%20Media%20Table%20(Movie%20%E2%86%92%20Multiple%20Media).png)


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

6. Create Artists and Skills Tables and Artist Roles Table

CREATE TABLE artists(
artist_id INT AUTO_INCREMENT PRIMARY KEY,
artist_name VARCHAR(200)
);

CREATE TABLE skills(
skill_id INT AUTO_INCREMENT PRIMARY KEY,
skill_name VARCHAR(100)
);

CREATE TABLE artist_skills(
artist_id INT,
skill_id INT,
PRIMARY KEY(artist_id,skill_id),
FOREIGN KEY(artist_id) REFERENCES artists(artist_id),
FOREIGN KEY(skill_id) REFERENCES skills(skill_id)
);

CREATE TABLE movie_artist_roles(
movie_id INT,
artist_id INT,
role VARCHAR(100),
PRIMARY KEY(movie_id,artist_id,role),
FOREIGN KEY(movie_id) REFERENCES movies(movie_id),
FOREIGN KEY(artist_id) REFERENCES artists(artist_id)
);


#output

![image alt](https://github.com/sanika233/PAT-Task-7/blob/732cd8a6ed91a9935fe69d58128c04ea4a32c106/6.%20Create%20Artists%20and%20Skills%20Tables%20and%20Artist%20Roles%20Table.png)

7. Insert Data

   INSERT INTO movies(title,release_year)
VALUES('Inception',2010);

INSERT INTO media(movie_id,media_type,media_url)
VALUES
(1,'image','poster.jpg'),
(1,'video','trailer.mp4');

INSERT INTO genres(genre_name)
VALUES('Action'),('Sci-Fi');

INSERT INTO movie_genre
VALUES(1,1),(1,2);

INSERT INTO users(username)
VALUES('Sanika'),('Rahul');

INSERT INTO reviews(movie_id,user_id,rating,review)
VALUES
(1,1,5,'Amazing movie'),
(1,2,4,'Great movie');

#output

![image alt](https://github.com/sanika233/PAT-Task-7/blob/f3a54dbf251d0dfc1bdb71c17e5e71f1d86c82e7/7.%20Insert%20Data.png)


![image alt](https://github.com/sanika233/PAT-Task-7/blob/c7198fc4050dc209b81e7f87cf58f3b30a1ca50b/8.%20media%20.png)

![image alt](https://github.com/sanika233/PAT-Task-7/blob/c7198fc4050dc209b81e7f87cf58f3b30a1ca50b/9.reviews%20tabel.png)


