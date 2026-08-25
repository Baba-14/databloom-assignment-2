# Assignment API

A simple FastAPI application for creating, viewing, and deleting assignments. Data is stored temporarily in a Python list and is lost when the server restarts.

Features

* Create assignments
* View all assignments
* View an assignment by ID
* Delete assignments
* Validate input data
* Return `404` for missing assignments
* Return `422` for invalid input

## Technologies

* Python
* FastAPI
* Pydantic
* Uvicorn

## Project Structure

```text
assignment-api/
├── main.py
├── requirements.txt
└── README.md
```

## Installation

```bash
git clone YOUR_GITHUB_REPOSITORY_LINK
cd assignment-api
python -m venv venv
```

Activate the virtual environment:

**Windows**

```bash
venv\Scripts\activate
```

**macOS/Linux**

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Run the API

```bash
uvicorn main:app --reload
```

API: `http://127.0.0.1:8000`
Swagger documentation: `http://127.0.0.1:8000/docs`

## Endpoints

| Method | Endpoint                       | Purpose              |
| ------ | ------------------------------ | -------------------- |
| POST   | `/assignments`                 | Create an assignment |
| GET    | `/assignments`                 | View all assignments |
| GET    | `/assignments/{assignment_id}` | View one assignment  |
| DELETE | `/assignments/{assignment_id}` | Delete an assignment |

## Example Assignment

```json
{
  "title": "Complete FastAPI exercise",
  "due_date": "2026-08-30",
  "done": false
}
```

A successful `POST` request returns `201 Created` and automatically generates the assignment ID.

## Validation

The `title` must be between **3 and 100 characters**. Invalid data returns:

```text
422 Unprocessable Entity
```

If an assignment does not exist, the API returns:

```json
{
  "detail": "Assignment not found"
}
```

with status:

```text
404 Not Found
```

## Storage

Assignments are stored **in memory**, so all data is deleted when the server stops or restarts.

## Testing

Use `/docs` to test:

1. `POST /assignments`
2. `GET /assignments`
3. `GET /assignments/1`
4. `DELETE /assignments/1`
5. Invalid titles for `422`
6. Missing IDs for `404`

## Author

**Yusif Issah Babamu**
