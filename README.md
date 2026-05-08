# Hackathon Prometeo 2026 – Registration System

A full-stack web application built for managing registrations for Hackathon Prometeo 2026.
The system allows users to register through a public form and provides an admin panel protected by an authorization token to retrieve all submissions.

## 📌 Features
### Frontend
* Public registration form with validation
* Responsive UI
* Error handling and success messages
* Admin dashboard for viewing registrations
* Admin authentication using a secure token
* Deployed on **Vercel**

### Backend
* REST API built with **Flask**
* Database **CRUD** operations using **MySQL** (Railway Managed)
* CORS enabled
* Email validation using **regex**
* Protected admin endpoint using server-side token
* Deployed on **Railway**

---

## 📁 Project Structure

### Frontend
```
/
  ├─ public/
  ├─ src/
  |  ├─ pages/
  |  |  └─ LandingPage.jsx
  |  └─ ... (App.jsx, main.jsx, assets, etc.)
  ├─ index.html
  └─ package.json
```

### Backend
 ```
/backend
  ├─ app.py
  └─ requirements.txt
```

---

## 🔧 Technologies Used

### Frontend
* **React**
* **HTML5**
* **CSS3**
* **JavaScript**

### Backend
* **Python 3**
* **Flask**
* **PyMySQL**
* **Regex**
* **Railway Hosting**

### Database
* **MySQL** (Railway Managed)

---

## 🔑 Environment Variables

The backend requires the following environment variables (configured on Railway):

| Variable | Description |
| :--- | :--- |
| `DATABASE_URL` | MySQL connection provided by Railway |
| `AUTH_TOKEN` | Secret admin token for accessing `/api/registrations` |
| `PORT` | 5000

> **Example (Do not commit into code):**
>
> ```bash
> DATABASE_URL = mysql://user:password@host:port/database
> AUTH_TOKEN = secret-token
> PORT = 5000
> ```
>
> ---

## 📡 API Endpoints

### `POST /api/register`
Registers a new participant.

**Request Body (JSON)**
```json
{
  "name": "John Doe",
  "email": "john@mail.com",
  "message": "Looking forward to it!"
}
```

**Responses**
| Status | Description |
| :--- | :--- |
| 200 | Registration successful |
| 400 | Missing or invalid fields |
| 409 | Email already registered |
| 500 | Database or server error |

### `GET /api/registrations?key=AUTH_TOKEN`
Returns all registrations.

> This endpoint is protected and only accessible with the correct token.

**Response Example**
```json
{
  "hackathondb": [
    {
      "name": "Jane Doe",
      "email": "jane@mail.com",
      "message": "Excited!",
      "created_at": "2025-11-10 21:47:15"
    }
  ]
}
```
## 🗄 Database Schema

```sql
CREATE TABLE hackathondb (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    message TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🌐 Deployments

### Frontend
* **Vercel**

### Backend
* **Railway**

---

## ✔️ Admin Panel

After deployment, access the admin dashboard via:

https://hackathon-prometeo-delta.vercel.app/admin/admin-panel.html

Enter secret **Admin Token** to view the registrations.

---

## 🛡 Security Notes

* API keys and DB credentials are never stored on the frontend.
* Admin token is stored on the backend and compared on every request.
* Email format is validated with a strict regex.
* The app includes basic hardening to avoid duplicate entries and malformed requests.

---


