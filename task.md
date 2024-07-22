
# API Documentation

## Books API

### Retrieve Books
```
GET /books/
```
Retrieve a list of books.

### Create Book
```
POST /books/
```
Create a new book.

### Retrieve Book
```
GET /books/{book_id}
```
Retrieve details of a specific book.

### Update Book
```
PUT /books/{book_id}
```
Update details of a specific book.

## Authors API

### Retrieve Authors
```
GET /authors/
```
Retrieve a list of authors.

### Create Author
```
POST /authors/
```
Create a new author.

### Retrieve Author
```
GET /authors/{author_id}
```
Retrieve details of a specific author.

### Update Author
```
PUT /authors/{author_id}
```
Update details of a specific author.

## Users API

### Retrieve Users
```
GET /users/
```
Retrieve a list of users.

### Create User
```
POST /users/
```
Create a new user.

### Retrieve User
```
GET /users/{user_id}
```
Retrieve details of a specific user.

### Update User
```
PUT /users/{user_id}
```
Update details of a specific user.

## Reviews API

### Retrieve Reviews
```
GET /books/{book_id}/reviews
```
Retrieve a list of reviews.

### Create Review
```
POST /books/{book_id}/reviews
```
Create a new review.

### Retrieve Review
```
GET /books/{book_id}/reviews/{review_id}
```
Retrieve details of a specific review.

### Update Review
```
PUT /books/{book_id}/reviews/{review_id}
```
Update details of a specific review.

## Categories API

### Retrieve Categories
```
GET /categories/
```
Retrieve a list of categories.

### Create Category
```
POST /categories/
```
Create a new category.

### Retrieve Category
```
GET /categories/{category_id}
```
Retrieve details of a specific category.

### Update Category
```
PUT /categories/{category_id}
```
Update details of a specific category.
```
