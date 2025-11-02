pipeline {
    agent any

    tools {
        maven 'MAVEN_HOME'  // Name must match Maven tool in Jenkins
        jdk 'JDK21'         // Name must match JDK installation in Jenkins
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/djha11/theMetro.git'
            }
        }

        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Build & Unit Test') {
            steps {
                sh 'mvn package'
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh '''
                # Example: Copy .jar to server or local deploy directory
                cp target/*.jar /var/www/myapp/
                '''
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
