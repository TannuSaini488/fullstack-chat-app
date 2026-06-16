# Fullstack Chat App

A full-stack real-time chat application with authentication, profile updates, image uploads, online presence, and Socket.IO-based messaging.

## Tech Stack

- Frontend: React, Vite, Zustand, React Router, Tailwind CSS, DaisyUI
- Backend: Node.js, Express, MongoDB, Mongoose, Socket.IO
- Auth and media: JWT cookies, bcryptjs, Cloudinary

## Features

- Sign up, log in, log out
- Protected routes with cookie-based JWT auth
- Update profile picture
- Real-time one-to-one messaging
- Image uploads through Cloudinary
- Online user presence

## Project Structure

- `backend/` - Express API, Socket.IO server, MongoDB models, auth and message routes
- `frontend/` - Vite React app, UI components, state stores, chat screens

## Prerequisites

- Node.js 20.x
- MongoDB database
- Cloudinary account

## Environment Variables

Create a `.env` file in `backend/` with:

```env
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_CLOUD_KEY=your_cloud_api_key
CLOUDINARY_CLOUD_SECRET=your_cloud_api_secret
PORT=5001
NODE_ENV=development
```

`PORT=5001` is recommended for local development because the frontend points to `http://localhost:5001`.

## Installation

From the project root:

```bash
npm install
```

Or install each app separately:

```bash
npm install --prefix backend
npm install --prefix frontend
```

## Development

Run the backend:

```bash
npm run dev --prefix backend
```

Run the frontend:

```bash
npm run dev --prefix frontend
```

If you use a different backend port, update the API base URL in `frontend/src/lib/axios.js` and the Socket.IO URL in `frontend/src/store/useAuthStore.js`.

## Production Build

Build the frontend and prepare dependencies:

```bash
npm run build
```

Start the backend:

```bash
npm start
```

In production, the backend serves the built frontend from `frontend/dist`.

## API Endpoints

Auth:

- `POST /api/auth/signup`
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `PUT /api/auth/update-profile`
- `GET /api/auth/check`

Messages:

- `GET /api/messages/users`
- `GET /api/messages/chat/:id`
- `POST /api/messages/send/:id`

## Notes

- The frontend uses `withCredentials: true`, so cookies must be enabled.
- Make sure CORS allows the frontend origin during development.
- The app expects MongoDB and Cloudinary credentials to be available before the server starts.
