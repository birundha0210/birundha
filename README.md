# Customer Support Ticketing System

A full-stack customer support ticketing system built with React, TypeScript, Node.js, Express, and MongoDB.

## Features

- **User Authentication**: Register and login with role-based access (Customer, Agent, Admin)
- **Ticket Management**: Create, view, update, and delete support tickets
- **Priority Levels**: Low, Medium, High, Urgent
- **Status Tracking**: Open, In Progress, Resolved, Closed
- **Comments**: Add comments to tickets for communication
- **Dashboard**: Overview with ticket statistics
- **Role-based Permissions**: Different access levels for customers, agents, and admins

## Tech Stack

### Backend
- Node.js with Express
- TypeScript
- MongoDB with Mongoose
- JWT Authentication
- Bcrypt for password hashing

### Frontend
- React 18
- TypeScript
- React Router for navigation
- Axios for API calls
- Context API for state management
- Vite as build tool

## Project Structure

```
customer-support-ticketing-system/
├── backend/
│   ├── src/
│   │   ├── config/          # Database configuration
│   │   ├── controllers/     # Request handlers
│   │   ├── middleware/      # Auth middleware
│   │   ├── models/          # MongoDB models
│   │   ├── routes/          # API routes
│   │   └── server.ts        # Entry point
│   ├── .env                 # Environment variables
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── components/      # React components
    │   ├── context/         # Context providers
    │   ├── pages/           # Page components
    │   ├── services/        # API services
    │   ├── types/           # TypeScript types
    │   ├── App.tsx          # Main app component
    │   └── main.tsx         # Entry point
    └── package.json
```

## Getting Started

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or cloud instance)

### Installation

1. **Clone the repository or navigate to the project folder**

2. **Install MongoDB** (if not already installed)
   - Download from: https://www.mongodb.com/try/download/community
   - Or use MongoDB Atlas (cloud): https://www.mongodb.com/cloud/atlas

3. **Backend Setup**

   ```bash
   cd backend
   npm install
   ```

   Update the `.env` file if needed:
   ```
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/ticket-system
   JWT_SECRET=your_jwt_secret_key_change_this_in_production
   NODE_ENV=development
   ```

4. **Frontend Setup**

   ```bash
   cd frontend
   npm install
   ```

### Running the Application

1. **Start MongoDB** (if using local MongoDB)
   - Windows: MongoDB should start as a service automatically
   - Or run: `mongod`

2. **Start the Backend Server**
   ```bash
   cd backend
   npm run dev
   ```
   The backend will run on http://localhost:5000

3. **Start the Frontend Development Server**
   ```bash
   cd frontend
   npm run dev
   ```
   The frontend will run on http://localhost:5173

4. **Access the Application**
   - Open your browser and go to http://localhost:5173

## Usage

### Creating an Account

1. Click "Register" on the login page
2. Fill in your details
3. Choose a role:
   - **Customer**: Can create and view their own tickets
   - **Agent**: Can view all tickets and update ticket status
   - **Admin**: Full access to all features

### Creating a Ticket

1. Log in to your account
2. Click "Create New Ticket" on the dashboard
3. Fill in the ticket details:
   - Title
   - Description
   - Priority (Low, Medium, High, Urgent)
   - Category
4. Click "Create Ticket"

### Managing Tickets

- **View Tickets**: Click on any ticket card to see details
- **Add Comments**: Add comments to communicate about the ticket
- **Update Status** (Agents/Admins): Change ticket status (In Progress, Resolved, Closed)
- **Filter Tickets**: Use the status filter on the dashboard

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user (protected)

### Tickets
- `GET /api/tickets` - Get all tickets (filtered by role)
- `GET /api/tickets/stats` - Get ticket statistics
- `GET /api/tickets/:id` - Get ticket by ID
- `POST /api/tickets` - Create new ticket
- `PUT /api/tickets/:id` - Update ticket
- `DELETE /api/tickets/:id` - Delete ticket

### Comments
- `GET /api/comments/:ticketId` - Get comments for a ticket
- `POST /api/comments/:ticketId` - Add comment to ticket
- `DELETE /api/comments/:id` - Delete comment

## Development

### Backend Development
```bash
cd backend
npm run dev  # Starts with nodemon for auto-reload
```

### Frontend Development
```bash
cd frontend
npm run dev  # Starts Vite dev server with HMR
```

### Building for Production

**Backend:**
```bash
cd backend
npm run build
npm start
```

**Frontend:**
```bash
cd frontend
npm run build
npm run preview  # Preview production build
```

## Security Features

- Password hashing with bcrypt
- JWT token-based authentication
- Role-based access control
- Protected API routes
- Input validation

## Future Enhancements

- File attachments for tickets
- Email notifications
- Real-time updates with WebSockets
- Advanced search and filtering
- Ticket assignment workflow
- SLA tracking
- Reports and analytics
- Multi-language support

## Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running
- Check the `MONGODB_URI` in backend `.env` file
- For MongoDB Atlas, ensure your IP is whitelisted

### Port Already in Use
- Change the `PORT` in backend `.env` file
- Or kill the process using the port

### CORS Issues
- Ensure backend CORS is configured correctly
- Check the API URL in frontend `services/api.ts`

## License

MIT

## Author

Built as a demonstration of a full-stack ticketing system
