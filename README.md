## 📦 Project: **Dockerized Node.js Web App**
* A simple **Node.js web application**
* A **Dockerfile** to containerize it
* A **docker-compose.yml** to manage services
* Instructions to build and run the container

---

### 📁 Project Structure

```
docker-node-webapp/
├── app/
│   ├── server.js
│   └── package.json
├── Dockerfile
├── .dockerignore
├── docker-compose.yml
└── README.md
```
# run on Windows 
// Open Docker Desktop 

```
# Download and install Chocolatey:
powershell -c "irm https://community.chocolatey.org/install.ps1|iex"

# Download and install Node.js:
choco install nodejs-lts --version="22"

# Verify the Node.js version:
node -v # Should print "v22.17.0".

# Verify npm version:
npm -v # Should print "10.9.2".
```
```
git clone https://github.com/atulkamble/docker-nodejs-webapp.git
cd docker-nodejs-webapp
node index.js

docker-compose build
docker-compose up
``
---
---

## 📜 Code Details

---

### 📄 `app/package.json`

```json
{
  "name": "docker-node-webapp",
  "version": "1.0.0",
  "description": "A simple Node.js app running in Docker",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

---

### 📄 `app/server.js`

```javascript
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req, res) => {
  res.send('Hello from Dockerized Node.js App 🚀');
});

app.listen(PORT, () => {
  console.log(`App listening at http://localhost:${PORT}`);
});
```

---

### 📄 `.dockerignore`

```
node_modules
npm-debug.log
```

---

### 📄 `Dockerfile`

```Dockerfile
# Use official Node.js base image
FROM node:20-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy package files and install dependencies
COPY app/package*.json ./
RUN npm install

# Copy application source
COPY app/ .

# Expose port
EXPOSE 3000

# Command to run the app
CMD [ "npm", "start" ]
```

---

### 📄 `docker-compose.yml`

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - ./app:/usr/src/app
    environment:
      - NODE_ENV=development
```

---

### 📄 `README.md` (Optional)

```markdown
# Dockerized Node.js Web Application

## 🐳 How to Run

1️⃣ Build the Docker image  
```

docker-compose build

```

2️⃣ Run the container  
```

docker-compose up

```

3️⃣ Visit the app:  
[http://localhost:3000](http://localhost:3000)

## 📦 Project Structure  
(see directory structure above)

---
```

---

## 🚀 How to Use

1️⃣ Clone the project or copy the files locally
2️⃣ Run:

```bash
docker-compose build
docker-compose up
```

3️⃣ Open your browser:

```
http://localhost:3000
```

---

## ✅ What You Learn from This

* Writing a **Dockerfile** for Node.js app
* Ignoring unnecessary files via `.dockerignore`
* Managing containers using **Docker Compose**
* Exposing container ports
* Live development via volume mounts

