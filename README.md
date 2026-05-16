# Task API

A simple RESTful API for managing tasks, built with Laravel and SQLite.

## Features

- Full CRUD for tasks (create, read, update, delete)
- Mark tasks as complete/incomplete
- Filter tasks by status (completed/pending)
- Search tasks by title
- Input validation and error handling

## Tech Stack

- PHP 8.2
- Laravel 12
- SQLite

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks` | Get all tasks |
| GET | `/api/tasks?status=completed` | Get completed tasks |
| GET | `/api/tasks?status=pending` | Get pending tasks |
| GET | `/api/tasks?search=keyword` | Search tasks by title |
| GET | `/api/tasks/{id}` | Get a single task |
| POST | `/api/tasks` | Create a new task |
| PUT | `/api/tasks/{id}` | Update a task |
| DELETE | `/api/tasks/{id}` | Delete a task |
| PATCH | `/api/tasks/{id}/toggle` | Toggle complete/incomplete |

## Setup

```bash
git clone https://github.com/VOLTIA1/task-api.git
cd task-api
composer install
cp .env.example .env
php artisan key:generate
touch database/database.sqlite
php artisan migrate
php artisan serve
```

## Usage Examples

```bash
# Create a task
curl -X POST http://localhost:8000/api/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Buy groceries", "description": "Milk, eggs, bread"}'

# Get all tasks
curl http://localhost:8000/api/tasks

# Get only completed tasks
curl http://localhost:8000/api/tasks?status=completed

# Search tasks
curl http://localhost:8000/api/tasks?search=groceries

# Toggle task complete/incomplete
curl -X PATCH http://localhost:8000/api/tasks/1/toggle

# Delete a task
curl -X DELETE http://localhost:8000/api/tasks/1
```

## Example Response

```json
{
  "id": 1,
  "title": "Buy groceries",
  "description": "Milk, eggs, bread",
  "is_completed": false,
  "created_at": "2026-05-17T12:00:00.000000Z",
  "updated_at": "2026-05-17T12:00:00.000000Z"
}
```
