# LAB6 – Node.js HTTP Server and Routing

This project was developed for the course **Tecnologías y Sistemas Web** and corresponds to **Laboratory 6**.

The objective of this laboratory was to build and debug a basic HTTP server using Node.js, understand how routing works at a low level, and implement dynamic responses using JSON and file handling.

---

## Project Description

This application consists of a simple HTTP server built using Node.js native modules.

The server allows users to:

- Access different routes through the browser
- Receive responses in both plain text and JSON format
- Retrieve data from a local JSON file
- Understand how HTTP requests and responses are handled manually

The project focuses on debugging, fixing errors, and extending functionality from an initial broken implementation.

---

## Part 1 – Debugging and Fixing the Server

The provided file (`servidor-malo.js`) contained multiple issues that prevented it from working correctly.

The following problems were identified and fixed:

- Incorrect Content-Type (`application-json` → `application/json`)
- Missing `await` when reading files with `fs.promises`
- Incorrect use of `res.writeHead()` as if it returned data
- Missing `JSON.parse()` when handling JSON files
- Improper closing of `createServer()` function
- Incorrect HTTP status code for unknown routes (200 → 404)
- Server crash when `datos.json` was not found

After fixing these issues, the server was successfully executed and tested.

---

## Part 2 – Server Enhancements

Once the base server was functional, the following features were implemented:

### Updated Route `/info`

- Now returns a JSON response instead of plain text
- Includes:
  - mensaje
  - curso
  - tecnologia

---

### New Route `/saludo`

- Returns a plain text message
- Used to demonstrate simple routing

---

### New Route `/api/status`

- Returns a JSON response with:
  - ok
  - status
  - puerto

---

### Improved 404 Handling

- Now displays the route that was not found

Example:

Ruta no encontrada: /example

---

## Available Routes

| Route | Method | Description |
|------|--------|------------|
| `/` | GET | Returns "Servidor activo" |
| `/info` | GET | Returns server information in JSON |
| `/saludo` | GET | Returns a greeting message |
| `/api/status` | GET | Returns server status in JSON |
| `/api/student` | GET | Returns data from `datos.json` |
| Any other | GET | Returns 404 with route message |

---

## File Handling

The server reads data from a local file:

- `datos.json`

Example content:

```json
{
  "nombre": "Miguel",
  "curso": "Sistemas y Tecnologías Web",
  "carnet": "12345"
}
```

---

## How to Run Locally

1. Clone the repository:
git clone <repo-url>
2. Navigate to the project folder:
cd Lab6
3. Make sure you have Node.js installed:
node -v
4. Run the server:
node servidor-malo.js
5. Open your browser and test:
http://localhost:3000



---

## Testing the Server

The following routes were tested:

- `/`
- `/info`
- `/saludo`
- `/api/status`
- `/api/student`
- Invalid routes (e.g. `/test`, `/hola`)

All routes returned the expected responses.

---

## Technologies Used

- Node.js  
- HTTP Module  
- File System (fs/promises)  
- Path Module  

---

## Author

- Student: Miguel Rosas – 241274  
- Course: Tecnologías y Sistemas Web  
- Year: 2026  
