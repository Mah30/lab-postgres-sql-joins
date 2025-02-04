![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Answers

## Iteration 2 - Joins

1. Using an **INNER JOIN**, list all books (left table) that have an assigned author (right table). The result should include only books with assigned authors.

```sql
-- Your Query Goes Here
select books.title, authors.name  
from books INNER JOIN authors 
on books.author_id = authors.id;


                 title                  |      name       
-----------------------------------------+-----------------
 Harry Potter and the Chamber of Secrets | J.K. Rowling
 Harry Potter and the Goblet of Fire     | J.K. Rowling
 1984                                    | George Orwell
 Animal Farm                             | George Orwell
 Adventures of Huckleberry Finn          | Mark Twain
 The Adventures of Tom Sawyer            | Mark Twain
 Murder on the Orient Express            | Agatha Christie
 Oliver Twist                            | Charles Dickens
 To Kill a Mockingbird                   | Harper Lee
(9 rows)


```

<br>

2. Using a **LEFT JOIN**, list all authors (left table) and their corresponding books on the (right table). The result should include all authors, including those who don't have any books assigned.

```sql
-- Your Query Goes Here
select authors.name, books.title from authors left join books on authors.id = books.author_id;

name         |                  title                  
---------------------+-----------------------------------------
 J.K. Rowling        | Harry Potter and the Chamber of Secrets
 J.K. Rowling        | Harry Potter and the Goblet of Fire
 George Orwell       | 1984
 George Orwell       | Animal Farm
 Mark Twain          | Adventures of Huckleberry Finn
 Mark Twain          | The Adventures of Tom Sawyer
 Agatha Christie     | Murder on the Orient Express
 Charles Dickens     | Oliver Twist
 Harper Lee          | To Kill a Mockingbird
 Stephen King        | 
 Virginia Woolf      | 
 F. Scott Fitzgerald | 
 Leo Tolstoy         | 
(13 rows)

```

<br>

3. Using a **RIGHT JOIN**, list all books (right table) and their corresponding authors on the (left table). The result should include books without assigned authors.

```sql
-- Your Query Goes Here
select books.title, authors.name from books right join authors on books.author_id = authors.id;


                  title                  |        name         
-----------------------------------------+---------------------
 Harry Potter and the Chamber of Secrets | J.K. Rowling
 Harry Potter and the Goblet of Fire     | J.K. Rowling
 1984                                    | George Orwell
 Animal Farm                             | George Orwell
 Adventures of Huckleberry Finn          | Mark Twain
 The Adventures of Tom Sawyer            | Mark Twain
 Murder on the Orient Express            | Agatha Christie
 Oliver Twist                            | Charles Dickens
 To Kill a Mockingbird                   | Harper Lee
                                         | Stephen King
                                         | Virginia Woolf
                                         | F. Scott Fitzgerald
                                         | Leo Tolstoy
(13 rows)

```

<br>

4. Using a **FULL JOIN**, list all records from the `books` and `authors` tables. The result should include all details from both tables, even if there are no match.

```sql
-- Your Query Goes Here
select books.title, authors.name
from books FULL JOIN authors 
on books.author_id = authors.id;


                  title                  |        name         
-----------------------------------------+---------------------
 Harry Potter and the Chamber of Secrets | J.K. Rowling
 Harry Potter and the Goblet of Fire     | J.K. Rowling
 1984                                    | George Orwell
 Animal Farm                             | George Orwell
 Adventures of Huckleberry Finn          | Mark Twain
 The Adventures of Tom Sawyer            | Mark Twain
 Murder on the Orient Express            | Agatha Christie
 Oliver Twist                            | Charles Dickens
 To Kill a Mockingbird                   | Harper Lee
 The Mysterious Manuscript               | 
 Echoes in the Void                      | 
                                         | Stephen King
                                         | Virginia Woolf
                                         | F. Scott Fitzgerald
                                         | Leo Tolstoy
(15 rows)


```

<br>

## BonUS: Iteration 3 - Joins (continued)

1. Using an **INNER JOIN**, list all books (left table) and their corresponding publishers on the (right table). The result should include the book's title, publisher's name, and location.

```sql
-- Your Query Goes Here
select books.title, publishers.name, publishers.location from books inner join publishers on books.publisher_id = publishers.id;

                  title                  |         name         | location 
-----------------------------------------+----------------------+----------
 Harry Potter and the Chamber of Secrets | Bloomsbury           | London
 Harry Potter and the Goblet of Fire     | Bloomsbury           | London
 1984                                    | Secker & Warburg     | London
 Animal Farm                             | Secker & Warburg     | London
 Adventures of Huckleberry Finn          | Chatto & Windus      | London
 The Adventures of Tom Sawyer            | Chatto & Windus      | London
 Murder on the Orient Express            | Penguin Books        | London
 Oliver Twist                            | Simon & Schuster     | New York
 To Kill a Mockingbird                   | Macmillan Publishers | London
(9 rows)

```

<br>

2. Using a **LEFT JOIN**, list all publishers (left table) and any books they have published on the (right table). The result should include all publishers, including those who haven't published any books.

```sql
-- Your Query Goes Here
select publishers.name, books.title
from publishers
LEFT JOIN books on publishers.id = books.publisher_id;


         name         |                  title                  
----------------------+-----------------------------------------
 Bloomsbury           | Harry Potter and the Chamber of Secrets
 Bloomsbury           | Harry Potter and the Goblet of Fire
 Secker & Warburg     | 1984
 Secker & Warburg     | Animal Farm
 Chatto & Windus      | Adventures of Huckleberry Finn
 Chatto & Windus      | The Adventures of Tom Sawyer
 Penguin Books        | Murder on the Orient Express
 Simon & Schuster     | Oliver Twist
 Macmillan Publishers | To Kill a Mockingbird
 Hachette Book Group  | 
 HarperCollins        | 
 Scholastic Inc.      | 
 Random House         | 
(13 rows)

```

<br>

3. Using a **RIGHT JOIN**, list all books (right table) and their corresponding publishers on the (left table). The result should include all books, even those without a linked publisher.

```sql
-- Your Query Goes Here
select books.title, publishers.name
from books RIGHT JOIN publishers on books.publisher_id = publishers.id;


                  title                  |         name         
-----------------------------------------+----------------------
 Harry Potter and the Chamber of Secrets | Bloomsbury
 Harry Potter and the Goblet of Fire     | Bloomsbury
 1984                                    | Secker & Warburg
 Animal Farm                             | Secker & Warburg
 Adventures of Huckleberry Finn          | Chatto & Windus
 The Adventures of Tom Sawyer            | Chatto & Windus
 Murder on the Orient Express            | Penguin Books
 Oliver Twist                            | Simon & Schuster
 To Kill a Mockingbird                   | Macmillan Publishers
                                         | Hachette Book Group
                                         | HarperCollins
                                         | Scholastic Inc.
                                         | Random House
(13 rows)


```

<br>

4. Using a **FULL JOIN**, list all records from the `authors`, `books`, and `publishers` tables. The result should include all records from the three tables, even if there are no matches between them.

```sql
-- Your Query Goes Here

select books.title, authors.name, publishers.name
from books FULL JOIN authors on books.author_id = authors.id
FULL JOIN publishers on books.publisher_id = publishers.id;

                  title                  |        name         |         name         
-----------------------------------------+---------------------+----------------------
 Harry Potter and the Chamber of Secrets | J.K. Rowling        | Bloomsbury
 Harry Potter and the Goblet of Fire     | J.K. Rowling        | Bloomsbury
 1984                                    | George Orwell       | Secker & Warburg
 Animal Farm                             | George Orwell       | Secker & Warburg
 Adventures of Huckleberry Finn          | Mark Twain          | Chatto & Windus
 The Adventures of Tom Sawyer            | Mark Twain          | Chatto & Windus
 Murder on the Orient Express            | Agatha Christie     | Penguin Books
 Oliver Twist                            | Charles Dickens     | Simon & Schuster
 To Kill a Mockingbird                   | Harper Lee          | Macmillan Publishers
 The Mysterious Manuscript               |                     | 
 Echoes in the Void                      |                     | 
                                         | Stephen King        | 
                                         | Virginia Woolf      | 
                                         | F. Scott Fitzgerald | 
                                         | Leo Tolstoy         | 
                                         |                     | Hachette Book Group
                                         |                     | HarperCollins
                                         |                     | Scholastic Inc.
                                         |                     | Random House
(19 rows)

```

<br>
