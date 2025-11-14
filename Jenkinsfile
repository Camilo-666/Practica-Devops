pipeline {
    agent any

    stages {
        
        stage('Clonar repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/Camilo-666/Practica-Devops.git'
            }
        }

        stage('Construir') {
            steps {
                echo 'Ejecutando build del proyecto...'
            }
        }

        stage('Probar') {
            steps {
                echo 'Ejecutando pruebas...'
                sh 'python3 app.py'
            }
        }

        stage('Desplegar') {
            steps {
                echo 'Desplegando aplicación (simulación)...'
            }
        }

    }
}


