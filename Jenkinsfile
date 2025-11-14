pipeline {
    agent any

    tools {
        python 'Python3'   // <-- EXACTAMENTE este nombre tal cual está en tu configuración
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
