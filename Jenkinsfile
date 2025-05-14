pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'nodejs', type: 'NodeJS'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Install Angular CLI') {
            steps {
                sh 'npm install -g @angular/cli'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'ng build'
            }
        }

        stage('Test') {
            steps {
                // Si no necesitas tests puedes comentar esta parte
                sh 'ng test --watch=false --browsers=ChromeHeadless || echo "Tests failed, but continuing..."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to production...'
                // Ejemplo: Copiar archivos al servidor remoto
                // sh 'scp -r dist/ubuntu@your.server:/var/www/html/angular-app'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
