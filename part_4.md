ANSWERS

1. Find the author with the name 'Kara Melton' and then select all the articles she has written.

----> SELECT author_id, title FROM articles WHERE author_id = (SELECT id FROM authors WHERE name = 'Kara Melton');

O/P:  8 | How Tech Business Models Come From Marginalized Communities, But Startups Are Still Mostly White
      8 | Confronting the Assumption of Whiteness in Virtual Spaces


2. Find Ontario in the provinces table and then find all the cities in that province.

----> SELECT * FROM cities WHERE province_id = (SELECT id FROM provinces WHERE name = 'Ontario');

O/P:  8 | Toronto |         1793 |          14
      11 | Ottawa  |         1826 |          14


3. Who wrote the article called 'Coding Bootcamps and Emotional Labor'?

----> SELECT id, name FROM authors WHERE id = (SELECT author_id FROM articles WHERE title = 'Coding Bootcamps and Emotional Labor');

O/P:  4 | Tilde Ann Thurium


4. Write a series of SQL queries to find out how many provinces are in Canada.

----> SELECT count() FROM provinces WHERE country_id = (SELECT id FROM countries WHERE name = 'Canada');

O/P: 14


5. How many people live at 4740 McDermott Street?

----> SELECT * FROM persons WHERE residence_id = (SELECT id  FROM residences WHERE address = '4740 McDermott Street');

O/P: 16 | Malvina King |  28 |            9
     17 | Theo Wolff   |  27 |            9


6. What city is 4740 McDermott Street in?

----> SELECT * FROM cities WHERE id = (SELECT id  FROM residences WHERE address = '4740 McDermott Street');

O/P:  9 | Montreal |         1642 |          15


7. What province is 4740 McDermott Street in?

----> SELECT * FROM provinces WHERE id = (SELECT province_id FROM cities WHERE id = (SELECT id  FROM residences WHERE address = '4740 McDermott Street')) ;

O/P:  15 | Quebec |         1867 |          1


8. What country is 4740 McDermott Street in?

----> SELECT * FROM countries WHERE id = (select country_id from provinces where id = (SELECT province_id FROM cities WHERE id = (SELECT id  FROM residences WHERE address = '4740 McDermott Street')));

O/P:  1 | Canada |         1867 | beaver


9. Find the person named 'Destini Davis' and then use a series of SQL queries to find what country they live in.

----> SELECT * FROM countries WHERE id = (SELECT country_id FROM provinces WHERE id = (SELECT province_id FROM cities WHERE id = (SELECT city_id FROM residences WHERE id = (SELECT residence_id FROM persons WHERE name = 'Destini Davis'))));

O/P:   1 | Canada |         1867 | beaver


10. How many articles has Aditya Mukerjee written?

----> SELECT author_id, title FROM articles WHERE author_id = (SELECT id FROM authors WHERE name = 'Aditya Mukerjee');

O/P:  2 | I Can Text You A Pile of Poo, But I Can’t Write My Name
