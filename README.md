# Personal Portfolio Project

A modern, full-stack personal portfolio application with a React TypeScript frontend and Node.js Express backend. This project showcases a complete web application featuring a portfolio, blog, admin dashboard, and more.

## 🌟 Project Overview

This project consists of two main components:

1. **Frontend**: A modern React application with TypeScript, Vite, TailwindCSS, and shadcn/ui components featuring neumorphic design
2. **Backend**: A secure Node.js Express API with Sequelize ORM, MySQL database, and JWT authentication

## 🐳 Development

This development environment uses Docker Compose to set up multiple containers on your development machine. These containers are self-contained Linux installations with their own IP addresses within their own private network. The following containers are defined in the `docker-compose.yml`:

- **nginx:** A webserver that routes traffic between frontend and backend. This runs on port 80 in the container, which is mapped to port 9090 on your development machine (the host). Any traffic it receives at `/api` will be routed to the **backend** server, and all other traffic will be routed to the **frontend** server.
- **frontend:** A React development server running with Vite. It has the `frontend/` folder in this repository mapped to its own `/app` directory, enabling live reloading during development.
- **backend:** A Node.js Express server. It has the `backend/` folder mapped to its own `/app` directory.
- **db:** A MySQL instance used by **backend** for database storage.

The `frontend/` and `backend/` folders in this repository are git submodules and must be initialized as such. Since they are mapped to filesystem locations on the Docker containers, any changes you make in these local folders will be immediately reflected on the Docker container, providing a seamless development experience.

### Installation

```bash
git clone git@github.com:stevenmoon/personal-portfolio-websuite.git --recurse-submodules
```

### Starting the Development Environment

```bash
docker-compose up
```

You can then access:
- Frontend: http://localhost:9090
- Backend API (via Nginx): http://localhost:9090/api
- Backend API (direct access): http://localhost:3000

## 📋 Main Features

- **Modern Portfolio Showcase**: Display projects, skills, and personal information
- **Blog System**: Create and share articles and insights
- **Secure Authentication**: JWT-based authentication and role-based access control
- **Admin Dashboard**: Manage content, blog posts, and projects
- **Responsive Design**: Works across all devices and screen sizes
- **API Integration**: Structured API for all data operations
- **Neumorphic UI**: Soft, elegant user interface with subtle shadows and transitions

## 🛠️ Technology Stack

- **Frontend**:
  - React 18+ with TypeScript
  - Vite for fast builds
  - TailwindCSS for styling
  - shadcn/ui components
  - React Router for navigation

- **Backend**:
  - Node.js with Express
  - Sequelize ORM
  - MySQL database
  - JWT authentication
  - Structured API endpoints

## 🚀 Getting Started

The project is split into two parts, each with its own setup process:

### Frontend Setup

For detailed frontend setup instructions, see the [Frontend README](/frontend/README.md).

### Backend Setup

For detailed backend setup and API documentation, see the [Backend README](/backend/README.md).

### Docker Setup

You can also run the entire application using Docker, which sets up both the frontend and backend with a single command:

#### Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop/) 
- [Docker Compose](https://docs.docker.com/compose/install/) (usually included with Docker Desktop)

#### Running with Docker Compose

1. **Start the application**:
   ```bash
   docker-compose up
   ```
   This command will build and start all services defined in the docker-compose.yml file.

2. **Start in detached mode** (run in background):
   ```bash
   docker-compose up -d
   ```

3. **Stop the application**:
   ```bash
   docker-compose down
   ```

4. **Rebuild containers** (after making changes to Dockerfiles):
   ```bash
   docker-compose up --build
   ```

5. **View logs**:
   ```bash
   docker-compose logs
   ```
   
   Or for a specific service:
   ```bash
   docker-compose logs frontend
   ```

#### Accessing the Application

- Frontend: http://localhost:9090
- Backend API (via Nginx): http://localhost:9090/api
- Backend API (direct access): http://localhost:3000
- Database (MySQL): localhost:3306

#### Database Initialization

When you first start the application with Docker Compose, the system will:

1. Set up the MySQL database with the required schema
2. Run seeders to populate the database with sample data including:
   - Admin user
   - Site settings
   - Home page content
   - About page with work experience, education, and skills
   - Sample projects and tags
   - Blog posts and categories
   - Contact information

This process happens automatically when the containers start up. You'll see seeding logs in the backend container output.

If you need to manually re-seed the database:

```bash
# Access the backend container
docker-compose exec backend sh

# Run the seeders script
node src/scripts/run-seeders.js

# Exit the container
exit
```

#### Environment Variables

You can customize the setup by setting these environment variables:
- `HOST_PORT`: The port to access the frontend application via Nginx (default: 9090)
- `API_PORT`: The port to access the backend API directly (default: 3000)
- `HOST_DB_PORT`: The port to access the database from the host (default: 3306)

Example:
```bash
HOST_PORT=8000 API_PORT=4000 docker-compose up
```

#### Connecting External Tools

- **API Testing Tools (like RapidAPI)**: Connect to http://localhost:3000
- **Database Tools (like Navicat)**:
  - Host: localhost
  - Port: 3306
  - User: portfolio_user
  - Password: portfolio_password
  - Database: portfolio_db

## 🧩 Project Structure

```
.
├── .cursorrules            # Root-level Cursor Rules for AI
├── frontend/               # React TypeScript frontend application
│   ├── public/             # Static assets
│   ├── src/                # Source code
│   ├── .cursorrules        # Frontend-specific Cursor Rules
│   └── README.md           # Frontend documentation
├── backend/                # Node.js Express backend API
│   ├── src/                # Source code
│   ├── scripts/            # Utility scripts
│   ├── .cursorrules        # Backend-specific Cursor Rules
│   └── README.md           # Backend documentation
├── documents/              # Project documentation
└── README.md               # This file
```

## 🤖 Cursor Rules for AI

This project uses Cursor's Rules for AI feature to maintain consistent coding standards, architecture, and development practices. The rules are structured in a hierarchical way:

- **Root-level `.cursor`**: Project-wide guidelines and references to component rules
- **`/frontend/.cursorrulesrulesrulesrulesrulesrules`**: Frontend development rules for React, TypeScript, and UI
- **`/backend/.cursorrules`**: Backend rules for Express, Sequelize, and API design

These rules help ensure consistency across the codebase and guide AI assistants in following project conventions. For more information, see:

- [Root-level Cursor Rules](/.cursorrules)
- [Frontend Cursor Rules](/frontend/.cursorrules)
- [Backend Cursor Rules](/backend/.cursorrules)

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgements

- [React](https://react.dev/)
- [Express.js](https://expressjs.com/)
- [Sequelize ORM](https://sequelize.org/)
- [TailwindCSS](https://tailwindcss.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [Vite](https://vitejs.dev/)
- [MySQL](https://www.mysql.com/)
- [JWT](https://jwt.io/)
- [Cursor](https://cursor.com/)

---

Created with ❤️ by [Steve Moon]
