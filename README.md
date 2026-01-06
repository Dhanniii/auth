# Movie Dashboard Application

A full-stack web application for managing movies with authentication, featuring a modern React frontend and Express.js backend.

## Features

### Authentication
- Secure login system with JWT tokens
- Username/password authentication
- Session persistence with localStorage
- Theme-aware SweetAlert2 notifications

### Movie Management
- View all movies in a responsive grid layout
- Add new movies with detailed information
- Delete movies with confirmation
- Persistent storage using JSON file
- Real-time updates via REST API

### User Interface
- Light and Dark mode themes
- Glassmorphism design elements
- Responsive layout for all screen sizes
- Smooth animations and transitions
- Custom scrollbar styling

## Technology Stack

### Frontend
- React.js 18.2.0
- Vite 5.0.8
- SweetAlert2 for notifications
- CSS3 with custom properties

### Backend
- Node.js with Express.js 4.18.2
- JWT for authentication
- CORS enabled
- File-based JSON storage
- dotenv for environment variables

## Project Structure

```
d:\auth\
├── src\
│   ├── components\
│   │   ├── Dashboard\
│   │   │   ├── Dashboard.jsx
│   │   │   └── Dashboard.css
│   │   ├── LoginForm\
│   │   │   ├── LoginForm.jsx
│   │   │   └── LoginForm.css
│   │   └── ThemeToggle\
│   │       ├── ThemeToggle.jsx
│   │       └── ThemeToggle.css
│   ├── data\
│   │   └── movies.json
│   ├── App.jsx
│   ├── App.css
│   ├── main.jsx
│   └── index.css
├── server\
│   ├── routes\
│   │   ├── auth.js
│   │   └── movies.js
│   ├── .env
│   └── index.js
├── index.html
├── package.json
└── vite.config.js
```

## Installation

### Prerequisites
- Node.js (v14 or higher)
- npm (v6 or higher)

### Steps

1. Clone or download the project to your local machine

2. Install dependencies for the main project:
```bash
cd d:\auth
npm install
```

3. Install dependencies for the server:
```bash
cd server
npm install
cd ..
```

## Configuration

### Environment Variables

Create or verify the `.env` file in the `server` directory with the following variables:

```env
PORT=5000
ADMIN_USERNAME=admin
ADMIN_PASSWORD=admin123
JWT_SECRET=your-secret-key-change-this-in-production
```

**Important:** Change the `JWT_SECRET` in production environment.

## Running the Application

### Development Mode

Run both frontend and backend simultaneously:

```bash
npm run dev
```

This will start:
- Frontend (Vite dev server) on `http://localhost:5173`
- Backend (Express API) on `http://localhost:5000`

### Individual Commands

Run frontend only:
```bash
npm run client
```

Run backend only:
```bash
npm run server
```

### Production Build

Build the frontend for production:
```bash
npm run build
```

Preview the production build:
```bash
npm run preview
```

## Usage

### Login

1. Navigate to `http://localhost:5173`
2. Enter credentials:
   - Username: `admin`
   - Password: `admin123`
3. Click "Sign In"

### Managing Movies

After successful login, you can:

**Add Movie:**
1. Click the "Add Movie" button in the header
2. Fill in all required fields:
   - Title
   - Year
   - IMDB Rating
   - Banner URL
   - Genres (comma-separated)
   - Synopsis
3. Click "Add Movie" to save

**Delete Movie:**
1. Hover over a movie card
2. Click the delete icon (trash bin) in the top-left corner
3. Confirm deletion in the popup

**Toggle Theme:**
- Click the sun/moon icon in the header to switch between light and dark modes

**Logout:**
- Click the "Logout" button in the header

## API Endpoints

### Authentication

**POST** `/api/auth/login`
- Body: `{ username, password }`
- Response: `{ success, message, token, user }`

**POST** `/api/auth/verify`
- Headers: `Authorization: Bearer <token>`
- Response: `{ success, user }`

### Movies

**GET** `/api/movies`
- Response: `{ success, movies }`

**POST** `/api/movies`
- Body: `{ title, year, imdbRating, banner, genres, synopsis }`
- Response: `{ success, movie }`

**DELETE** `/api/movies/:id`
- Response: `{ success, message }`

## Data Persistence

Movie data is stored in `src/data/movies.json`. All changes made through the application are automatically saved to this file.

## Troubleshooting

### Server Connection Issues

If you see "Failed to connect to server":
1. Ensure the backend server is running on port 5000
2. Check that no other application is using port 5000
3. Verify CORS is enabled in `server/index.js`

### Login Issues

If login fails with valid credentials:
1. Check the `.env` file exists in the `server` directory
2. Verify the credentials match those in `.env`
3. Ensure the server is running and accessible

### Port Conflicts

If port 5173 or 5000 is already in use:
- Frontend: Vite will automatically try the next available port
- Backend: Change the `PORT` variable in `server/.env`

## Development Notes

- The application uses ES modules (type: "module" in package.json)
- Hot Module Replacement (HMR) is enabled for React components
- All console.log debug statements have been removed for production readiness
- SweetAlert2 themes automatically match the selected UI theme

## Security Considerations

- Change the default admin credentials in production
- Use a strong JWT secret
- Implement rate limiting for API endpoints
- Add input validation and sanitization
- Use HTTPS in production
- Store sensitive data in environment variables

## License

ISC

## Author

Created as a demonstration project for authentication and CRUD operations with React and Express.js.
