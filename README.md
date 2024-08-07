# Notes
Notes For Quick Reminders

# Table of Content
1. [Vite](#Vite)
2. [Markdown](#Markdown)
3. [Ports](#Ports)
4. [Docker](#Docker)

<!-----------------------------------------------------  -->

# <a name="Vite">1. Vite</a>

<details>
<Summary>How to Setup with VITE</Summary>


```bash
    npm create vite@latest
```
- Follow on screen instructions. 
- If you already created a folder for project, leave project name empty. 
- Select what you need from displayed list.

</details>

<!-- ---------------------------------------------------- -->

# <a name="Markdown">2. Markdown</a>

<details>
<Summary>Table of Contents Link</Summary>
 
```bash
[placeholder](#MyTitle)
```
```bash
<a name="MyTitle">MyTitle</a>
```

</details>
<!-- ---------------------------------------------------- -->

# <a name="Ports">3. Ports</a>

<details>
<Summary>Port List and Kill a Specific Port Process</Summary>
 
```bash
netstat -ano | findstr :<port_number>
OUTPUT: TCP    0.0.0.0:<port_number>       0.0.0.0:0              LISTENING       <PID>
```
```bash
taskkill /PID <PID> /F
```

</details>

<!-- ---------------------------------------------------- -->

# <a name="Docker">4. Docker</a>

<details>
<Summary>Docker Commands</Summary>
 
**ebuild and restart your Docker containers From Docker Compose file**
```bash
docker-compose down
```
```bash
docker-compose up --build
```
</details>
<!-- =========================================== -->
<details>
<Summary>Docker file templates</Summary>
 
**Docker Compose Yml**
```bash
version: '3.9'

services:
  admin:
    build:
      context: ./client/Admins
    ports:
      - "8081:8080"
    depends_on:
      - server
    environment:
      - REACT_APP_API_URL=http://server:3006
    env_file:
      - .env

  customer:
    build:
      context: ./client/Customers
    ports:
      - "8082:8080"
    depends_on:
      - server
    environment:
      - REACT_APP_API_URL=http://server:3006
    env_file:
      - .env

  user:
    build:
      context: ./client/Users
    ports:
      - "8083:8080"
    depends_on:
      - server
    environment:
      - REACT_APP_API_URL=http://server:3006
    env_file:
      - .env

  server:
    build:
      context: ./server
    ports:
      - "3006:3006"
    environment:
      - DB_HOST=${DB_HOST}
      - DB_NAME=${DB_NAME}
      - DB_USER=${DB_USER}
      - DB_PASSWORD=${DB_PASSWORD}
      - JWT_SECRET=${JWT_SECRET}
      - PORT=${PORT}
    env_file:
      - .env
```
**Note: Set .evn at Root**

**Docker File Template**

```bash 

# Use the official Node.js 20 alpine image as a base
FROM node:20-alpine

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Vite app
RUN npm run build

# Expose port 8080
EXPOSE 8080

# Command to run the application with --host flag
CMD ["npm", "run", "preview", "--", "--host", "0.0.0.0"]

```

</details>