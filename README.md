# Wanderlust - Your Ultimate Travel Blog 🌍✈️

WanderLust is a simple MERN travel blog website ✈ This project is aimed to help people to contribute in open source, upskill in react and also master git.

![Preview Image](https://github.com/krishnaacharyaa/wanderlust/assets/116620586/17ba9da6-225f-481d-87c0-5d5a010a9538)

## [Figma Design File](https://www.figma.com/file/zqNcWGGKBo5Q2TwwVgR6G5/WanderLust--A-Travel-Blog-App?type=design&node-id=0%3A1&mode=design&t=c4oCG8N1Fjf7pxTt-1)
## [Discord Channel](https://discord.gg/FEKasAdCrG)

## 🎯 Goal of this project

At its core, this project embodies two important aims:

1. **Start Your Open Source Journey**: It's aimed to kickstart your open-source journey. Here, you'll learn the basics of Git and get a solid grip on the MERN stack and I strongly believe that learning and building should go hand in hand.
2. **React Mastery**: Once you've got the basics down, a whole new adventure begins of mastering React. This project covers everything, from simple form validation to advanced performance enhancements. And I've planned much more cool stuff to add in the near future if the project hits more number of contributors.

_I'd love for you to make the most of this project - it's all about learning, helping, and growing in the open-source world._

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- Docker (v20.10+)
- Docker Compose (v2.0+)
- Git

## 🚀 Quick Start (Using Docker)

1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/wanderlust.git
   cd wanderlust
   ```

2. **Start the Application**
   ```bash
   docker-compose up --build
   ```

3. **Access the Application**
   - Frontend: http://localhost:7500
   - Backend API: http://localhost:5000
   - MongoDB: mongodb://localhost:27017

4. **Import Sample Data** (Optional)
   ```bash
   # Copy sample data to MongoDB container
   docker cp ./backend/data/sample_posts.json $(docker-compose ps -q database):/sample_posts.json
   ```

# Import the data
docker-compose exec database mongoimport --db wanderlust --collection posts --file /sample_posts.json --jsonArray


That's it! 🎉 Your Wanderlust application is now running.

## Setting up the project locally

### Setting up the Backend

1. **Fork and Clone the Repository**

   ```bash
   git clone https://github.com/{your-username}/wanderlust.git
   ```

2. **Navigate to the Backend Directory**

   ```bash
   cd backend
   ```

3. **Install Required Dependencies**

   ```bash
   npm i
   ```

4. **Set up your MongoDB Database**

   - Open MongoDB Compass and connect MongoDB locally at `mongodb://localhost:27017`.

5. **Import sample data**

   > To populate the database with sample posts, you can copy the content from the `backend/data/sample_posts.json` file and insert it as a document in the `wanderlust/posts` collection in your local MongoDB database using either MongoDB Compass or `mongoimport`.

   ```bash
   mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray
   ```

6. **Configure Environment Variables**

   ```bash
   cp .env.sample .env
   ```

7. **Start the Backend Server**

   ```bash
   npm start
   ```

   > You should see the following on your terminal output on successful setup.
   >
   > ```bash
   > [BACKEND] Server is running on port 5000
   > [BACKEND] Database connected: mongodb://127.0.0.1/wanderlust
   > ```

### Setting up the Frontend

1. **Open a New Terminal**

   ```bash
   cd frontend
   ```

2. **Install Dependencies**

   ```bash
   npm i
   ```

3. **Configure Environment Variables**

   ```bash
   cp .env.sample .env.local
   ```

4. **Launch the Development Server**

   ```bash
   ```bash
   npm run dev
   ```

   ## 📁 Project Structure
   ```
   wanderlust/
   ├── 📁 backend/              # Node.js API server
   │   ├── 🐳 Dockerfile        # Backend container config
   │   ├── 📄 package.json      # Dependencies
   │   ├── 🚀 server.js         # Entry point
   │   └── 📁 data/
   │       └── 📄 sample_posts.json
   ├── 📁 frontend/             # React application  
   │   ├── 🐳 Dockerfile        # Frontend container config
   │   ├── ⚙️ nginx.conf        # Nginx configuration
   │   ├── 📄 package.json      # Dependencies
   │   └── 📁 src/
   ├── 🐳 docker-compose.yml    # Multi-container setup
   ├── 📄 .env                  # Environment variables
   └── 📖 README.md            # This file
   ```
   ```

   ## 🏗️ Project Architecture

   ### Docker Components Overview
   - **Frontend Container**: React application served via Nginx on port 7500
   - **Backend Container**: Node.js API service running on port 5000
   - **Database Container**: MongoDB instance on default port 27017

   ### Network Communication
   All containers are networked together using Docker Compose, enabling seamless internal communication while maintaining isolation. External access is provided through mapped ports.

## 🐳 Docker Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │    Backend      │    │    Database     │
│   (React+Nginx) │    │   (Node.js)     │    │   (MongoDB)     │
│   Port: 7500    │◄──►│   Port: 5000    │◄──►│   Port: 27017   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```


## ⚙️ Configuration

### Environment Variables
Create a `.env` file in the root directory:

```env
# Database Configuration
MONGODB_URI=mongodb://database:27017/wanderlust

# Backend Configuration
NODE_ENV=production
PORT=5000

# Frontend Configuration
VITE_API_URL=/api
```

### Port Configuration

| Service  | Container Port | Host Port | URL |
|----------|---------------|-----------|-----|
| Frontend | 80 | 7500 | http://localhost:7500 |
| Backend | 5000 | 5000 | http://localhost:5000 |
| MongoDB | 27017 | 27017 | mongodb://localhost:27017 |

## 🔧 Development

### Available Commands

```bash
# 🚀 Start all services
docker-compose up

# 🔨 Build and start (after code changes)
docker-compose up --build

# 🕰️ Run in background
docker-compose up -d

# 📊 View logs
docker-compose logs -f

# 🔄 Restart specific service
docker-compose restart backend

# 🛑 Stop all services
docker-compose down

# 🗑️ Clean up (removes volumes/data)
docker-compose down -v
```


