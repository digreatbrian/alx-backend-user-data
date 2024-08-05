Here is the raw README text:

```
# Simple API

A simple HTTP API for interacting with the `User` model.

## Table of Contents

- [Files](#files)
- [Setup](#setup)
- [Run](#run)
- [Routes](#routes)

## Files

### `models/`

- **`base.py`**: Base class for all models in the API, handling serialization to file.
- **`user.py`**: Contains the `User` model.

### `api/v1`

- **`app.py`**: Entry point of the API.
- **`views/index.py`**: Basic endpoints of the API: `/status` and `/stats`.
- **`views/users.py`**: All user-related endpoints.

## Setup

1. Clone the repository:
   ```sh
   git clone <repository_url>
   cd <repository_directory>
   ```

2. Install the required dependencies:
   ```sh
   pip3 install -r requirements.txt
   ```

## Run

Start the API server by running the following command:
```sh
API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
```
This will start the API on `http://0.0.0.0:5000`.

## Routes

### Status and Stats

- **`GET /api/v1/status`**: Returns the status of the API.
  - Example response:
    ```json
    {
      "status": "OK"
    }
    ```

- **`GET /api/v1/stats`**: Returns some statistics of the API.
  - Example response:
    ```json
    {
      "user_count": 42,
      "other_stat": 123
    }
    ```

### User Endpoints

- **`GET /api/v1/users`**: Returns the list of users.
  - Example response:
    ```json
    [
      {
        "id": 1,
        "email": "user@example.com",
        "first_name": "John",
        "last_name": "Doe"
      },
      ...
    ]
    ```

- **`GET /api/v1/users/:id`**: Returns a user based on the ID.
  - Example response:
    ```json
    {
      "id": 1,
      "email": "user@example.com",
      "first_name": "John",
      "last_name": "Doe"
    }
    ```

- **`DELETE /api/v1/users/:id`**: Deletes a user based on the ID.
  - Example response:
    ```json
    {
      "result": "User deleted"
    }
    ```

- **`POST /api/v1/users`**: Creates a new user.
  - JSON parameters: `email`, `password`, `last_name` (optional), and `first_name` (optional).
  - Example request:
    ```json
    {
      "email": "newuser@example.com",
      "password": "password123",
      "first_name": "Jane",
      "last_name": "Smith"
    }
    ```
  - Example response:
    ```json
    {
      "id": 2,
      "email": "newuser@example.com",
      "first_name": "Jane",
      "last_name": "Smith"
    }
    ```

- **`PUT /api/v1/users/:id`**: Updates a user based on the ID.
  - JSON parameters: `last_name` and `first_name`.
  - Example request:
    ```json
    {
      "first_name": "Jane",
      "last_name": "Doe"
    }
    ```
  - Example response:
    ```json
    {
      "id": 1,
      "email": "user@example.com",
      "first_name": "Jane",
      "last_name": "Doe"
    }
    ```

---

