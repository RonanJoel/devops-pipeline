# 🚀 CI/CD Pipeline with Jenkins and Docker

## 💡 Description

This project demonstrates how to build and deploy a **Continuous Integration (CI)** and **Continuous Delivery (CD)** pipeline using **Jenkins** and **Docker**. It automates the process of building, testing, and deploying applications to various environments. The pipeline is designed to show how to create an automated workflow from development to deployment using Jenkins and Docker containers.

## 🛠️ Technologies

- **Jenkins**: 🤖 Automation server to run the CI/CD pipeline.
- **Docker**: 🐳 Containerization technology for building, running, and deploying applications.
- **GitHub Actions**: 🔄 Optional integration with GitHub for continuous integration.
- **Git**: 📂 Version control system for source code management.
- **Jenkinsfile**: 📝 Script to define the stages of the CI/CD pipeline.

## 🎯 Objective

The goal of this project is to implement a robust, automated pipeline for building and deploying a simple web application. The pipeline runs in Jenkins, uses Docker for containerization, and can be easily extended to support more complex workflows.

## 📁 Repository Structure

/ci-cd-pipeline/ ├── jenkins/ │ ├── Dockerfile # 🐳 Dockerfile to set up Jenkins environment │ ├── jenkinsfile # 📝 Jenkins pipeline definition file ├── app/ │ └── Dockerfile # 🐳 Dockerfile for the application ├── requirements.txt # 📄 Python dependencies for the app ├── .env # 🌍 Environment variables (credentials, secrets) ├── README.md # 📑 Project documentation └── Jenkinsfile # 📝 Jenkins pipeline script (root directory)


## ⚙️ Steps to Set Up the Project

### 1. Clone the Repository

First, clone the repository to your local machine:

```
git clone https://github.com/RonanJoel/devops-pipeline.git
cd devops-pipeline
```

2. Install Docker

Ensure Docker is installed on your machine. To check if Docker is installed, run:

```
docker --version
```

If Docker is not installed, follow the official installation guide for your operating system:

    Install Docker on Linux
    Install Docker on macOS
    Install Docker on Windows

3. Install Jenkins

If Jenkins is not installed, follow the instructions to install Jenkins:

    Install Jenkins on Ubuntu
    Install Jenkins on macOS
    Install Jenkins on Windows

Start Jenkins once installed and ensure it’s accessible via http://localhost:8080.
4. Configure Jenkins for Docker

You need to configure Jenkins to interact with Docker:

    Install the Docker plugin in Jenkins from the Manage Jenkins > Manage Plugins section.
    Add your Docker credentials to Jenkins under Manage Jenkins > Manage Credentials (if using a private Docker registry).

5. Running Jenkins

If Jenkins is running in Docker, use the following command to start it:

```
docker run -d -p 8080:8080 -p 50000:50000 --name jenkins jenkins/jenkins:lts
```

Once Jenkins is up and running, open your browser and navigate to http://localhost:8080.
6. Configuring the Pipeline in Jenkins

    Create a New Jenkins Pipeline:
        In Jenkins, click New Item, name your project, and select Pipeline.
        Under Pipeline Definition, select Pipeline script from SCM and configure it to pull from your GitHub repository.
        Set the Script Path to Jenkinsfile if it’s in the root of your repository.

    Configure GitHub Integration:
        Provide the repository URL (e.g., https://github.com/RonanJoel/devops-pipeline.git).
        If necessary, configure credentials for accessing GitHub.

7. Build and Deploy Process

Once the pipeline is configured, you can trigger the build manually by clicking Build Now in Jenkins.

The pipeline will perform the following steps:

    Build the application Docker image using the app/Dockerfile.
    Run tests (if tests are defined in the project).
    Push the Docker image to a container registry (Docker Hub or private registry).
    Deploy the application to your chosen environment.

You can monitor the process through Jenkins’s Console Output.
8. Customizing the Pipeline

You can modify the Jenkinsfile to add more stages or modify the existing stages:

    Build: Customize the Docker build process.
    Test: Add unit tests, integration tests, etc.
    Deploy: Add deployment steps for your specific environment (e.g., deploy to AWS, Azure, or a local server).

Example stages in Jenkinsfile:

```
pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'myapp'
        REGISTRY = 'docker.io'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }
        stage('Test') {
            steps {
                // Run your tests here
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
                        docker.image(DOCKER_IMAGE).push()
                    }
                }
            }
        }
    }
}
```
9. Verify Deployment

Once the pipeline runs successfully, you can verify the deployment:

    If it’s a web application, open your browser and navigate to http://localhost:PORT (replace PORT with the port you’ve configured for your Docker container).
    Check if the application is running as expected.

10. Monitoring and Debugging

To debug and monitor the pipeline execution:

    Check Jenkins’s Console Output for detailed logs of each step.
    For Docker, use docker ps to list running containers and docker logs <container_id> to view logs for the container.

🎉 Conclusion

This project sets up a CI/CD pipeline using Jenkins and Docker, automating the process of building, testing, and deploying applications. You can extend this pipeline to include additional tools and environments based on your needs.
🤝 Contributing

Feel free to fork the repository, open issues, and submit pull requests. Contributions are always welcome!
📜 License

This project is licensed under the MIT License - see the LICENSE file for details.
