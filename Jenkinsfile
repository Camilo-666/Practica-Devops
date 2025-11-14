pipeline {
    agent any

    tools {
        // exactamente el Name que pusiste en Tools
        python 'Python3'
    }

    stages {
        stage('Checkout') {
            steps {
                // si usas Pipeline script from SCM, no hace falta; si pegas inline, añade checkout
                checkout scm
            }
        }

        stage('Verificar Python') {
            steps {
                // bat ejecuta el comando en Windows
                bat 'python --version'
                bat 'where python'
            }
        }

        stage('Probar app') {
            steps {
                // ejecuta tu app.py (se asumirá que está en el workspace tras el checkout)
                bat 'python app.py'
            }
        }
    }
}
