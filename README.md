# Books Demo API

A simple FastAPI-based REST API for managing a collection of books. This demo application provides basic CRUD operations for book management with endpoints to create, read, update, and delete books.

## Features

- **GET** `/` - Welcome endpoint
- **GET** `/books` - Retrieve all books
- **GET** `/books/{book_title}` - Get a specific book by title
- **GET** `/books/?category={category}` - Filter books by category
- **POST** `/books/create_book` - Add a new book
- **PUT** `/books/update_book` - Update an existing book
- **DELETE** `/books/delete_book/{book_title}` - Delete a book by title

## Book Schema

Each book in the system has the following structure:

```json
{
  "title": "Book Title",
  "author": "Author Name",
  "category": "science|history|math|etc"
}
```

## Prerequisites

- Python 3.7+
- pip (Python package installer)

## Installation

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd books-demo
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Running the Application

Start the FastAPI server:

```bash
fastapi dev main.py
```

The API will be available at `http://localhost:8000`

## API Documentation

Once the server is running, you can access:

- **Interactive API docs (Swagger UI)**: `http://localhost:8000/docs`
- **Alternative API docs (ReDoc)**: `http://localhost:8000/redoc`

## API Endpoints

### Get All Books

```http
GET /books
```

**Response:**

```json
[
  {
    "title": "Title One",
    "author": "Author One",
    "category": "science"
  },
  {
    "title": "Title Two",
    "author": "Author Two",
    "category": "science"
  }
]
```

### Get Book by Title

```http
GET /books/{book_title}
```

**Example:**

```http
GET /books/Title One
```

### Filter Books by Category

```http
GET /books/?category=science
```

### Create New Book

```http
POST /books/create_book
Content-Type: application/json

{
  "title": "New Book",
  "author": "New Author",
  "category": "fiction"
}
```

### Update Book

```http
PUT /books/update_book
Content-Type: application/json

{
  "title": "Updated Title",
  "author": "Updated Author",
  "category": "updated_category"
}
```

### Delete Book

```http
DELETE /books/delete_book/{book_title}
```

**Example:**

```http
DELETE /books/delete_book/Title One
```

## Sample Data

The application comes pre-loaded with sample books:

- Title One (Author One) - science
- Title Two (Author Two) - science
- Title Three (Author Three) - history
- Title Four (Author Four) - math
- Title Five (Author Five) - math
- Title Six (Author Two) - math

## Testing the API

You can test the API using:

1. **Swagger UI** at `http://localhost:8000/docs`
2. **curl** commands:

   ```bash
   # Get all books
   curl http://localhost:8000/books

   # Get specific book
   curl http://localhost:8000/books/Title%20One

   # Filter by category
   curl http://localhost:8000/books/?category=science

   # Create new book
   curl -X POST http://localhost:8000/books/create_book \
     -H "Content-Type: application/json" \
     -d '{"title": "Test Book", "author": "Test Author", "category": "test"}'
   ```

## Project Structure

```
books-demo/
├── main.py           # FastAPI application with all endpoints
├── requirements.txt  # Python dependencies
└── README.md        # This documentation
```

## Dependencies

- **FastAPI** - Modern, fast web framework for building APIs
- **Uvicorn** - ASGI server for running FastAPI applications
- **Pydantic** - Data validation and settings management

## Development

This is a demo application designed to showcase basic FastAPI functionality. For production use, consider adding:

- Database persistence (SQLAlchemy, MongoDB, etc.)
- Authentication and authorization
- Input validation and error handling
- Logging and monitoring
- Unit tests
- Docker containerization

## License

This project is for demonstration purposes.
