# School Management API with Location-Based Search

A Node.js + Express + MySQL project to manage schools with location support.

This project provides:

- Add School API
- List Schools API sorted by nearest location
- Frontend pages with interactive maps
- Auto user geolocation
- MySQL database integration
- Environment variable support with `.env`

---

## Features

### Add School
- Add school name
- Add school address
- Search location on map
- Click map to auto-fill latitude & longitude
- Store school in MySQL database

### List Schools
- Auto detect user current location
- Manual location selection using map
- Fetch all schools
- Sort schools by nearest distance using Haversine formula

---

## Tech Stack

- Node.js
- Express.js
- MySQL
- HTML
- CSS
- JavaScript
- Leaflet.js
- OpenStreetMap
- dotenv

---

## Project Structure

```bash
school-project/
│── server.js
│── db.js
│── package.json
│── .env
│── .gitignore
│
└── public/
    │── addSchool.html
    │── listSchools.html
    │── style.css
```

---

## Installation

Clone repository:

```bash
git clone <your-repo-url>
cd school-project
```

Install dependencies:

```bash
npm install
```

---

## Environment Variables

Create `.env`

```env
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=schooldb
PORT=3000
```

For Railway MySQL:

```env
DB_HOST=your-proxy.rlwy.net
DB_PORT=your_port
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=railway
PORT=3000
```

---

## Database Setup

Create database:

```sql
CREATE DATABASE schooldb;
USE schooldb;
```

Create table:

```sql
CREATE TABLE schools (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  address TEXT NOT NULL,
  latitude DECIMAL(10,8) NOT NULL,
  longitude DECIMAL(11,8) NOT NULL
);
```

---

## Run Project

Start server:

```bash
npm start
```

Server runs on:

```bash
http://localhost:3000
```

---

## API Endpoints

---

### Add School API

**Endpoint**

```http
POST /addSchool
```

**Payload**

```json
{
  "name": "ABC School",
  "address": "Delhi",
  "latitude": 28.6139,
  "longitude": 77.2090
}
```

**Response**

```json
{
  "message": "School added successfully",
  "schoolId": 1
}
```

---

### List Schools API

**Endpoint**

```http
GET /listSchools?latitude=28.6139&longitude=77.2090
```

**Response**

```json
[
  {
    "id": 1,
    "name": "ABC School",
    "address": "Delhi",
    "latitude": "28.61390000",
    "longitude": "77.20900000",
    "distance": 1.24
  }
]
```

---

## Frontend Pages

### Add School Page

Open:

```bash
http://localhost:3000/addSchool.html
```

Features:
- Search location
- Click map to select location
- Add school to database

---

### List Schools Page

Open:

```bash
http://localhost:3000/listSchools.html
```

Features:
- Auto locate user
- Manual location selection
- View nearest schools

---

## Distance Calculation

Distance between user and schools is calculated using:

- Haversine Formula

This ensures accurate geographic sorting.

---

## Deployment

Can be deployed on:

- Railway
- Render
- VPS
- Localhost

---

## Author

Ankit Prasad

---

## License

MIT License
