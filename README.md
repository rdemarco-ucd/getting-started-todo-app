# Getting Started Todo App

This project provides a sample todo list application. It demonstrates all of
the current Docker best practices, ranging from the Compose file, to the
Dockerfile, to CI (using GitHub Actions), and running tests. It's intended to 
be a well-documented to ensure anyone can come in and easily learn.

## Application architecture

![image](https://github.com/docker/getting-started-todo-app/assets/313480/c128b8e4-366f-4b6f-ad73-08e6652b7c4d)


This sample application is a simple React frontend that receives data from a
Node.js backend. 

When the application is packaged and shipped, the frontend is compiled into
static HTML, CSS, and JS and then bundled with the backend where it is then
served as static assets. So no... there is no server-side rendering going on
with this sample app.

During development, since the backend and frontend need different dev tools, 
they are split into two separate services. This allows [Vite](https://vitejs.dev/) 
to manage the React app while [nodemon](https://nodemon.io/) works with the 
backend. With containers, it's easy to separate the development needs!

## Development

To spin up the project, simply install Docker Desktop and then run the following 
commands:

```
git clone https://github.com/docker/getting-started-todo-app
cd getting-started-todo-app
docker compose up --watch
```

You'll see several container images get downloaded from Docker Hub and, after a
moment, the application will be up and running! No need to install or configure
anything on your machine!

Simply open to [http://localhost](http://localhost) to see the app up and running!

Any changes made to either the backend or frontend should be seen immediately
without needing to rebuild or restart the containers.

To help with the database, the development stack also includes phpMyAdmin, which
can be access at [http://db.localhost](http://db.localhost) (most browsers will 
resolve `*.localhost` correctly, so no hosts file changes should be required).

### Tearing it down

When you're done, simply remove the containers by running the following command:

```
docker compose down
```

## Build and push your first image
Once you've updated the to-do list app, you're ready to create a container image for the application and share it on Docker Hub. To do so, you will need to do the following:
1. Sign in with your Docker account
2. Create an image repository on Docker Hub
3. Build the container image
4. Push the image to Docker Hub

### Sign in with your Docker account
1. Open Docker dashboard.
2. Select Sign-in at the top-right corner
3. If needed, create an account and then complete the sign-in flow.

### Create an image reposigory
Just as a Git repository holds source code, an image repository stores container images.
1. Make sure you're signed into Docker Hub
2. Select Create repository
3. On the create repository page, enter the following information:
    - Repository name - ```getting-started-todo-app```
    - Short discription
    - Visibility - select Public to allow others to pull your customized to-do app
4. Select Create to create the repository

### Build and push the image
VS Code:
1. Open VS Code and endure you have the Docker extention installed
2. Clone the repository of the to-do application if you haven't already
3. Right-click the ```Dockerfile``` and select the Build Image... menu item
4. in the dialogue that appears, enter a name of ```DOCKER_USERNAME/getting-started-todo-app```, replacing with your Docker username
5. After pressing Enter, you will see a terminal appear where the build will occur.
6. Open the Docker Extension for VS Code by selecting the Docker logo in the left nav menu
7. Find the image you created. It'll have the name of ```docker.io/DOCKER_USERNAME/getting-started-todo-app.```
8. Expand the image to view the different tags (versions) of the image. The default tag given to an image is ```latest```.
9. Right-click on the latest item and select the Push... option
10. Press Enter to confirm and then watch as your image is pushed to Docker Hub.