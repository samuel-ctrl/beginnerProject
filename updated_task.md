### Updated Models:

1. **Book Model**:
```json
{
    "id": "6683f946ec61bfa6a3c2d7c7",
    "created_at": "2024-07-02T12:57:42.076000",
    "updated_at": "2024-07-02T12:57:42.076000",
    "name": "Harry Porter Chambers of secrets (VOLUME 1)",
    "description": "This is description about a book.",
    "author": "6683e1a4710824df4e5d76e9",
    "is_published": false,
    "category": "6683e1a4710824df4e5d76e9",
    "publisher": "6683e1a4710824df4e5d76e9",
    "average_rating": 4.5,
    "total_reviews": 150
}
```

2. **Author Model**:
```json
{
    "id": "6682cdeed4646ca7d4f37874",
    "created_at": "2024-07-01T15:40:30.960000",
    "updated_at": "2024-07-02T13:04:37.931231",
    "name": "James",
    "latest_books": [
        {
            "id": "6683f946ec61bfa6a3c2d7c7",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)"
        },
        {
            "id": "6683f98a7b7297bd6dcdf119",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)"
        },
        {
            "id": "6683f9afdc0e77f278b07ddf",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)"
        }
    ],
    "age": 25,
    "gender": "Male",
    "awards": [
        "Best writer of the decade - 2018 "
    ],
    "total_published": 4,
    "average_rating": 4.5
}
```

3. **User Model**:
```json
{
    "id": "6683abe1455818257eb1d668",
    "created_at": "2024-07-02T07:27:29.278000",
    "updated_at": "2024-07-02T07:27:29.278000",
    "name": "Albert Joseph",
    "email": "test@gmail.com",
    "gender": "Male",
    "phone_number": "+918856852123",
    "age": 25,
    "favorite_books": [
        {
            "id": "6683f946ec61bfa6a3c2d7c7",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)"
        }
    ],
    "total_reviews": 10
}
```

4. **Review Model**:
```json
{
    "id": "6683fbafb25f017d052716af",
    "created_at": "2024-07-02T13:07:59.425000",
    "updated_at": "2024-07-02T13:07:59.425000",
    "content": "This is the content",
    "rating": 4,
    "created_by": {
        "id": "6683abe1455818257eb1d668",
        "name": "Albert Joseph"
    },
    "book_id": {
        "id": "6683f946ec61bfa6a3c2d7c7",
        "name": "Harry Porter Chambers of secrets (VOLUME 1)"
    },
    "review_details": {
        "likes": 120,
        "comments": [
            {
                "id": "6683e1a4710824df4e5d76e9",
                "user": "John Doe",
                "content": "Great review!"
            }
        ]
    }
}
```

5. **Category Model**:
```json
{
    "id": "6683e1a4710824df4e5d76e9",
    "name": "Fiction",
    "description": "Fiction description"
}
```

6. **Publisher Model**:
```json
{
    "id": "6683e1a4710824df4e5d76e9",
    "name": "Penguin Random House",
    "location": "New York, USA",
    "books": [
        {
            "id": "6683f946ec61bfa6a3c2d7c7",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)"
        }
    ]
}
```

7. **Bookstore Model**:
```json
{
    "id": "6683e1a4710824df4e5d76e9",
    "name": "Barnes & Noble",
    "location": "New York, USA",
    "books": [
        {
            "id": "6683f946ec61bfa6a3c2d7c7",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)"
        }
    ]
}
```

### New Endpoints:

1. **Publisher Endpoints**:
    - `GET /publishers`: Retrieve all publishers.
    - `POST /publishers`: Create a new publisher.
    - `GET /publishers/{publisher_id}`: Retrieve a specific publisher.
    - `PUT /publishers/{publisher_id}`: Update a specific publisher.
    - `DELETE /publishers/{publisher_id}`: Delete a specific publisher.

2. **Bookstore Endpoints**:
    - `GET /bookstores`: Retrieve all bookstores.
    - `POST /bookstores`: Create a new bookstore.
    - `GET /bookstores/{bookstore_id}`: Retrieve a specific bookstore.
    - `PUT /bookstores/{bookstore_id}`: Update a specific bookstore.
    - `DELETE /bookstores/{bookstore_id}`: Delete a specific bookstore.
    - `POST /bookstores/{bookstore_id}/books/{book_id}`: Add a book to a bookstore's stock.
    - `DELETE /bookstores/{bookstore_id}/books/{book_id}`: Remove a book from a bookstore's stock.

