# Notes
Notes For Quick Reminders

# Table of Content
1. [Vite](#Vite)
2. [Markdown](#Markdown)
3. [Ports](#Ports)
4. [Docker](#Docker)
5. [Java](#Java)
6. [Linux](#Linux)


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
<Summary>Images Commands</Summary>
 
- Build an Image from a Dockerfile
```bash
docker build -t <image_name>
```

- Build an Image from a Dockerfile without the cache
```bash
docker build -t <image_name> . –no-cache
```

- List local images
```bash
docker images
```
- Delete an Image
```bash
docker rmi <image_name>
```

- Remove all unused images
```bash
docker image prune 
```
</details>
<details>
<Summary>Compose Commands</Summary>
- Starts existing containers for a service.

```bash
docker-compose start
```

- Stops running containers without removing them.
```bash
docker-compose stop
```

- Pauses running containers of a service.
```bash
docker-compose pause
```

- Unpauses paused containers of a service.
```bash
docker-compose unpause
```

- Lists containers.
```bash
docker-compose ps 
```
- Rebuild and restart your Docker containers From Docker Compose file**
```bash
docker-compose down
```
```bash
docker-compose up --build
```

</details>
<details>
<Summary>DockerHub Commands</Summary>
 
- Login into Docker
```bash
docker login -u <username>
```

- Publish an image to Docker Hub
```bash
docker push <username>/<image_name>
```

- Search Hub for an image
```bash
docker search <image_name>
```

- Pull an image from a Docker Hub
```bash
docker pull <image_name>
```

</details>
<details>
<Summary>Container Commands</Summary>
 
- Create and run a container from an image, with a custom name:
```bash
docker run --name <container_name> <image_name>
```
- Run a container with and publish a container’s port(s) to the host.
```bash
docker run -p <host_port>:<container_port> <image_name>
```

- Run a container in the background
```bash
docker run -d <image_name>
```

- Start or stop an existing container:
```bash
docker start|stop <container_name> (or <container-id>)
```

- Remove a stopped container:
```bash
docker rm <container_name>
```

- Open a shell inside a running container:
```bash
docker exec -it <container_name> sh
```

- Fetch and follow the logs of a container:
```bash
docker logs -f <container_name>
```

- To inspect a running container:
```bash
docker inspect <container_name> (or <container_id>)
```

- To list currently running containers:
```bash
docker ps
```

- List all docker containers (running and stopped):
```bash
docker ps --all
```

- View resource usage stats
```bash
docker container stats
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

<!-----------------------------------------------------  -->

# <a name="Java">5. Java</a>

<details>
<Summary>Commands</Summary>

- Checking JDK verion
```bash
  javac --version
```
- Checking Run Time Env verion
```bash
  java --version
```


</details>

<!-- ---------------------------------------------------- -->
# <a name="Linux">6. Linux</a>

<details>
<Summary>1. File and Directory Operations Commands</Summary>

- flags
```bash
  -f: force 
  -r: recursively
  -n: number of lines 
```
- Print current working directory.
```bash
  pwd
```
- Remove files and directories.
```bash
  rm
```
- Search for files and directories.
```bash
  find 
  e.g. find /path/to/search -name “*.txt” 
```
- Create an empty file
```bash
  touch
```
- Read File Content
```bash
  cat
```
- copy move
```bash
  cp
  mv
```
-used to search for specific patterns or regular expressions in text files or streams and display matching lines.
```bash
  grep

  -i: Ignore case distinctions while searching.
  -v: Invert the match, displaying non-matching lines.
  -r or -R: Recursively search directories for matching patterns.
  -l: Print only the names of files containing matches.
  -n: Display line numbers alongside matching lines.
  -w: Match whole words only, rather than partial matches.
  -c: Count the number of matching lines instead of displaying them.
  -e: Specify multiple patterns to search for.
  -A: Display lines after the matching line.
  -B: Display lines before the matching line.
  -C: Display lines both before and after the matching line.

  e.g.  grep -i “hello” file.txt
  grep -v “error” file.txt
  grep -r “pattern” directory/
  grep -l “keyword” file.txt
  grep -n “pattern” file.txt
```

</details>

<details>
<Summary>2. File Permission Commands</Summary>

- Change file permissions.
```bash
  chmod
  
  u: User/owner permissions.
  g: Group permissions.
  o: Other permissions.
  +: Add permissions.
  –: Remove permissions.
  =: Set permissions explicitly.

  e.g. chmod u+rwx file.txt 
```
</details>
<details>
<Summary>3. Process Management Commands</Summary>

- Display running processes.
```bash
  ps aux
```
- Monitor system processes in real-time.
```bash
  top
```
- Kill a Process
```bash
  kill <PID>
```
</details>

<details>
<Summary>4. System Information Commands</Summary>

- Print system information.
```bash
  uname
```
- Display current username.
```bash
  whoami
```
- Disk Space
```bash
  df -h 
```
- Estimate file and directory sizes.
```bash
  df -h 
  e.g. du -h directory/ 
```
- Display memory usage information.
```bash
  df -h 
  e.g. du -h directory/ 
```
- Display CPU information.
```bash
  lscpu
```
- List PCI devices.
```bash
  lspci
```
</details>

<details>
<Summary>5. Networking Commands</Summary>

- details of all network interfaces.
```bash
  ifconfig
```
- echo requests to “google.com” to check connectivity.
```bash
  ping google.com
```
- Display network connections and statistics.
```bash
  netstat
```
- Securely connect to a remote server.
```bash
  ssh user@hostname 
```
- Securely copy files between hosts.
```bash
  scp

  e.g. 
  scp file.txt user@hostname:/path/to/destination 
  securely copies “file.txt” to the specified remote host.
```
-  Download files from the web.
```bash
  wget

  e.g. 
  wget http://example.com/file.txt 
  downloads “file.txt” from the specified URL.
```
- 	Transfer data to or from a server.
```bash
  curl
  e.g.
  curl http://example.com 
  retrieves the content of a webpage from the specified URL.
```
</details>