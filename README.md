# 🔐 Secure Authentication with Node.js & PostgreSQL

This project demonstrates how to build a secure user authentication system using **Node.js**, **PostgreSQL**, and **bcrypt** for password hashing with salting.  
It highlights best practices in **web security**, **database integration**, and **backend development**.

---

## 🚀 Key Skills Demonstrated
- **Node.js & Express.js**
  - Built RESTful routes for registration and login
  - Middleware for request parsing and static file handling

- **PostgreSQL**
  - User management with relational database design
  - Secure storage of user credentials in a dedicated `users` table

- **Security**
  - Passwords are **never stored in plain text**
  - Implemented **bcrypt hashing with salting** to protect credentials
  - Password verification using secure hash comparison

- **Templating**
  - Simple UI with EJS templates for registration, login, and secure content

---

## 🔐 Security Implementation
- On **registration**:
  - User enters email + password
  - Password is **hashed with bcrypt and salt rounds**
  - Stored securely in PostgreSQL

- On **login**:
  - User enters credentials
  - Password is compared with stored hash using `bcrypt.compare`
  - If match → Access granted, else → Error

This ensures that even if the database is compromised, raw passwords are **never exposed**.

---

## 📂 Project Structure
```
├── index.js          # Express server and routes
├── package.json      # Dependencies
├── public/           # Static assets
├── views/            # EJS templates
└── screenshots/      # Project screenshots
```

---

## ⚙️ Setup & Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Setup PostgreSQL**
   - Create a database called `secrets`
   - Create a `users` table:
     ```sql
     CREATE TABLE users (
       id SERIAL PRIMARY KEY,
       email VARCHAR(100) UNIQUE NOT NULL,
       password VARCHAR(200) NOT NULL
     );
     ```

4. **Configure database connection in `index.js`**
   ```js
   const db = new pg.Client({
     user: "postgres",
     host: "localhost",
     database: "secrets",
     password: "your-password",
     port: 5432
   });
   ```

5. **Run the project**
   ```bash
   node index.js
   ```
   Navigate to [http://localhost:3000](http://localhost:3000).

---

## 📸 Screenshots

### 🗄️ Database: Users Table
![Database Screenshot](screenshots/db-users.png)

### 📝 Register Page
![Register Screenshot](screenshots/register.png)

### 🔑 Login Page
![Login Screenshot](screenshots/login.png)

### 🎉 Secrets Page
![Secrets Screenshot](screenshots/secrets.png)

> 💡 Add your actual screenshots in the `screenshots/` folder with the names shown above.

---

## 🛠 Technologies Used
- **Node.js** – Server-side JavaScript runtime  
- **Express.js** – Web framework for handling routes  
- **PostgreSQL** – Relational database for user storage  
- **bcrypt** – Secure hashing & salting for passwords  
- **EJS** – Templating for views  

---

## 📌 Future Enhancements
- Use **environment variables** (`dotenv`) for credentials  
- Implement **JWT or sessions** for persistent authentication  
- Add **password reset functionality**  
- Integrate **input validation** & **rate limiting** for stronger security  

---

## 📜 License
Licensed under the **ISC License**.
