  pipeline {
    agent any

    tools {
       nodejs "Node25"
        dockerTool "Dockertool" 
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ZambranoIvania3A/Despliegue2026.git'
            }
        }

        stage('Instalar dependencias') {
            steps {
                sh 'npm install'
            }
        }

        stage('Construir imagen') {
            steps {
                sh 'docker build -t hola-mundo-node .'
            }
        }

        stage('Ejecutar contenedor') {
            steps {
                sh '''
                docker stop hola-mundo-node || true
                docker rm hola-mundo-node || true
                docker run -d -p 3000:3000 --name hola-mundo-node hola-mundo-node
                '''
            }
        }
    }
}
