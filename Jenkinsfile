pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker Image'
                sh 'docker build -t my-app-image:latest ./app'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application'
                // Aquí puedes agregar comandos para el despliegue, por ejemplo:
                // sh 'docker run -d -p 5000:5000 my-app-image:latest'
            }
        }
    }
}

