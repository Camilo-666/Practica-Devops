pipeline {
    agent any

    tools {
        python 'Python3'
    }

    stages {

        stage('Verificar Python') {
            steps {
                bat 'python --version'
                bat 'where python'
            }
        }

        stage('Probar app') {
            steps {
                bat 'python app.py'
            }
        }
    }
}
