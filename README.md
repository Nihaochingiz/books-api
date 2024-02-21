### README.md

#### Description
This Go code provides a simple RESTful API to manage a "books" database. It allows users to perform operations like retrieving all books, creating a new book entry, deleting a specific book, and deleting all books.

#### Database Table
To use this code, you need to create a table named `books` in your PostgreSQL database. Below is the SQL query to create the `books` table:

```sql
CREATE TABLE books (
    id SERIAL PRIMARY KEY,
    bookid character varying(50) NOT NULL,
    bookname character varying(255) NOT NULL
);
```

#### API Endpoints
- **GET all books:** Retrieve all books from the database.
  ```bash
  curl -X GET http://localhost:8000/books/
  ```

- **CREATE a book:** Add a new book to the database.
  ```bash
  curl -X POST http://localhost:8000/books/ -d "bookid=123&bookname=SampleBook" -H "Content-Type: application/x-www-form-urlencoded"
  ```

- **DELETE a specific book by bookID:** Remove a book from the database using its bookID.
  ```bash
  curl -X DELETE http://localhost:8000/books/{bookid}
  ```

- **DELETE all books:** Delete all books from the database.
  ```bash
  curl -X DELETE http://localhost:8000/books/
  ```

#### Code Explanation
The code implements a simple HTTP server using the Gorilla Mux library in Go. It provides endpoints for managing books in a PostgreSQL database. The code includes functions for handling GET, POST, and DELETE requests for books.

1. **GetBooks:** Retrieves all books from the database, excluding the book with the ID "1".
2. **CreateBook:** Adds a new book to the database using the provided bookID and bookName.
3. **DeleteBook:** Deletes a specific book from the database based on the bookID.
4. **DeleteBooks:** Deletes all books from the database.

#### Running the Code
1. Ensure you have the required dependencies by running `go mod tidy`.
2. Create the `books` table in your PostgreSQL database.
3. Update the database details (DB_USER, DB_PASSWORD, DB_NAME) in the code if necessary.
4. Run the Go application using `go run main.go`.
5. Test the API using cURL commands as shown in the examples above.

