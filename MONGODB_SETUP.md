# MongoDB Setup Guide

The application requires MongoDB to store tickets, users, and comments. You have two options:

## Option 1: Install MongoDB Locally (Recommended for Development)

### Windows

1. **Download MongoDB Community Server**
   - Visit: https://www.mongodb.com/try/download/community
   - Download the Windows installer (.msi)

2. **Install MongoDB**
   - Run the installer
   - Choose "Complete" installation
   - Install MongoDB as a Windows Service (recommended)
   - Install MongoDB Compass (optional GUI tool)

3. **Verify Installation**
   - Open Command Prompt
   - Run: `mongod --version`
   - You should see the MongoDB version

4. **Start MongoDB Service**
   - MongoDB should start automatically as a Windows service
   - To manually start: Open Services (Win + R, type `services.msc`)
   - Find "MongoDB Server" and ensure it's running
   
   **OR** run in Command Prompt:
   ```bash
   net start MongoDB
   ```

5. **Verify MongoDB is Running**
   - Open Command Prompt
   - Run: `mongosh` (or `mongo` for older versions)
   - You should see MongoDB shell connect successfully

### macOS

1. **Install using Homebrew**
   ```bash
   brew tap mongodb/brew
   brew install mongodb-community
   ```

2. **Start MongoDB**
   ```bash
   brew services start mongodb-community
   ```

3. **Verify**
   ```bash
   mongosh
   ```

### Linux (Ubuntu/Debian)

1. **Import MongoDB GPG Key**
   ```bash
   wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -
   ```

2. **Add MongoDB Repository**
   ```bash
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
   ```

3. **Install MongoDB**
   ```bash
   sudo apt-get update
   sudo apt-get install -y mongodb-org
   ```

4. **Start MongoDB**
   ```bash
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```

5. **Verify**
   ```bash
   mongosh
   ```

## Option 2: Use MongoDB Atlas (Cloud)

MongoDB Atlas is a free cloud-hosted MongoDB service, perfect if you don't want to install MongoDB locally.

1. **Create Account**
   - Go to: https://www.mongodb.com/cloud/atlas
   - Click "Try Free" and create an account

2. **Create a Cluster**
   - Choose "Shared" (Free tier)
   - Select your cloud provider and region
   - Click "Create Cluster" (takes ~3-5 minutes)

3. **Set Up Database Access**
   - Go to "Database Access" in the left menu
   - Click "Add New Database User"
   - Create a username and password (remember these!)
   - Choose "Read and write to any database"

4. **Set Up Network Access**
   - Go to "Network Access" in the left menu
   - Click "Add IP Address"
   - Click "Allow Access from Anywhere" (for development)
   - Or add your specific IP address

5. **Get Connection String**
   - Go to "Database" and click "Connect" on your cluster
   - Choose "Connect your application"
   - Copy the connection string
   - It looks like: `mongodb+srv://username:password@cluster.xxxxx.mongodb.net/`

6. **Update Backend Configuration**
   - Open `backend/.env`
   - Replace the MONGODB_URI:
   ```
   MONGODB_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@YOUR_CLUSTER.mongodb.net/ticket-system?retryWrites=true&w=majority
   ```
   - Replace YOUR_USERNAME, YOUR_PASSWORD, and YOUR_CLUSTER with your details

## Verifying the Connection

After setting up MongoDB:

1. **Start the Backend Server**
   ```bash
   cd backend
   npm run dev
   ```

2. **Check Console Output**
   - You should see: "MongoDB connected successfully"
   - If you see connection errors, review the steps above

## Common Issues

### Connection Refused Error
- **Local MongoDB**: Ensure MongoDB service is running
  - Windows: Check Services or run `net start MongoDB`
  - macOS: `brew services start mongodb-community`
  - Linux: `sudo systemctl start mongod`

### Authentication Failed (Atlas)
- Check username and password in connection string
- Ensure user has proper permissions in Database Access

### IP Not Whitelisted (Atlas)
- Add your IP address in Network Access
- Or temporarily use "Allow Access from Anywhere"

### Port Already in Use
- MongoDB default port is 27017
- Check if another process is using it
- Change port in connection string if needed

## Testing MongoDB

Once connected, you can:

1. **Use MongoDB Compass** (GUI tool)
   - Connect to: `mongodb://localhost:27017`
   - Or your Atlas connection string
   - Browse databases and collections

2. **Use MongoDB Shell** (mongosh)
   ```bash
   mongosh
   use ticket-system
   show collections
   db.users.find()
   db.tickets.find()
   ```

## Next Steps

After MongoDB is set up and running:
1. Start the backend server: `cd backend && npm run dev`
2. Start the frontend: `cd frontend && npm run dev`
3. Open http://localhost:5173 in your browser
4. Register a new user to test the application
