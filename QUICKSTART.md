# Quick Start Guide

## What You Have

A complete **Customer Support Ticketing System** with:
- ✅ Backend API (Node.js + Express + TypeScript)
- ✅ Frontend UI (React + TypeScript + Vite)
- ✅ User authentication and authorization
- ✅ Full CRUD operations for tickets
- ✅ Comments system
- ✅ Role-based access control
- ✅ Beautiful, responsive design

## Current Status

🟢 **Frontend**: Running on http://localhost:5173  
🟢 **Backend**: Running on http://localhost:5000  
🔴 **MongoDB**: Not connected (needs setup)

You can click the preview browser button to view the frontend, but you'll need to set up MongoDB before the application can fully function.

## Quick Start (3 Steps)

### Step 1: Set Up MongoDB

**Option A - Local Installation (Recommended)**
1. Download MongoDB: https://www.mongodb.com/try/download/community
2. Install and start MongoDB service
3. See `MONGODB_SETUP.md` for detailed instructions

**Option B - Cloud (MongoDB Atlas)**
1. Create free account at https://www.mongodb.com/cloud/atlas
2. Create cluster and get connection string
3. Update `backend/.env` with your connection string

### Step 2: Restart Backend

Once MongoDB is running:
```bash
# The backend will automatically reconnect
# Or restart it manually:
cd backend
npm run dev
```

### Step 3: Use the Application

1. Click the preview browser button (or open http://localhost:5173)
2. Click "Register" to create an account
3. Choose a role:
   - **Customer**: Create and manage your tickets
   - **Agent**: View and update all tickets
   - **Admin**: Full system access
4. Start creating tickets!

## Features Overview

### For Customers
- Create support tickets with priority levels
- View your ticket history
- Add comments to tickets
- Track ticket status

### For Agents
- View all open and assigned tickets
- Update ticket status (In Progress, Resolved, Closed)
- Add internal notes
- Communicate with customers via comments

### For Admins
- All agent features
- Delete tickets
- Access to all system data
- User management capabilities

## Application Structure

```
Frontend (React)
├── Login/Register pages
├── Dashboard (with stats)
├── Create Ticket form
└── Ticket Details (with comments)

Backend (Express API)
├── /api/auth/* - Authentication endpoints
├── /api/tickets/* - Ticket management
└── /api/comments/* - Comment system

Database (MongoDB)
├── users - User accounts
├── tickets - Support tickets
└── comments - Ticket comments
```

## Testing the Application

1. **Register multiple users** with different roles
2. **As Customer**: Create a few tickets with different priorities
3. **As Agent**: Update ticket statuses and add comments
4. **Test filtering**: Use the status filter on dashboard
5. **Test real-time**: Open same ticket in two browsers

## Customization

### Change Port Numbers

**Backend** (default: 5000)
- Edit `backend/.env`
- Change `PORT=5000` to your preferred port

**Frontend** (default: 5173)
- Edit `frontend/vite.config.ts`
- Add: `server: { port: YOUR_PORT }`

### Modify Styles

- Main stylesheet: `frontend/src/App.css`
- Colors, fonts, and layouts are all customizable
- Uses vanilla CSS (no framework dependencies)

### Add Features

The codebase is well-structured for extensions:
- Add new ticket fields in `backend/src/models/Ticket.ts`
- Create new API endpoints in `backend/src/routes/`
- Add new pages in `frontend/src/pages/`
- Extend types in `frontend/src/types/index.ts`

## Troubleshooting

### "Cannot connect to server"
- Ensure backend is running on port 5000
- Check `frontend/src/services/api.ts` for correct API URL

### "MongoDB connection error"
- Follow steps in `MONGODB_SETUP.md`
- Verify MongoDB is running
- Check connection string in `backend/.env`

### "Module not found" errors
- Run `npm install` in both backend and frontend folders
- Delete `node_modules` and reinstall if persists

### Port already in use
- Kill the process using the port
- Or change port in configuration files

## Production Deployment

See `README.md` for:
- Building for production
- Environment variables
- Security considerations
- Deployment options

## Need Help?

- See `README.md` for full documentation
- See `MONGODB_SETUP.md` for database setup
- Check console for error messages
- Verify all services are running

---

**Happy Ticketing! 🎫**

The application is ready to use once MongoDB is connected.
