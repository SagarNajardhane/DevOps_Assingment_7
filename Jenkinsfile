pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                credentialsId: 'github-creds',
                url: 'https://github.com/SagarNajardhane/DevOps_Assingment_7.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                for /f "tokens=5" %%a in ('netstat -ano ^| findstr :8082') do taskkill /F /PID %%a
                start "" /B java -jar target\\DevOps_Ass_7-0.0.1-SNAPSHOT.jar
                '''
            }
        }
    }
}
