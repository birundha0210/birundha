# 🚀 How to Run the Application

## ✅ Error Fixed!

The error you saw was because you tried to run `npm` commands from the root directory, but the actual code is in `backend/` and `frontend/` subdirectories.

**I've fixed this by creating a root package.json with helpful scripts!**

---

## Quick Start (Easiest Way)

Now you can run the entire application from the root directory with one command!

### Option 1: Run Both Servers at Once (Recommended)

```bash
npm run dev
```

This starts both the backend and frontend simultaneously!

### Option 2: Run Servers Separately

**Terminal 1 - Backend:**
```bash
npm run dev:backend
```

**Terminal 2 - Frontend:**
```bash
npm run dev:frontend
```

---

## Available Commands (From Root Directory)

| Command | Description |
|---------|-------------|
| `npm run dev` | Start both backend & frontend |
| `npm run dev:backend` | Start backend only |
| `npm run dev:frontend` | Start frontend only |
| `npm run install:all` | Install all dependencies |
| `npm run build:all` | Build both projects |

---

## Alternative: Run from Subdirectories

If you prefer to work in individual folders:

### Backend
```bash
cd backend
npm run dev
```

### Frontend
```bash
cd frontend
npm run dev
```

---

## Current Application Status

✅ **Backend**: Port 5000  
✅ **Frontend**: Port 5173  
✅ **Database**: In-Memory MongoDB (auto-starts)  
✅ **All Dependencies**: Installed  

---

## Next Steps

1. **Start the application:**
   ```bash
   npm run dev
   ```

2. **Open your browser:**
   - Frontend: http://localhost:5173
   - Or click the preview button

3. **Test the app:**
   - Register a new account
   - Login and create tickets
   - Enjoy!

---

## Common Commands Reference

### From Root Directory:
- `npm run dev` - Start everything
- `npm run dev:backend` - Backend only
- `npm run dev:frontend` - Frontend only

### From Backend Directory (`cd backend`):
- `npm run dev` - Start backend
- `npm run build` - Build backend
- `npm start` - Run production

### From Frontend Directory (`cd frontend`):
- `npm run dev` - Start dev server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

---

## Troubleshooting

### "Cannot find package.json"
- Make sure you're in the correct directory
- Root directory: Use `npm run dev`
- Backend: `cd backend` then `npm run dev`
- Frontend: `cd frontend` then `npm run dev`

### Port Already in Use
- Kill the existing process
- Or change ports in configuration files

### Module Not Found
- Run `npm install` in the root directory
- Or run `npm run install:all`

---

**Everything is set up! Just run `npm run dev` to start! 🎉**
