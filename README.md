# Introduction 

Manage my Damn Life (MMDL) is a self hosted front end for managing your CalDAV tasks and calendars.

**This project is in beta state, so be careful if you're working with production data.**

![Demo](docs/pics/screenRecord.gif)
![Task View](docs/pics/screenshots/TaskView.png "Task View")
![Home](docs/pics/screenshots/HomeView.png "Task View")
![GanttView](docs/pics/screenshots/GanttView.png "Task View")

More screenshots are available in the directory '/docs/pics/screenshots'

## Features

1. Manage your CalDAV tasks.
    - Supports sub tasks.
    - Supports many fields like due, status, description, recurrence, and more
2. Manage calendar events.  
3. Supports multiple CalDAV accounts, and multiple user accounts.
4. View your tasks as a list, in a gantt view, or on a calendar.  
1. Create and manage task filters to view your tasks as you see fit.
1. "Reponsive-ish" view. This is a desktop first project, as multiple clients like JTX Boards, OpenTasks exist for mobile.
1. OAUTH support


### Planned features

1. Support all fields for VTODO and VEVENT as described in [RFC 5545](https://www.rfc-editor.org/rfc/rfc5545).
1. More flexible ways to view tasks, and customisable views.
1. Drag and drop capability for tasks
1. Ability to create external plugins.

## Compatibility

This client has been tested with Nextcloud and Baikal.

As of now, it only supports basic authentication, and not OAUTH. 

## Getting Started

To get started, you can checkout full documentation [here](https://manage-my-damn-life-nextjs.readthedocs.io/en/latest/install/).


Here's an updated version of your README file with instructions on how to build and run your Docker container:

---

# Introduction

Manage my Damn Life (MMDL) is a self-hosted front-end for managing your CalDAV tasks and calendars.

**This project is in beta state, so be careful if you're working with production data.**

![Demo](docs/pics/screenRecord.gif)
![Task View](docs/pics/screenshots/TaskView.png "Task View")
![Home](docs/pics/screenshots/HomeView.png "Home View")
![GanttView](docs/pics/screenshots/GanttView.png "Gantt View")

More screenshots are available in the directory '/docs/pics/screenshots'

## Features

1. Manage your CalDAV tasks.
    - Supports sub tasks.
    - Supports many fields like due, status, description, recurrence, and more.
2. Manage calendar events.
3. Supports multiple CalDAV accounts and multiple user accounts.
4. View your tasks as a list, in a Gantt view, or on a calendar.
5. Create and manage task filters to view your tasks as you see fit.
6. "Responsive-ish" view. This is a desktop-first project, as multiple clients like JTX Boards, OpenTasks exist for mobile.
7. OAUTH support.

### Planned Features

1. Support all fields for VTODO and VEVENT as described in [RFC 5545](https://www.rfc-editor.org/rfc/rfc5545).
2. More flexible ways to view tasks and customizable views.
3. Drag-and-drop capability for tasks.
4. Ability to create external plugins.

## Compatibility

This client has been tested with Nextcloud and Baikal.

As of now, it only supports basic authentication, and not OAUTH.

## Getting Started

To get started, you can check out full documentation [here](https://manage-my-damn-life-nextjs.readthedocs.io/en/latest/install/).

## Docker Instructions
1. Prerequisites
Ensure that you have Docker installed on your system. You can install Docker by following the instructions here.

2. Building the Docker Image
In order to containerize the MMDL application, follow these steps to build the Docker image:

Clone the repository:

bash
Copy code
git clone https://github.com/your-repo/manage-my-damn-life.git
cd manage-my-damn-life
Create a Dockerfile in the root directory (if it’s not already present), with instructions on how to build the Docker image. Example Dockerfile:

dockerfile
Copy code
# Use an official Node.js runtime as the base image
FROM node:16

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json into the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Expose the port your app runs on (adjust based on your app's port)
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
Build the Docker image:

bash
Copy code
```
docker build -t previously-made-app .
```
This command will create a Docker image with the name mmdl-app.

3. Running the Docker Container
Once the image is built, you can run your application inside a Docker container.

Run the container:

bash
Copy code
```
docker run -d -p 3000:3000 previously-made-app
```
-d runs the container in detached mode (in the background).
-p 3000:3000 maps port 3000 of the container to port 3000 on your local machine. Make sure this matches the port your app listens on.

You can now access the application by visiting http://localhost:3000 in your browser.

4. Stopping the Docker Container
To stop the running container, you can use:

bash
Copy code
```
docker stop <container_id>
```
You can find the container ID by running:

bash
Copy code
```
docker ps
```
5. Using Docker Compose (Optional)
If you want to use Docker Compose (especially if your app requires other services like a database), you can create a docker-compose.yml file.

Example docker-compose.yml:


Copy code
```
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/usr/src/app
```
To start the application using Docker Compose:

bash
Copy code
```
docker-compose up
```