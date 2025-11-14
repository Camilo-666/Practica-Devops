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
                bat 'python app.py'   // ← cambia a python3 cuando sepamos cuál usas
            }
        }

        stage('Desplegar') {
            steps {
                echo 'Desplegando aplicación (simulación)...'
            }
        }

    }
}
