# 🔗 ShortURLs (URL shortener)

A small, modern URL shortener web app with user accounts and Google OAuth. This README follows a friendly, emoji-led format with everything you need to run, develop, and deploy the project.

✨ Features
- User accounts with email/password
- Google sign-in (OAuth2)
- Create, list and delete short URLs
- Private (per-user) and public short-links (fallback)
- Simple EJS-based dashboard and views

🚀 Tech stack
- Node.js + Express
- PostgreSQL (pg)
- Passport.js (local + passport-google-oauth2)
- EJS templating
- shortid for key generation

📦 Installation & Setup

Prerequisites
- Node.js (v16+)
- npm
- PostgreSQL

1. Clone the repository
```bash
git clone <your-repo-url>
cd shortURLS
```

2. Install dependencies
```bash
npm install
```

3. Environment configuration
Copy `.env.example` to `.env` and fill the values:
```bash
cp .env.example .env
```
Required variables in `.env`:
- PGHOST, PGDATABASE, PGUSER, PGPASSWORD
- SECRET (session secret)
- GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET
- CALLBACK_URL (e.g. `http://localhost:3000/auth/google/dashboard`)
- NODE_ENV

> Make sure `CALLBACK_URL` exactly matches the Authorized Redirect URI in Google Cloud Console.

4. Start the app
```bash
npm start
```
Open: http://localhost:3000

🌐 API & Routes
| Method | Path | Description |
|---|---|---|
| GET | / | Home |
| GET | /register | Register page |
| POST | /register | Create account |
| GET | /login | Login page |
| POST | /login | Local login |
| GET | /auth/google | Start Google OAuth |
| GET | /auth/google/dashboard | Google callback |
| GET | /dashboard | User dashboard (auth) |
| GET | /submit | Submit page (auth) |
| POST | /submit | Create short URL (auth) |
| POST | /delete | Delete short URL (auth) |
| GET | /:code | Resolve short URL (public fallback) |

Example: resolve a short link
```bash
curl http://localhost:3000/abc12
```

🏗️ Project structure
```
shortURLS/
├── index.js        # Express app, routes, auth
├── package.json
├── .env.example
├── README.md
├── public/         # static assets
├── views/          # EJS templates (home, login, dashboard...)
└── queries.sql     # DB schema (users, urls)
```

🔁 Database (quick)
The `queries.sql` creates two tables:
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password TEXT NOT NULL
);

CREATE TABLE urls (
    id SERIAL PRIMARY KEY,
    user_id INT NOT NULL,
    short_key VARCHAR(50) UNIQUE NOT NULL,
    original_url TEXT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

Recommended indexes (to improve lookup performance):
- `CREATE INDEX idx_urls_short_key ON urls(short_key);`
- `CREATE INDEX idx_urls_user_short ON urls(user_id, short_key);`

🔑 Google OAuth setup
1. Go to Google Cloud Console → APIs & Services → Credentials
2. Create OAuth client (Web application)
3. Add Authorized redirect URIs:
```
http://localhost:3000/auth/google/dashboard
https://your-production-domain.com/auth/google/dashboard
```
4. Set `GOOGLE_CLIENT_ID` and `GOOGLE_CLIENT_SECRET` in `.env`

🧪 Testing & development tips
- To run on a different port: `PORT=4000 npm start`
- Use browser devtools → Application → Cookies to confirm session cookie is set after login
- For local Google testing, add `http://localhost:3000/auth/google/dashboard` to Google Console

🚀 Deployment notes
- Set env vars on the host (Render, Vercel, Heroku, Railway)
- Ensure `CALLBACK_URL` uses your production domain and is added to Google Console

🙏 Acknowledgments
- Built with Express, Passport, and PostgreSQL
- Thanks to open-source contributors

Made with ❤️ by Aakarsh Divyam
