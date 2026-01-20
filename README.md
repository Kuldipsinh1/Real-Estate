# Real Estate Platform

A full-stack real estate application that connects property buyers, sellers, and administrators. The platform enables users to browse properties, schedule appointments, leave reviews, and manage their favorites. Administrators have control over property listings, user management, and content moderation.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Frontend Routes](#frontend-routes)
- [Database Schema](#database-schema)
- [Development](#development)
- [Docker](#docker)
- [Contributing](#contributing)

## ✨ Features

### User Features
- **User Authentication**: Registration, login, and profile management
- **Property Browsing**: View properties with detailed information and images
- **Search & Filter**: Find properties by location, category, price range, and features
- **Property Details**: View comprehensive property information including amenities
- **Favorites Management**: Save favorite properties for quick access
- **Appointments**: Schedule viewing appointments with property owners
- **Reviews**: Write and read reviews about properties and experiences
- **Profile Management**: Update profile information, password, and profile picture
- **Image Cropping**: Tool to crop and resize profile pictures

### Admin Features
- **Admin Dashboard**: Overview of platform statistics and pending items
- **Property Management**: 
  - Approve/reject property listings
  - Feature properties for homepage showcase
  - View all properties and their status (pending, approved, sold)
- **User Management**: 
  - View all users
  - Verify user accounts
  - Activate/deactivate user accounts
- **Category Management**: Create, update, and delete property categories
- **Location Management**: Create, update, and delete property locations
- **Review Moderation**: Approve/reject user reviews
- **Appointment Tracking**: View all appointments and manage scheduling

### General Features
- **JWT Authentication**: Secure token-based authentication
- **Multi-role Authorization**: Different access levels for users and admins
- **Image Upload**: Upload property images and profile pictures
- **Responsive Design**: Mobile-friendly interface with Tailwind CSS and Ant Design
- **Real-time Updates**: Redux state management for efficient data handling

## 🛠 Tech Stack

### Backend
- **Framework**: Flask 3.1.2
- **Database**: MySQL 8.0
- **ORM**: SQLAlchemy 2.0.44
- **Authentication**: PyJWT 2.10.1
- **Security**: cryptography 46.0.3
- **API**: Flask-CORS 6.0.1, Flask-SQLAlchemy 3.1.1
- **Environment**: python-dotenv 1.2.1

### Frontend
- **Framework**: React 19.2.0
- **Build Tool**: Vite (rolldown-vite 7.2.5)
- **State Management**: Redux Toolkit 2.11.2
- **Routing**: React Router DOM 7.11.0
- **UI Components**: Ant Design 6.1.4
- **Styling**: Tailwind CSS 4.1.18
- **HTTP Client**: Axios 1.13.2
- **Image Editor**: React Easy Crop 5.5.6

### DevOps
- **Containerization**: Docker & Docker Compose
- **Container Orchestration**: Docker Compose

## 📁 Project Structure

```
real-estate/
├── docker-compose.yml              # Docker Compose configuration
├── README.md                        # Project documentation
│
├── real-estate-backend/
│   ├── app.py                      # Flask application entry point
│   ├── requirements.txt             # Python dependencies
│   ├── Dockerfile                  # Backend Docker configuration
│   ├── .env                        # Environment variables
│   └── base/
│       ├── __init__.py             # Flask app initialization and database setup
│       ├── com/
│       │   ├── controller/         # API endpoints
│       │   │   ├── admin_controller.py       # Admin operations
│       │   │   ├── appointment_controller.py # Appointment management
│       │   │   ├── category_controller.py    # Category management
│       │   │   ├── favorite_controller.py    # Favorites management
│       │   │   ├── location_controller.py    # Location management
│       │   │   ├── property_controller.py    # Property management
│       │   │   ├── review_controller.py      # Review operations
│       │   │   └── user_controller.py        # User authentication & profile
│       │   ├── dao/                # Data Access Objects
│       │   │   ├── appointment_dao.py
│       │   │   ├── category_dao.py
│       │   │   ├── favorite_dao.py
│       │   │   ├── location_dao.py
│       │   │   ├── property_dao.py
│       │   │   ├── review_dao.py
│       │   │   └── user_dao.py
│       │   ├── vo/                 # Value Objects (Database Models)
│       │   │   ├── appointment_vo.py
│       │   │   ├── category_vo.py
│       │   │   ├── favorite_vo.py
│       │   │   ├── location_vo.py
│       │   │   ├── property_vo.py
│       │   │   ├── review_vo.py
│       │   │   └── user_vo.py
│       ├── static/                 # Static files
│       │   ├── property_images/    # Uploaded property images
│       │   └── profile_pictures/   # User profile pictures
│       └── utils/
│           ├── admin_setup.py      # Admin user initialization
│           ├── decorators.py       # Token verification decorator
│           ├── helpers.py          # Utility functions
│           └── validators.py       # Input validation functions
│
└── real-estate-frontend/
    ├── package.json                # Node dependencies
    ├── vite.config.js              # Vite configuration
    ├── eslint.config.js            # ESLint configuration
    ├── Dockerfile                  # Frontend Docker configuration
    ├── .env                        # Frontend environment variables
    ├── index.html                  # HTML entry point
    └── src/
        ├── main.jsx                # React entry point
        ├── App.jsx                 # Main App component
        ├── App.css                 # App styles
        ├── index.css               # Global styles
        ├── output.css              # Tailwind CSS output
        ├── assets/                 # Images and static assets
        ├── components/             # Reusable components
        │   ├── AdminLayout.jsx
        │   ├── AppointmentModal.jsx
        │   ├── AuthLayout.jsx
        │   ├── AuthWatcher.jsx
        │   ├── Footer.jsx
        │   ├── Navbar.jsx
        │   ├── PropertyCard.jsx
        │   ├── ProtectedRoute.jsx
        │   ├── ReviewForm.jsx
        │   └── Toast.jsx
        ├── pages/                  # Page components
        │   ├── AdminAddCategory.jsx
        │   ├── AdminAddLocation.jsx
        │   ├── AdminAddProperty.jsx
        │   ├── AdminAppointments.jsx
        │   ├── AdminCategories.jsx
        │   ├── AdminDashboard.jsx
        │   ├── AdminLocations.jsx
        │   ├── AdminLogin.jsx
        │   ├── AdminProperties.jsx
        │   ├── AdminReviews.jsx
        │   ├── AdminUsers.jsx
        │   ├── BookAppointment.jsx
        │   ├── Dashboard.jsx
        │   ├── EditProfile.jsx
        │   ├── Favorites.jsx
        │   ├── Home.jsx
        │   ├── Login.jsx
        │   ├── NotFound.jsx
        │   ├── PropertyDetails.jsx
        │   ├── PropertyList.jsx
        │   └── Register.jsx
        ├── redux/                  # Redux state management
        │   ├── store.js
        │   └── slices/
        │       ├── appointmentSlice.js
        │       ├── authSlice.js
        │       ├── categorySlice.js
        │       ├── favoriteSlice.js
        │       ├── locationSlice.js
        │       ├── propertySlice.js
        │       └── reviewSlice.js
        ├── services/               # API service layer
        │   ├── api.js              # Axios configuration
        │   ├── appointmentService.js
        │   ├── authService.js
        │   ├── categoryService.js
        │   ├── favoriteService.js
        │   ├── locationService.js
        │   ├── propertyService.js
        │   └── reviewService.js
        └── utils/
            └── imageHelper.js      # Image processing utilities
```

## 📋 Prerequisites

- **Node.js** 18+ and npm
- **Python** 3.8+
- **MySQL** 8.0+
- **Docker** and **Docker Compose** (for containerized setup)

## 🚀 Installation & Setup

### Using Docker (Recommended)

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd real-estate
   ```

2. **Create environment files**
   
   Create `real-estate-backend/.env`:
   ```env
   SECRET_KEY=your-secret-key-here
   DB_HOST=mysql
   DB_PORT=3306
   DB_NAME=RealEstate_DB
   DB_USER=root
   DB_PASSWORD=root
   ```

   Create `real-estate-frontend/.env`:
   ```env
   VITE_API_URL=http://localhost:5000
   ```

3. **Build and run with Docker Compose**
   ```bash
   docker-compose up -d --build
   ```

   This will start:
   - MySQL database on port 3307
   - Backend API on port 5000
   - Frontend on port 3000

### Manual Setup

#### Backend Setup

1. **Navigate to backend directory**
   ```bash
   cd real-estate-backend
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your database credentials
   ```

5. **Run the backend**
   ```bash
   python app.py
   ```
   The API will be available at `http://localhost:5000`

#### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd real-estate-frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your API URL
   ```

4. **Run the frontend**
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:5173`

## ⚙️ Configuration

### Backend Configuration

The backend uses environment variables for configuration:

| Variable | Description | Default |
|----------|-------------|---------|
| `SECRET_KEY` | JWT secret key for token generation | Required |
| `DB_HOST` | MySQL hostname | localhost |
| `DB_PORT` | MySQL port | 3306 |
| `DB_NAME` | Database name | RealEstate_DB |
| `DB_USER` | Database user | root |
| `DB_PASSWORD` | Database password | root |

### Frontend Configuration

The frontend uses environment variables for API configuration:

| Variable | Description | Default |
|----------|-------------|---------|
| `VITE_API_URL` | Backend API base URL | http://localhost:5000 |

## 🏃 Running the Application

### With Docker Compose
```bash
cd real-estate
docker-compose up -d
```

Access:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000
- MySQL: localhost:3307 (user: root, password: root)

### Manual (Two terminals required)

**Terminal 1 - Backend:**
```bash
cd real-estate-backend
python app.py
```

**Terminal 2 - Frontend:**
```bash
cd real-estate-frontend
npm run dev
```

### Default Admin Credentials

The system automatically creates a default admin user:
- **Email**: admin@example.com
- **Password**: Admin@123
- **Username**: admin

> Change these credentials after first login!

## 📚 API Documentation

### Authentication Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/register` | Register new user |
| POST | `/api/login` | User login |
| GET | `/api/profile` | Get current user profile (Protected) |
| PUT | `/api/profile` | Update user profile (Protected) |
| POST | `/api/change-password` | Change user password (Protected) |

### Property Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/properties` | Create new property (Protected) |
| GET | `/api/properties` | Get all properties with filters |
| GET | `/api/properties/<id>` | Get specific property |
| GET | `/api/my-properties` | Get user's properties (Protected) |
| PUT | `/api/properties/<id>/sold` | Mark property as sold (Protected) |
| PUT | `/api/properties/<id>/pending` | Mark property as pending (Protected) |
| GET | `/api/properties/sold` | Get all sold properties |
| GET | `/api/properties/pending-status` | Get pending properties |

### Appointment Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/appointments` | Create appointment (Protected) |
| GET | `/api/appointments` | Get appointments (Protected) |
| PUT | `/api/appointments/<id>` | Update appointment (Protected) |
| PUT | `/api/appointments/<id>/cancel` | Cancel appointment (Protected) |
| DELETE | `/api/appointments/<id>` | Delete appointment (Protected) |
| GET | `/api/appointments/today` | Get today's appointments (Protected) |

### Review Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/reviews` | Create review (Protected) |
| GET | `/api/reviews/property/<id>` | Get property reviews |
| GET | `/api/reviews/my-reviews` | Get user's reviews (Protected) |
| PUT | `/api/reviews/<id>` | Update review (Protected) |
| DELETE | `/api/reviews/<id>` | Delete review (Protected) |

### Favorite Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/favorites` | Add favorite (Protected) |
| GET | `/api/favorites` | Get user's favorites (Protected) |
| DELETE | `/api/favorites/<property_id>` | Remove favorite (Protected) |
| GET | `/api/favorites/check/<property_id>` | Check if property is favorited (Protected) |

### Location Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/locations` | Create location (Admin) |
| GET | `/api/locations` | Get all locations |
| GET | `/api/locations/search` | Search locations |
| GET | `/api/locations/city/<city>` | Get locations by city |
| PUT | `/api/locations/<id>` | Update location (Admin) |
| DELETE | `/api/locations/<id>` | Delete location (Admin) |

### Category Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/categories` | Create category (Admin) |
| GET | `/api/categories` | Get all categories |
| GET | `/api/categories/<id>` | Get specific category |
| PUT | `/api/categories/<id>` | Update category (Admin) |
| DELETE | `/api/categories/<id>` | Delete category (Admin) |

### Admin Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/admin/dashboard` | Admin dashboard stats (Admin) |
| GET | `/api/admin/properties/pending` | Get pending properties (Admin) |
| POST | `/api/admin/properties/<id>/approve` | Approve property (Admin) |
| POST | `/api/admin/properties/<id>/feature` | Feature property (Admin) |
| POST | `/api/admin/users/<id>/verify` | Verify user (Admin) |
| POST | `/api/admin/users/<id>/deactivate` | Deactivate user (Admin) |
| POST | `/api/admin/users/<id>/activate` | Activate user (Admin) |
| GET | `/api/admin/reviews/pending` | Get pending reviews (Admin) |
| POST | `/api/admin/reviews/<id>/approve` | Approve review (Admin) |

## 🗺️ Frontend Routes

### Public Routes
- `/` - Home page
- `/login` - User login
- `/register` - User registration
- `/properties` - Property listing
- `/properties/:id` - Property details
- `/not-found` - 404 page

### Protected User Routes (Authentication Required)
- `/dashboard` - User dashboard
- `/favorites` - User's favorite properties
- `/edit-profile` - Edit profile
- `/book-appointment` - Book appointments

### Admin Routes (Admin Authentication Required)
- `/admin/login` - Admin login
- `/admin/dashboard` - Admin dashboard
- `/admin/properties` - Manage properties
- `/admin/properties/add` - Add new property
- `/admin/categories` - Manage categories
- `/admin/categories/add` - Add new category
- `/admin/locations` - Manage locations
- `/admin/locations/add` - Add new location
- `/admin/users` - Manage users
- `/admin/appointments` - View appointments
- `/admin/reviews` - Moderate reviews

## 💾 Database Schema

### Key Tables

**Users**
- user_id (PK)
- user_name
- user_email (UNIQUE)
- user_password
- user_phone
- user_address
- user_role (user/admin)
- user_profile_picture
- is_verified
- is_active
- created_at

**Properties**
- property_id (PK)
- user_id (FK)
- category_id (FK)
- location_id (FK)
- property_title
- property_description
- property_type
- price
- bedrooms
- bathrooms
- area_sqft
- address
- property_images (JSON)
- status (pending/approved/sold)
- is_featured
- created_at

**Appointments**
- appointment_id (PK)
- property_id (FK)
- user_id (FK)
- appointment_date
- appointment_time
- status (scheduled/completed/cancelled)
- notes
- created_at

**Reviews**
- review_id (PK)
- property_id (FK)
- user_id (FK)
- rating
- review_text
- is_approved
- created_at

**Favorites**
- favorite_id (PK)
- user_id (FK)
- property_id (FK)
- created_at

**Locations**
- location_id (PK)
- city
- state
- country
- latitude
- longitude

**Categories**
- category_id (PK)
- category_name
- category_description

## 👨‍💻 Development

### Backend Development

1. **Project Structure**: The backend follows a layered architecture:
   - **Controllers**: Handle HTTP requests and responses
   - **DAOs**: Manage database operations
   - **Value Objects (VOs)**: Define database models
   - **Utils**: Helper functions and validators

2. **Adding a New Feature**:
   - Create VO (model) in `base/com/vo/`
   - Create DAO in `base/com/dao/`
   - Create Controller with routes in `base/com/controller/`
   - Add validators if needed in `base/utils/validators.py`

3. **Authentication**: 
   - Use `@token_required` decorator on protected endpoints
   - Tokens verified in `base/utils/decorators.py`

### Frontend Development

1. **Component Structure**: React components with hooks
2. **State Management**: Redux Toolkit for global state
3. **API Layer**: Services in `src/services/` for API calls
4. **Styling**: Tailwind CSS + Ant Design components

### Linting

Run ESLint on the frontend:
```bash
npm run lint
```

## 🐳 Docker

### Building Images

```bash
# Build all services
docker-compose build

# Build specific service
docker-compose build real-estate-backend
docker-compose build real-estate-frontend
```

### Container Commands

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f real-estate-backend
docker-compose logs -f real-estate-frontend

# Execute command in container
docker-compose exec real-estate-backend bash
docker-compose exec real-estate-frontend bash
```

### Useful Commands

```bash
# Rebuild and restart
docker-compose up -d --build

# Clean up all containers and volumes
docker-compose down -v

# Check container status
docker-compose ps
```

## 📝 Contributing

1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Submit a pull request with detailed description

### Code Style

- **Backend**: Follow PEP 8 conventions
- **Frontend**: Use ESLint configuration provided

## 📝 License

This project is licensed under the MIT License.

## 🤝 Support

For issues and questions, please create an issue in the repository.

---

**Last Updated**: January 2026