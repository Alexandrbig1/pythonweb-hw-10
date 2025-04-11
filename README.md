# pythonweb-hw-10

## Project Overview

This project is a **REST API for managing contacts**, built using the **FastAPI** framework. It provides functionality to store and manage contact information, including CRUD operations (Create, Read, Update, Delete). The API uses **SQLAlchemy** as the ORM for database interactions and **PostgreSQL** as the database.

The project now includes **user authentication and authorization** using **JWT tokens**, **email verification**, **rate limiting**, and **user avatar management** with **Cloudinary**.

---

## Features

- **FastAPI Framework**: A modern, fast (high-performance) web framework for building APIs.
- **SQLAlchemy ORM**: Used for database modeling and interaction.
- **PostgreSQL Database**: A robust and reliable relational database.
- **JWT Authentication**: Secure user authentication and authorization using access tokens.
- **Email Verification**: Users must verify their email addresses to activate their accounts.
- **Rate Limiting**: Limits the number of requests to sensitive routes (e.g., `/me`).
- **User-Specific Operations**: Users can only access and modify their own contacts.
- **CORS Support**: Enabled for secure cross-origin requests.
- **Cloudinary Integration**: Allows users to upload and update their avatars.
- **Swagger Documentation**: Automatically generated API documentation available at `/docs`.
- **Pydantic Validation**: Ensures data integrity and validation for all API inputs.

---

## Requirements

- **Python**: 3.10 or higher
- **PostgreSQL**: Version 14 or higher
- **Docker Compose**: For running the application and its dependencies.
- **Dependencies**: Listed in `requirements.txt`

---

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/Alexandrbig1/pythonweb-hw-10.git
   cd pythonweb-hw-10
   ```
2. **Set Up a Virtual Environment**:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
4. **Set Up the Database**:

- Ensure PostgreSQL is installed and running.
- Create a database named `contacts_db`:

```bash
CREATE DATABASE contacts_db;
```

- Update the `.env` file with your database credentials:

```properties
POSTGRES_DB=contacts_db
POSTGRES_USER=example_user
POSTGRES_PASSWORD=your_password
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
```

5. **Run Alembic Migrations**:
   ```bash
   alembic upgrade head
   ```
6. **Start the Application**:

   ```bash
   uvicorn main:app --reload
   ```

7. **Run with Docker Compose** (Optional):
   If you prefer to use Docker Compose, ensure `docker` and `docker-compose` are installed, then run:
   ```bash
   docker-compose up --build
   ```

---

## API Endpoints

### Base URL

```bash
http://localhost:8000
```

### Endpoints

| Method | Endpoint         | Description                           |
| ------ | ---------------- | ------------------------------------- |
| POST   | `/auth/register` | Register a new user                   |
| POST   | `/auth/login`    | Log in and retrieve a JWT token       |
| GET    | `/auth/verify`   | Verify a user's email address         |
| GET    | `/contacts`      | Retrieve all contacts (user-specific) |
| GET    | `/contacts/{id}` | Retrieve a contact by ID              |
| POST   | `/contacts`      | Create a new contact                  |
| PUT    | `/contacts/{id}` | Update a contact by ID                |
| DELETE | `/contacts/{id}` | Delete a contact by ID                |
| GET    | `/me`            | Retrieve the current user's profile   |
| PUT    | `/me/avatar`     | Update the user's avatar              |

### Swagger Documentation

Access the Swagger UI for API documentation at:

```bash
http://localhost:8000/docs
```

---

## Project Structure

```markdown
pythonweb-hw-10/
├── migrations/ # Alembic migrations
├── src/
│ ├── conf/ # Configuration files
│ ├── database/ # Database session management
│ ├── entity/ # SQLAlchemy models
│ ├── repository/ # Database query logic
│ ├── routes/ # API routes
│ ├── schemas/ # Pydantic schemas
│ ├── services/ # Business logic and service layer
├── main.py # Application entry point
├── .env # Environment variables
├── requirements.txt # Python dependencies
└── README.md # Project documentation
```

---

## Technologies Used

- **FastAPI**: Web framework for building APIs.
- **SQLAlchemy**: ORM for database modeling and interaction.
- **PostgreSQL**: Relational database.
- **Pydantic**: Data validation and settings management.
- **Alembic**: Database migrations.
- **Uvicorn**: ASGI server for running the application.
- **JWT**: Secure user authentication and authorization.
- **Cloudinary**: For managing user avatars.
- **Docker Compose**: For containerized deployment.

---

## Future Improvements

- Add advanced search and filtering capabilities for contacts.
- Implement pagination for retrieving large contact lists.
- Deploy the application to a cloud platform (e.g., AWS, Heroku).
- Add support for social login (e.g., Google, Facebook).
- Improve rate-limiting policies for better security.

---

## Homework 10 Features

### Authentication and Authorization

- Implemented user authentication using hashed passwords and JWT tokens.
- Users can only access their own contacts.

### Email Verification

- Added email verification for new user registrations.

### Rate Limiting

- Limited the number of requests to the `/me` route.

### CORS Support

- Enabled CORS for secure cross-origin requests.

### Avatar Management

- Integrated Cloudinary for uploading and updating user avatars.

---

## Environment Variables

All sensitive data is stored in the `.env` file. Example:

```properties
POSTGRES_DB=contacts_db
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your_password
POSTGRES_HOST=localhost
POSTGRES_PORT=5432

ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=7
ALGORITHM=HS256
SECRET_KEY=your_secret_key
REDIS_URL=redis://localhost

MAIL_USERNAME=your_email@example.com
MAIL_PASSWORD=your_password
MAIL_FROM=your_email@example.com
MAIL_PORT=465

CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

---
