# 🔗 ShortURLS

A lightweight **URL Shortener** built with **Node.js** and **SQL**. This project allows users to shorten long URLs into compact short links and redirect them seamlessly to the original destination.  

🎯 **Goal**: Provide a simple, efficient, and extensible service to generate and manage short URLs.

---

## Features 🚀

- ✅ **URL Shortening** – Convert long URLs into short, shareable links  
- ✅ **Redirection** – Access the original site using the short URL  
- ✅ **Database Integration** – Store URL mappings with SQL  
- ✅ **Environment Config** – Secure setup using `.env` variables  
- ✅ **Scalable Design** – Modular and clean codebase for easy expansion  

---

## Tech Stack 🛠️

- **Language**: JavaScript (Node.js)  
- **Framework**: Express.js  
- **Database**: MySQL (or PostgreSQL)  
- **IDE**: VS Code  
- **Dependencies**: Listed in `package.json`  

---

## Project Structure 📁

```plaintext
shortURLS/
├── index.js        // Main server file
├── package.json    // Project dependencies & scripts
├── queries.sql     // Database schema & queries
├── .env            // Environment variables
└── README.md       // Project documentation
How It Works 🔍

A user submits a long URL.

The backend generates a unique short ID and stores it with the original URL in the database.

When someone visits the short link, the service looks up the original URL and redirects the user.

The mapping stays persistent in the database for repeated use.
