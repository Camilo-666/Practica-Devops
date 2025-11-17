pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout repository'
                checkout scm
            }
        }

        stage('Build image') {
            steps {
                echo 'Construir imagen Docker'
                bat 'docker build -t practica-devops-app:latest .'
            }
        }

        stage('Install & Test (optional)') {
            steps {
                echo 'Instalar dependencias y ejecutar tests si existen'
                bat """
                if exist requirements.txt (
                  python -m pip install --upgrade pip
                  python -m pip install -r requirements.txt
                ) else (
                  echo No requirements.txt detected
                )
                if exist tests (
                  python -m pytest tests || (echo Tests failed & exit /b 1)
                ) else (
                  echo No tests folder detected
                )
                """
            }
        }

        stage('Deploy with Compose') {
            steps {
                echo 'Desplegando con docker compose'
                bat 'docker compose down --remove-orphans || echo "compose down returned non-zero"'
                bat 'docker compose up -d --build'
            }
        }

        stage('Smoke check') {
            steps {
                echo 'Chequeo rapido de servicio'
                bat 'powershell -Command "try { Invoke-WebRequest -UseBasicParsing -Uri http://localhost:5000 -TimeoutSec 5; Write-Host \\"OK: endpoint reachable\\" } catch { Write-Host \\"WARNING: no response from endpoint\\" }"'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado'
        }
    }
}
