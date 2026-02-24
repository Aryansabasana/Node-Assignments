https://documenter.getpostman.com/view/50839265/2sBXcGDKLt



GET
Count Students
http://localhost:3000/students/count
GET /students/count
Returns the total number of students currently stored in the system.

Request
Method: GET
URL: http://localhost:3000/students/count
Auth: None
Request body: None
Successful response
Status: 200 OK
Content-Type: application/json
Body: JSON object containing the total count.
Response fields
Field	Type	Description
totalStudents	number	Total number of student records.
Example response (200)
json
{
  "totalStudents": 10
}
Status codes
200 OK — Count returned successfully.
4xx — Client error (e.g., invalid route or request not allowed by server configuration).
5xx — Server error while calculating or retrieving the count.
Example Request
Count Students
curl
curl --location 'http://localhost:3000/students/count'
200 OK
Example Response
Body
Headers (7)
{
  "totalStudents": 10
}
GET
Student by ID
http://localhost:3000/students/:id
Purpose
Retrieve a single student record by its unique identifier.

Base URL
This request targets a local server:

http://localhost:3000
Path variable
id (required): Student identifier.
Example: 4
Example request
http
GET http://localhost:3000/students/4
Expected responses
200 OK
Returns a student object.

Example shape:

json
{
  "id": 4,
  "name": "...",
  "...": "..."
}
404 Not Found
Returned when no student exists for the provided id.

Tests (suggested)
Assert status code is 200 for valid IDs.
Validate response body is JSON and contains an id matching the requested id.
Optionally assert required fields (e.g., name) are present and non-empty.
For invalid/non-existent IDs, assert status code is 404.
PATH VARIABLES
id
4

Example Request
Student by ID
curl
curl --location 'http://localhost:3000/students/4'
200 OK
Example Response
Body
Headers (7)
{
  "id": 4,
  "name": "Meera Iyer",
  "branch": "CSE",
  "semester": 8,
  "cgpa": 9.1
}
GET
Student By Branch
http://localhost:3000/students/branch/:branchName
Get students by branch
Returns a list of students filtered by a specific branch.

What it does
Performs a GET request to fetch students that belong to the branch provided in the path.
Intended for use with the local API running on http://localhost:3000.
Endpoint
GET http://localhost:3000/students/branch/:branchName

Path variables
Variable	Type	Required	Description	Example
branchName	string	yes	Branch identifier/name to filter students by.	cse
Example usage
Request

http
GET http://localhost:3000/students/branch/cse
Postman variable form

text
GET http://localhost:3000/students/branch/{{branchName}}
Successful response
Status: 200 OK

Schema (example)

json
[
  {
    "id": "<string|number>",
    "name": "<string>",
    "branch": "<string>",
    "semester": "<number>",
    "email": "<string>"
  }
]
Notes:


The exact fields depend on your server implementation. The response is expected to be an array of student objects.

Possible error responses
400 Bad Request — branchName is missing/invalid.
404 Not Found — No students found for the given branch (or the route is not implemented).
500 Internal Server Error — Unexpected server error.
Error body (typical shape)

json
{
  "message": "<string>",
  "error": "<string|object>"
}
Local development notes (localhost:3000)
Ensure your API server is running and listening on port 3000.
If you see connection errors (e.g., ECONNREFUSED), start the server and confirm the base URL is correct.
If your server uses a different port, update the request base URL accordingly.
PATH VARIABLES
branchName
cse
