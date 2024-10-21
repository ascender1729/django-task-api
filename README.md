# Django Task API

## Overview

Django Task API is a simple RESTful API for managing tasks. It's built with Django and Django REST Framework, providing basic CRUD operations for tasks.

Repository: [https://github.com/ascender1729/django-task-api](https://github.com/ascender1729/django-task-api)

## Features

- Create, Read, Update, and Delete tasks
- RESTful API design
- Built with Django and Django REST Framework

## Project Workflow

The following diagram illustrates the workflow of the Django Task API:

![Django Task API Workflow](/workspaces/django-task-api/IMG.png)

### Workflow Explanation

1. **Client Interaction**: The process starts with a client (e.g., web browser, mobile app) sending an HTTP request to the Django web server.

2. **Django Web Server**: Receives the request and routes it based on the URL patterns.

3. **URL Routing**: The request is directed to the appropriate view (TaskViewSet) based on the URL pattern (/api/tasks/).

4. **TaskViewSet**: This is the main view handling CRUD operations for tasks. It interacts with the database to query or update task data and uses the TaskSerializer to convert data between Python objects and JSON.

5. **Database**: Stores all the task data and is interacted with via Django's ORM.

6. **TaskSerializer**: Handles the conversion of task data between Python objects and JSON format.

7. **Response**: The serialized data is sent back to the client as an HTTP response.

8. **Django Admin Interface**: Allows admin users to manage tasks directly through a web interface.

9. **Django ORM**: Used by developers to interact with the database using Python code.

10. **Authentication**: Shown as a future feature that could be integrated into the workflow.

## Requirements

- Python 3.8+
- Django 5.0.1
- Django REST Framework 3.14.0

## Setup

1. Clone the repository:
   ```
   git clone https://github.com/ascender1729/django-task-api.git
   cd django-task-api
   ```

2. Create a virtual environment and activate it:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

4. Run migrations:
   ```
   python manage.py migrate
   ```

5. Create a superuser (for admin access):
   ```
   python manage.py createsuperuser
   ```

6. Run the development server:
   ```
   python manage.py runserver
   ```

The API will be available at `http://localhost:8000/api/`.

## API Endpoints

- Task List: `GET /api/tasks/`
- Create Task: `POST /api/tasks/`
- Retrieve Task: `GET /api/tasks/{id}/`
- Update Task: `PUT /api/tasks/{id}/`
- Partial Update Task: `PATCH /api/tasks/{id}/`
- Delete Task: `DELETE /api/tasks/{id}/`

## Models

### Task

- `title`: CharField (max length: 200 characters)
- `description`: TextField (optional)
- `completed`: BooleanField (default: False)
- `created_at`: DateTimeField (auto-added)

## Usage

You can interact with the API using tools like curl, Postman, or the built-in Django REST Framework browsable API.

Example API calls:

1. List all tasks:
   ```
   curl -X GET http://localhost:8000/api/tasks/
   ```

2. Create a new task:
   ```
   curl -X POST http://localhost:8000/api/tasks/ -H "Content-Type: application/json" -d '{"title":"New Task", "description":"Task description"}'
   ```

3. Retrieve a specific task (replace {id} with the actual task ID):
   ```
   curl -X GET http://localhost:8000/api/tasks/{id}/
   ```

4. Update a task:
   ```
   curl -X PUT http://localhost:8000/api/tasks/{id}/ -H "Content-Type: application/json" -d '{"title":"Updated Task", "description":"Updated description", "completed":true}'
   ```

5. Delete a task:
   ```
   curl -X DELETE http://localhost:8000/api/tasks/{id}/
   ```

## Admin Interface

You can access the Django admin interface at `http://localhost:8000/admin/`. Use the superuser credentials you created during setup to log in.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open-source and available under the MIT License.