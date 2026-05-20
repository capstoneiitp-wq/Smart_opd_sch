# Smart OPD Queue Management System

Smart OPD is a modern, real-time Outpatient Department (OPD) queue management system designed to streamline hospital waiting rooms. It provides an intuitive interface for patients to check in, doctors to manage their queues, and administrators to oversee hospital operations.

## Architecture

The project is built as a monorepo containing both the frontend and backend applications:

*   **Frontend (`/frontend`)**: A fast, responsive Single Page Application (SPA) built with React and Vite.
*   **Backend (`/backend`)**: A robust REST API and Server-Sent Events (SSE) provider built with Python and Flask.
*   **Database**: MySQL (configured for persistent storage, with a fallback to memory-based storage for testing).

## Features

*   **Patient Experience**:
    *   Self check-in via QR codes or manual entry.
    *   Real-time queue position tracking.
    *   Estimated wait time predictions based on dynamic doctor consultation averages.
    *   Automated notifications (SMS/WhatsApp integration ready).
*   **Doctor Dashboard**:
    *   Real-time queue visibility.
    *   Ability to call the next patient, mark as completed, or flag as a "no-show".
    *   Emergency insert capabilities for critical cases.
*   **Admin / Hospital Overview**:
    *   Live tracking of all departments and active doctors.
    *   Queue analytics, average wait times, and delay tracking.
    *   Crowd risk level monitoring for different hospital zones.

## Local Development

### Prerequisites
*   Node.js (v18+)
*   Python (3.11+)
*   MySQL (Optional, defaults to memory storage if not configured)

### Setting up the Backend
1. Navigate to the backend directory: `cd backend`
2. Create a virtual environment: `python -m venv venv`
3. Activate the environment:
    *   Windows: `venv\Scripts\activate`
    *   Mac/Linux: `source venv/bin/activate`
4. Install dependencies: `pip install -r requirements.txt`
5. Run the server: `python app.py` (The API will start on `http://localhost:5000`)

### Setting up the Frontend
1. Navigate to the frontend directory: `cd frontend`
2. Install dependencies: `npm install`
3. Start the development server: `npm run dev` (The app will start on `http://localhost:5173`)

## Deployment

This project is configured for seamless deployment to Vercel (Frontend) and Railway (Backend).

### Railway (Backend)
The backend is configured to use Railway's Dockerfile builder. 
1. Create a new Railway project and connect your GitHub repository.
2. Set the **Root Directory** to `/backend`.
3. Add a MySQL plugin to the Railway project. Railway will automatically inject variables like `MYSQLHOST`, `MYSQLUSER`, etc., which the application will automatically detect.
4. Set the `APP_ALLOWED_ORIGINS` environment variable to your frontend URL (e.g., `https://your-frontend.vercel.app`) to resolve CORS issues.

### Vercel (Frontend)
The frontend uses Vite and is configured via the `vercel.json` file.
1. Create a new Vercel project and connect your GitHub repository.
2. Set the **Root Directory** to `frontend`.
3. Add a new Environment Variable: `VITE_API_BASE_URL` and set it to your Railway backend URL (e.g., `https://your-backend.up.railway.app/api`).
4. Deploy. (Note: If you change the environment variable later, you must manually trigger a Redeploy).

## License

This project is licensed under the MIT License.
