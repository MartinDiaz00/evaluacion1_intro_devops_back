⚙️ Backend - Evaluación DevOps
📌 Descripción
Este repositorio contiene el Backend de la aplicación desarrollada para la evaluación de Introducción a DevOps.

El backend expone una API REST que permite gestionar datos y es consumida por el Frontend.

Se ejecuta en una instancia privada (EC2) dentro de AWS, siguiendo el principio de mínimo privilegio.

🏗️ Arquitectura
La aplicación forma parte de una arquitectura de tres capas:

🌐 Frontend → Subred pública (Nginx)
⚙️ Backend → Subred privada (API)
🗄️ Base de Datos → Subred privada (MySQL/PostgreSQL)
📊 Flujo:

Frontend → Backend → Base de Datos

🔐 Seguridad:

El backend NO es accesible desde internet
Solo acepta tráfico desde el Frontend (Security Group)
Puerto utilizado: 8080
🛠️ Tecnologías utilizadas
Node.js / Express (o la que estés usando)
Docker
AWS EC2
GitHub Actions
Base de datos (MySQL o PostgreSQL)
⚙️ Configuración
🔧 Variables de entorno
Crear un archivo .env o configurar variables en la instancia:

DB_HOST=IP_PRIVADA_DATABASE
DB_PORT=3306
DB_USER=usuario
DB_PASSWORD=contraseña
DB_NAME=nombre_db
PORT=8080
 
⚠️ Reemplazar los valores según tu configuración en AWS.



🐳 Ejecución con Docker
1. Construir imagen
docker build -t backend .
2. Ejecutar contenedor
docker run -d -p 8080:8080 --env-file .env backend
 
🔌 Endpoints principales
Ejemplo de endpoints:

GET /api/items → Listar datos
POST /api/items → Crear registro
📌 El frontend consume estos endpoints a través de la red privada.
🔐 Secrets necesarios
Configurar en GitHub:

DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
🌍 Despliegue
El backend se ejecuta en una instancia EC2 privada:

Puerto: 8080
Sin acceso público
Acceso solo desde Frontend o mediante SSH/Bastion
✅ Verificación
Para comprobar el funcionamiento:

Hacer SSH a la instancia backend (desde la pública)
Verificar contenedor:
docker ps
Probar API localmente:
curl http://localhost:8080/api/items
Validar consumo desde el frontend
📸 Evidencias esperadas
Contenedor backend en ejecución
API respondiendo correctamente
Conectividad con base de datos
GitHub Actions en estado