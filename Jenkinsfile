pipeline {
    agent any

    tools {
        nodejs 'Node 24' // Replace with the name you used in Jenkins configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jlmejia21/angular-jenkins.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test --watch=false --browsers=ChromeHeadless'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando a servidor local...'
                // Ejemplo: Copiar archivos a /var/www
                // sh 'cp -r dist/angular-ci-demo/* /var/www/html/'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
