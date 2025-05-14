pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'nodejs', type: 'NodeJS'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Clonar el repositorio
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Instalar dependencias de Node.js
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                // Construir la aplicación Angular
                script {
                    sh 'ng build'
                }
            }
        }

        stage('Test') {
            steps {
                // Ejecutar pruebas (opcional)
                script {
                    sh 'ng test --watch=false --browsers=ChromeHeadless'
                }
            }
        }

        stage('Deploy') {
            steps {
                // Desplegar en un servidor (por ejemplo, usar FTP, SCP, o Docker)
                script {
                    // Aquí puedes agregar tu lógica de despliegue
                    echo 'Deploying to production...'
                }
            }
        }
    }

    post {
        always {
            // Limpiar el entorno
            cleanWs()
        }
    }
}
