pipeline {
    agent any

    tools {
        python 'Python3'
    }

    stages {
        stage('Verificar Python') {
            steps {
                bat "\"${tool 'Python3'}\\python.exe\" --version"
                bat "where python"
            }
        }

        stage('Probar app') {
            steps {
                bat "\"${tool 'Python3'}\\python.exe\" app.py"
            }
        }
    }
}
