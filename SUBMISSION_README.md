## Multi-Container Docker Application with CI/CD: Calculator App Project

#### Complete Project Instructions: [DevOps Foundations Course/Project](https://github.com/shiftkey-labs/DevOps-Foundations-Course/tree/master/Project)

#### Submission by - Tata Abule Othow 

### Project Overview

- **Brief project description:** What is the purpose of your application?

The application is designed to perform basic calculations. The backend, implemented in Python, handles the core calculation logic. The frontend, built with Node.js, React, provides an interactive web interface for users to input values and view results.

The deployment and management of the application, Dockerfiles are created for both the frontend and backend services. These Dockerfiles specify the environment and dependencies required to run each service.

A Docker Compose YAML file is used to orchestrate the deployment of both services as a single unit. This simplifies the process of starting, stopping, and scaling the application.

Finally, a GitHub Actions YAML file is used to automate the build, test, and deployment process. This file defines the steps involved in building the Docker images, running tests, and pushing the images to a container registry.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

- **Which files are you implmenting? and why?:**

Frontend Dockerfile: create instructions to build a Docker image for the frontend service,
Backend Dockerfile: create instructions to build a Docker image for the backend service.
docker compose yaml file: Defines the services (frontend and backend) and their configurations for a multi-container Docker application.
github yaml file: Defines the CI/CD pipeline for automating the build, test, and deployment process.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

- _**Any other explanations for personal note taking.**_

<!-- Include explanation here -->
<!-- Include explanation here -->
<!-- Include explanation here -->
<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

### Docker Implementation

**Explain your Dockerfiles:**

- **Backend Dockerfile** (Python API):
  - Here please explain the `Dockerfile` created for the Python Backend API.
  - This can be a simple explanation which serves as a reference guide, or revision to you when read back the readme in future.

This Dockerfile is used to build a Docker image containing the Python backend application and its dependencies, the base image used python 3.9-slim-buster

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

- **Frontend Dockerfile** (React App):
  - Similar to the above section, please explain the Dockerfile created for the React Frontend Web Application.

Dockerfile used to build a Docker image containing the React frontend application and its dependencies. It ensures a consistent environment for the frontend, making it portable and reproducible. Example node.js is a base image which provides the necessary Node.js environment to run the React application.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

**Use this section to document your choices and steps for building the Docker images.**

### Docker Compose YAML Configuration

**Break down your `docker-compose.yml` file:**

- **Services:** List the services defined. What do they represent?
- **Networking:** How do the services communicate with each other?
- **Volumes:** Did you use any volume mounts for persistent data?
- **Environment Variables:** Did you define any environment variables for configuration?

**Use this section to explain how your services interact and are configured within `docker-compose.yml`.**

Services:
Example frontend and backend represent a service container with its own image, build, and port.

frontend: This service represents the frontend application. It's built from the local . directory using the specified Dockerfile. Port 3000 on the host machine is mapped to port 3000 inside the container, making the frontend accessible at localhost:3000.

backend: This service represents the backend application. It's also built from the local . directory using the specified Dockerfile. Port 6000 on the host machine is mapped to the corresponding port inside the container, making the backend accessible at localhost:6000.

network -I am using the default (bridge) network, as I didn't specify a custom one. This means the default network allows services like the frontend and backend to communicate with each other within Docker compose environment.

volumes - i did't define volumes in my Docker compose which is away to store data genereated by container, If I need to store data persistently, I can add volume definitions to services.

evnironment variable - I didn't define any evnironment variable, which can be used to configure services without modifying the container image. They can be useful for setting sensitive information for example my Docker Hub credentials. which I applied evnironment variable on to access my Docker account.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

### CI/CD Pipeline (YAML Configuration)

**Explain your CI/CD pipeline:**

- What triggers the pipeline (e.g., push to main branch)?
- What are the different stages (build, test, deploy)?
- How are Docker images built and pushed to a registry (if applicable)?

**Use this section to document your automated build and deployment process.**

what triggers the pipline is the push and pull_request to my main branch, this makes sure that code changes is reflected
in the CI/CD,
stages:
build - the frontend Builds the React frontend application into a production-ready bundle,this goes for the backend builds the python backend application into a Docker image.
test - runs test for backend, (I didn't do it for frontend)
deploy - Pushes the Docker images to a container registry (docker pull tataothow101/backend) (docker pull tataothow101/frontend)

Dockerfile: Each service (frontend and backend) has its own Dockerfile, which defines the environment and dependencies required to build the image. Docker build used to build the Docker images based on the Dockerfiles. docker push command is used to push the built images to a container registry.
The CI/CD pipeline automates the process of building, testing, and deploying the Docker images. It triggers the build and push steps whenever changes are pushed to the repository.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

### CI/CD Pipeline (YAML Configuration)

**Simply explain your CI/CD pipeline:**

- What triggers the pipeline (e.g., push to main branch)?
- What are the different stages (build, test, deploy)?
- How are Docker images built and pushed to a registry?

**Use this section to document your automated build, and docker process.**

<!-- Include explanation here -->
<!-- Include explanation here -->
<!-- Include explanation here -->
<!-- Include explanation here -->
<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

### Assumptions

- List any assumptions you made while creating the Dockerfiles, `docker-compose.yml`, or CI/CD pipeline.

I assumed that you would need to explicitly define a network in your docker-compose.yml file to enable communication between the frontend and backend services. However, it seems that the default Docker Compose network was sufficient.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

### Lessons Learned

- What challenges did you encounter while working with Docker and CI/CD?
- What did you learn about containerization and automation?

**Use this section to reflect on your experience and learnings when implementing this project.**

One challenge I faced was related to port configuration and container building. Occasionally, my container's localhost wouldn’t work, and I had to rebuild the container to fix the port settings. This process was necessary to ensure I could use Postman to test my backend properly.

Through this project, I gained a deeper understanding of containerization and how it simplifies application deployment by ensuring consistency across environments. I also learned how automation, especially with CI/CD pipelines, can streamline the development process and reduce manual errors.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

### Future Improvements

- How could you improve your Dockerfiles, `docker-compose.yml`, or CI/CD pipeline?
- (Optional-Just for personal reflection) Are there any additional functionalities you would like to consider for the calculator application to crate more stages in the CI/CD pipeline or add additional configuration in the Dockerfiles?

**Use this section to brainstorm ways to enhance your project.**

In the future, I plan to enhance the project by incorporating network configuration and volumes to better manage data persistence and inter-container communication.

I might also add new features, such as a Pi calculation functionality, to make the application more interactive and showcase additional capabilities. I would also include more test cases for frontend.

<!-- NOTE: It is not compulsory to include detailed explanations, writing succint concise points would also sufice. Make sure maintain readability and clarity. -->

<!-- BEST OF LUCK! -->