3. **User Endpoints**:
    - `GET /users/{user_id}/favorite_books`: Retrieve a user's favorite books.
    - `POST /users/{user_id}/favorite_books/{book_id}`: Add a book to a user's favorite books.
    - `DELETE /users/{user_id}/favorite_books/{book_id}`: Remove a book from a user's favorite books.

4. **Review Details Endpoints**:
    - `GET /books/{book_id}/reviews/{review_id}/details`: Retrieve details of a review.
    - `POST /books/{book_id}/reviews/{review_id}/details`: Add details to a review.
    - `PUT /books/{book_id}/reviews/{review_id}/details`: Update details of a review.
    - `DELETE /books/{book_id}/reviews/{review_id}/details`: Delete details of a review.

5. **Search Endpoints**:
    - `GET /search/books`: Search books by name, description, author, category, or publisher.
    - `GET /search/authors`: Search authors by name or awards.
    - `GET /search/categories`: Search categories by name or description.
    - `GET /search/reviews`: Search reviews by content, rating, or user.
    - `GET /search/users`: Search users by name, email, or phone number.

### Example Search Endpoint Responses:

1. **Search Books**:
```json
{
    "results": [
        {
            "id": "6683f946ec61bfa6a3c2d7c7",
            "name": "Harry Porter Chambers of secrets (VOLUME 1)",
            "author": {
                "id": "6683e1a4710824df4e5d76e9",
                "name": "James"
            },
            "category": {
                "id": "6683e1a4710824df4e5d76e9",
                "name": "Fiction"
            },
            "publisher": {
                "id": "6683e1a4710824df4e5d76e9",
                "name": "Penguin Random House"
            },
            "average_rating": 4.5,
            "total_reviews": 150
        }
    ]
}
```

2. **Search Authors**:
```json
{
    "results": [
        {
            "id": "6682cdeed4646ca7d4f37874",
            "name": "James",
            "age": 25,
            "gender": "Male",
            "awards": [
                "Best writer of the decade - 2018 "
            ],
            "latest_books": [
                {
                    "id": "6683f946ec61bfa6a3c2d7c7",
                    "name": "Harry Porter Chambers of secrets (VOLUME 1)"
                }
            ],
            "total_published": 4,
            "

average_rating": 4.5
        }
    ]
}
```

3. **Search Categories**:
```json
{
    "results": [
        {
            "id": "6683e1a4710824df4e5d76e9",
            "name": "Fiction",
            "description": "Fiction description"
        }
    ]
}
```

4. **Search Reviews**:
```json
{
    "results": [
        {
            "id": "6683fbafb25f017d052716af",
            "content": "This is the content",
            "rating": 4,
            "created_by": {
                "id": "6683abe1455818257eb1d668",
                "name": "Albert Joseph"
            },
            "book_id": {
                "id": "6683f946ec61bfa6a3c2d7c7",
                "name": "Harry Porter Chambers of secrets (VOLUME 1)"
            },
            "review_details": {
                "likes": 120,
                "comments": [
                    {
                        "id": "6683e1a4710824df4e5d76e9",
                        "user": "John Doe",
                        "content": "Great review!"
                    }
                ]
            }
        }
    ]
}
```

5. **Search Users**:
```json
{
    "results": [
        {
            "id": "6683abe1455818257eb1d668",
            "name": "Albert Joseph",
            "email": "test@gmail.com",
            "gender": "Male",
            "phone_number": "+918856852123",
            "age": 25,
            "favorite_books": [
                {
                    "id": "6683f946ec61bfa6a3c2d7c7",
                    "name": "Harry Porter Chambers of secrets (VOLUME 1)"
                }
            ],
            "total_reviews": 10,
            "average_rating": 4.2
        }
    ]
}
```

### Summary:

1. **Define New Models**:
    - Create `Publisher` and `Bookstore` models.
    - Update existing models to reflect new relationships.

2. **Create Endpoints for New Models**:
    - Implement CRUD endpoints for `Publisher` and `Bookstore`.
    - Implement endpoints for managing books in a bookstore.

3. **Update Existing Endpoints**:
    - Update the `User`, `Book`, and `Review` models and their respective endpoints to include new fields and relationships.

4. **Add Search Functionality**:
    - Implement search endpoints for `Book`, `Author`, `Category`, `Review`, and `User`.

5. **Test All Endpoints**:
    - Ensure all new and updated endpoints work as expected.
    - Write tests for each endpoint to validate functionality.

By following this plan, you can significantly enhance the functionality of your API with more complex relationships and search capabilities. Let me know if you need detailed implementation code for any of the new endpoints or models!