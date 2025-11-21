Descripción del proyecto:
Este proyecto es una aplicación sencilla creada con Python, Flask y Gunicorn, empaquetada y ejecutada dentro de Docker.
El objetivo es mostrar un mensaje dinámico generado con pyfiglet y demostrar cómo se despliega una aplicación usando:
- Dockerfile
- Docker-compose
- Gunicorn como servidor WSGI
- Entorno virtual para desarrollo local

mi_proyecto/
│
├── app.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── README.md

<img width="1195" height="798" alt="image" src="https://github.com/user-attachments/assets/c9de8fc6-f8b1-4467-af8e-2457454d8257" />

Instalación local (modo desarrollo)
1. Crear y activar entorno virtual
- python -m venv venv
- source venv/Scripts/activate

2. Instalar dependencias
- pip install -r requirements.txt

3. Ejecutar la aplicación localmente
python app.py

Ejecucioon con Docker:
1. Construir imagen
- docker-compose build
2. Ejecutar el contenedor
-docker-compose up

ARCHIVOS PRINCIPALES
app.py

from flask import Flask
from waitress import serve
import pyfiglet

app = Flask(__name__)

@app.route('/')
def hello():
    
    ascii_art = pyfiglet.figlet_format("¡¡Que Ondaaa!!")
    return f"<pre>{ascii_art}</pre>"

if __name__ == '__main__':
    serve(app, host='0.0.0.0', port=8000)

requerements.txt

Flask==3.1.2
gunicorn==23.0.0
pyfiglet==0.7
waitress==2.1.2
setuptools==67.0.0

dockerfile

FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt /app
RUN pip install --no-cache-dir -r requirements.txt
COPY . /app
EXPOSE 8000

CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:8000"]

docker-compose.yml

version: '3.8'
services:
  app:
    build: .
    ports:
      - "8000:8000"
    environment:
      - FLASK_ENV=development
    volumes:
      - .:/app
    networks:
      - app-network

networks:
  app-network:
    driver: bridge









