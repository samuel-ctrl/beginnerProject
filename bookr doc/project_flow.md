## Bookr Project Guide for Beginners

### Introduction
- **Overview**: Brief description of the Bookr project.
- **Technologies**: FastAPI, PostgreSQL, SQLAlchemy.
- **Purpose**: Learn how to build a web application with modern technologies.

### Prerequisites
- Basic knowledge of Python.
- Familiarity with SQL.
- Basic understanding of REST APIs.

### Setup

1. **Install Required Tools**
   - Install Python 3.8+.
   - Install PostgreSQL.
   - Install an IDE (like VSCode).

2. **Create and Activate Virtual Environment**

   - **Windows:**
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

   - **macOS/Linux:**
     ```bash
     python -m venv venv
     source venv/bin/activate
     ```

3. **Install Dependencies**

   With the virtual environment activated, install the required packages using pip:

   ```bash
   pip install fastapi uvicorn sqlalchemy psycopg2-binary
   ```

### Project Structure

1. **Create Project Directory**
   ```bash
   mkdir bookr_project
   cd bookr_project
   ```

2. **Set Up Directory Structure**
   please refer to the [Structure Guide](project_structure.md).

### Database Setup

1. **Create PostgreSQL Database**
   ```bash
   createdb bookr_db
   ```

2. **Configure Database Connection**
   In `app/database.py`:
   ```python
   from sqlalchemy import create_engine
   from sqlalchemy.ext.declarative import declarative_base
   from sqlalchemy.orm import sessionmaker

   SQLALCHEMY_DATABASE_URL = "postgresql://user:password@localhost/bookr_db"
   engine = create_engine(SQLALCHEMY_DATABASE_URL)
   SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)
   Base = declarative_base()
   ```

### Defining Models

1. **Create Models**
   In `app/models.py`:
   ```python
   from sqlalchemy import Column, Integer, String
   from .database import Base

   class Book(Base):
       __tablename__ = "books"

       id = Column(Integer, primary_key=True, index=True)
       title = Column(String, index=True)
       author = Column(String)
   ```

2. **Create Tables**
   ```python
   from app.database import Base, engine
   from app.models import Book

   Base.metadata.create_all(bind=engine)
   ```

### Creating CRUD Operations

1. **Define CRUD Functions**
   In `app/crud.py`:
   ```python
   from sqlalchemy.orm import Session
   from . import models, schemas

   def get_book(db: Session, book_id: int):
       return db.query(models.Book).filter(models.Book.id == book_id).first()

   def create_book(db: Session, book: schemas.BookCreate):
       db_book = models.Book(**book.dict())
       db.add(db_book)
       db.commit()
       db.refresh(db_book)
       return db_book
   ```

### Creating API Endpoints

1. **Define Schemas**
   In `app/schemas.py`:
   ```python
   from pydantic import BaseModel

   class BookBase(BaseModel):
       title: str
       author: str

   class BookCreate(BookBase):
       pass

   class Book(BookBase):
       id: int

       class Config:
           orm_mode = True
   ```

2. **Create FastAPI Endpoints**
   In `app/main.py`:
   ```python
   from fastapi import FastAPI, Depends
   from sqlalchemy.orm import Session
   from . import crud, models, schemas
   from .database import SessionLocal, engine

   app = FastAPI()

   models.Base.metadata.create_all(bind=engine)

   def get_db():
       db = SessionLocal()
       try:
           yield db
       finally:
           db.close()

   @app.post("/books/", response_model=schemas.Book)
   def create_book(book: schemas.BookCreate, db: Session = Depends(get_db)):
       return crud.create_book(db=db, book=book)

   @app.get("/books/{book_id}", response_model=schemas.Book)
   def read_book(book_id: int, db: Session = Depends(get_db)):
       db_book = crud.get_book(db=db, book_id=book_id)
       if db_book is None:
           raise HTTPException(status_code=404, detail="Book not found")
       return db_book
   ```

### Running the Application

1. **Start the Server**
   ```bash
   uvicorn app.main:app --reload
   ```

2. **Testing the API**
   - Open `http://127.0.0.1:8000/docs` in your browser to access the interactive API documentation.

### Conclusion
- Recap of what was covered.
- Encourage experimentation and further learning.