## maturitni prace ait

Modern JavaScript/TypeScript application for managing courses, learning materials, and quizzes for students and teachers.

### Project structure

- **apps/server**: Node.js (Express) backend API
- **apps/web**: Vue 3 + Vite frontend
- **pytest-selenium**: Python test suite (pytest + Selenium)

### Requirements

- Node.js 18–22
- npm (or yarn/pnpm if you prefer)
- Docker (recommended, for local MySQL)
- Python 3.10+ (only if you want to run the pytest/Selenium tests)

### 1. Run the backend (API)

From the project root:

```bash
cd apps/server
npm install

# Start MySQL in Docker on port 3307 (recommended)
npm run db

# Prepare environment file if needed (example)
# cp .env.example .env

# Start backend in development mode
npm run dev
```

The backend will run on `http://localhost:3000` and expose endpoints such as:

- `GET /api/courses`
- `GET /api/dashboard`
- `POST /api/login`

### 2. Run the frontend (web app)

In another terminal, from the project root:

```bash
cd apps/web
npm install
npm run dev
```

By default Vite will start on something like `http://localhost:5173`.  
The frontend will call the backend API under the `/api/...` paths.

### 3. Run the Python tests (optional)

The `pytest-selenium` folder contains:

- API tests using pytest and `requests`
- End-to-end UI tests using Selenium + Chrome

From the project root:

```bash
cd pytest-selenium
python -m venv .venv
# On Windows PowerShell:
.venv\Scripts\Activate.ps1

pip install pytest selenium requests
pytest
```

You can configure:

- `BACKEND_BASE_URL` (default `http://localhost:3000`)
- `FRONTEND_BASE_URL` (default `http://localhost:5173`)
- `SELENIUM_HEADLESS` (default `"1"`, runs Chrome headless)

