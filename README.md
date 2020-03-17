### Примеры SQL - запросов

Реализация связи многие ко многим для вывода раздела с книгами
- Внутренние объединения:

		" SELECT books.* FROM books, books2books_author, books2books_genre
		  WHERE (
			books.id = books2books_author.books_id 
		  	AND
			books2books_author.books_author_id = ".$author."
		  ) AND (
			books.id = books2books_genre.books_id  
			AND
			books2books_genre.books_genre_id = ".$genre."
		  )
        LIMIT ".$limit." OFFSET ".$offset." "


- UNION - объединение:

		" SELECT SQL_CALC_FOUND_ROWS * FROM books 
		  WHERE id IN (
			SELECT books_id FROM books2books_author 
			WHERE books_author_id IN (".$author.")
			UNION 
			SELECT books_id FROM books2books_genre 
			WHERE books_genre_id IN (".$genre.")
		  )
     	LIMIT ".$limit." OFFSET ".$offset." "





