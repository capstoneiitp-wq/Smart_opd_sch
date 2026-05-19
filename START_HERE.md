# Smart OPD Share Folder

This folder is prepared for group sharing and local testing.

## Run Locally

1. Install Docker Desktop and make sure Docker is running.
2. Open this folder in a terminal.
3. Run:

```powershell
docker compose up --build -d
```

4. Open the app in a browser:

- Frontend: `http://127.0.0.1:3000`
- Backend health: `http://127.0.0.1:5000/api/health`

## Staff Login

- Admin: `admin@smartopd.local` / `Admin@123`
- Doctor: `doctor.cardiology@smartopd.local` / `Doctor@123`
- Doctor: `doctor.general@smartopd.local` / `DoctorNew@123`
- Staff: `staff.frontdesk@smartopd.local` / `Staff@123`

## Notes

- This share folder keeps the project files needed to run the app.
- It does not include local cache folders like `node_modules`, `.venv`, or `dist`.
- Current notification/provider settings are included, so share this only within your project group.
