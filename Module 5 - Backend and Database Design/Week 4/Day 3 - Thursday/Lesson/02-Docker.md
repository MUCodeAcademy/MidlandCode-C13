# Docker

## How can Docker help in development?

- The main point is consistent functionality.
- Standardization of applications is huge during the entirety of the dev lifecycle.
- Massively speeds up deployment.
- Allows for consistency across environments to allow for continuous deployment and testing.
- Segregation and Security. By having everything contained (literally) in it's own space it reduces cross contamination of any malicious code / security vulnerabilities that might exist on a non containerized application

## Step By Step Guide

0. Install [Docker Desktop](https://www.docker.com/products/docker-desktop).
1. Create Dockerfiles for each part of your app (such as Dockerfile.frontend, Dockerfile.backend).
2. In each one, define some configurations for that section.
3. Create a docker-compose.yml file. This will be used to build your app.
4. Run `docker-compose build`.
5. Start the containers using `docker-compose up -d`. The -d is for running it in the background and is optional.
6. (optional) If you have errors while running this, try following the instructions, and run `docker-compose down`, then `docker-compose up -d` again.
7. Check the status of your containers using `docker-compose ps`. This will show you if the containers are running properly.
8. Open a web browser and navigate to `http://localhost:3000`. This should load your frontend application if it's set up correctly.
9. Test the backend. You can use tools like Postman or CURL to make requests to `http://localhost:3006` (or whatever port your server is running on) and verify the responses.

## More Advanced Development with Docker

There are plenty more options and a ton of great resources on the docs for docker. I would recommend taking a look at a lot of their stuff to see what all you can do.
