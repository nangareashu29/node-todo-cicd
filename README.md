Overview
This project is a simple Node.js todo application with continuous integration and continuous deployment (CI/CD) implemented using Jenkins. It also utilizes a webhook as a trigger for automation. The application allows you to manage your todos through a web interface.

Prerequisites
Before you can run the application, ensure that you have Node.js and npm installed on your system. If not, you can install them using the following commands:

sudo apt install nodejs
sudo apt install npm
Getting Started
Follow these steps to run the project locally:

Clone the repository:

git clone https://github.com/theyashsisodiya/node-todo-cicd.git
Navigate to the project directory:

cd node-todo-cicd
Install project dependencies:

npm install
Run the application:

node app.js
The application will be accessible at http://localhost:8000/todo.

CI/CD with Jenkins
This project includes CI/CD pipelines implemented using Jenkins. The Jenkins job is triggered automatically through a webhook whenever changes are pushed to the repository.

Jenkins Setup
Install Jenkins on your server.

Configure Jenkins with the necessary plugins, including Github integration only.

Select Git on Source Code Management.
Paste your repo link.
Add your Github credentials.
Branches to build: main if your project is on the main branch, else master or other.
Build triggers: Select "GitHub hook trigger for GITScm polling."
Execute shell script:

#!/bin/bash

# Define variables
CONTAINER_NAME=node-app-container
IMAGE_NAME=node-app-todo
PORT=8000

# Check if the port 8000 is in use and kill the process if needed
if lsof -i :$PORT; then
    echo "Port $PORT is in use, killing the process..."
    lsof -ti :$PORT | xargs kill -9
fi

# Check if the container is running
if docker ps -a --format '{{.Names}}' | grep -q $CONTAINER_NAME; then
    echo "Stopping and removing existing container..."
    docker stop $CONTAINER_NAME
    docker rm $CONTAINER_NAME
fi

# Build and run the Docker container
echo "Building and running the new container..."
docker build -t $IMAGE_NAME .
docker run -d --name $CONTAINER_NAME -p $PORT:8000 $IMAGE_NAME
Apply and save it.

Access the Deployed Application
The deployed version on AWS of this application can be accessed at [http://35.153.231.90:8000/todo]. Please note that the URL might change, so make sure to check the latest deployment URL.

Feel free to explore the application and manage your todos!

Architecture
Group

Contributing
If you would like to contribute to this project, feel free to open issues or submit pull requests. Your feedback and contributions are highly appreciated.

Happy devops learning!😄:-)# node-todo-cicd
