 
# Flask App with MySQL Docker Setup

This is a simple Flask app that interacts with a MySQL database. The app allows users to submit messages, which are then stored in the database and displayed on the frontend.

## Prerequisites

Before you begin, make sure you have the following installed:

- Docker
- Git (optional, for cloning the repository)

## Setup

1. Clone this repository (if you haven't already):

   ```bash
   git clone git@github.com:ayushranjan828/Two-Tier-Flask-App.git
   ```

2. Build the Flask Backend Image:

   ```bash
   docker build -t two_tier_flask_backend .
   ```

3. Create a Docker Network:

   ```bash
   docker network create two-tier -d bridge
   ```

4. Verify Network:
   ```
   docker network ls
   ```

5. Pull MySQL Image:
   ```
   docker pull mysql
   ```

6. Run MySQL Container:
   ```
   docker run -d --name mysql --network two-tier -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=devops mysql
   ```

7. Run Flask Backend Container:
   ```
   docker run -d -p 5000:5000 --network two-tier -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=root -e MYSQL_DB=devops two_tier_flask_backend:latest
   ```
8.  Inspect the Docker Network:
   ```
   docker network inspect two-tier
   ```

## 🌐 Access the App
    Open your browser and go to: http://localhost:5000


## Notes

- Make sure to replace placeholders (e.g., `your_username`, `your_password`, `your_database`) with your actual MySQL configuration.

- This is a basic setup for demonstration purposes. In a production environment, you should follow best practices for security and performance.

- Be cautious when executing SQL queries directly. Validate and sanitize user inputs to prevent vulnerabilities like SQL injection.

- If you encounter issues, check Docker logs and error messages for troubleshooting.

```

