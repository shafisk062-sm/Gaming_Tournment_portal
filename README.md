# NEXUS ARENA — Gaming Tournament Portal

## Run locally

1. Install and start MongoDB Community Server, or create a MongoDB Atlas database.
2. In `server`, copy `.env.example` to `.env` and set `MONGO_URI` to your MongoDB connection string. For a local MongoDB server, use:

   ```env
   MONGO_URI=mongodb://127.0.0.1:27017/nexus_arena
   ```

   For Atlas, use the URI from your Atlas deployment and replace its username, password, and database name. Keep `.env` private.
3. Install dependencies for the API and frontend:

   ```powershell
   cd server
   npm install
   cd ..\client
   npm install
   cd ..
   npm install
   ```

4. Start both the API and frontend from the project root:

   ```powershell
   npm run dev
   ```

5. Open the frontend URL printed by Vite (normally `http://localhost:5173`). The API health check is at `http://localhost:5000/api/health`. Keep the terminal running while using the app.

Sample tournaments and demo accounts are inserted into MongoDB when the database is empty. Demo accounts:

- Admin: `admin@nexusarena.gg` / `admin123`
- Organizer: `organizer@nexusarena.gg` / `organizer123`
- Player: `nova@nexusarena.gg` / `player123`

Change demo credentials and `JWT_SECRET` before deploying this application.

## Deploy to Vercel

1. Push this project to GitHub.
2. Import the repository in Vercel.
3. Keep the project root as the repository root.
4. Add these environment variables in Vercel:

   ```env
   MONGO_URI=your_MongoDB_Atlas_connection_string
   JWT_SECRET=a-long-random-production-secret
   ```

5. Deploy. Vercel builds `client` and serves `server/server.js` through `api/index.js`.

MongoDB Atlas must allow network access from `0.0.0.0/0` or Vercel's network, and the Atlas database user must have read/write access.
