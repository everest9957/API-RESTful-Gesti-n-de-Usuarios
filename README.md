# API RESTful - Gestión de Usuarios

![Node.js](https://img.shields.io/badge/Node.js-18.x-339933?style=for-the-badge&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-4.x-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-8.x-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Mongoose](https://img.shields.io/badge/Mongoose-8.x-880000?style=for-the-badge&logo=mongoose&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

API RESTful desarrollada con **Node.js**, **Express** y **MongoDB** para la gestión de usuarios. Permite crear usuarios y consultar el listado completo a través de endpoints HTTP.

---

## 🛠️ Stack técnico

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js"/>
  <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express"/>
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB"/>
  <img src="https://img.shields.io/badge/Mongoose-880000?style=for-the-badge&logo=mongoose&logoColor=white" alt="Mongoose"/>
  <img src="https://img.shields.io/badge/dotenv-ECD53F?style=for-the-badge&logo=dotenv&logoColor=black" alt="dotenv"/>
  <img src="https://img.shields.io/badge/nodemon-76D04B?style=for-the-badge&logo=nodemon&logoColor=white" alt="nodemon"/>
</p>

| Tecnología | Versión | Propósito |
|---|---|---|
| **Node.js** | 18.x | Runtime de JavaScript |
| **Express** | 4.x | Framework web y enrutado |
| **MongoDB** | 8.x | Base de datos NoSQL |
| **Mongoose** | 8.x | ODM para MongoDB |
| **dotenv** | 16.x | Gestión de variables de entorno |
| **nodemon** | 3.x | Auto-reload en desarrollo |

---

## 📁 Estructura del proyecto

```text

API-RESTful-Gestion-de-Usuarios/
├── config/
│ └── db.js # Conexión a MongoDB
├── controllers/
│ └── userController.js # Lógica de negocio (createUser, getUsers)
├── models/
│ └── User.js # Esquema Mongoose del usuario
├── routes/
│ └── userRoutes.js # Definición de endpoints
├── .env.example # Plantilla de variables de entorno
├── .gitignore
├── package.json
├── server.js # Punto de entrada
└── README.md

```

---

## 📡 Endpoints de la API

**Base URL**: `http://localhost:5000`

| Método | Endpoint | Descripción | Body requerido |
|---|---|---|---|
| `GET` | `/api/users` | Obtener todos los usuarios | — |
| `POST` | `/api/users` | Crear un nuevo usuario | `name`, `email`, `password` |

### Ejemplo: Crear usuario

**Request**:
```http
POST /api/users
Content-Type: application/json

{
  "name": "Judit Giravent",
  "email": "judit@example.com",
  "password": "mi_password_segura"
}

Response (201 Created):

{
  "_id": "507f1f77bcf86cd799439011",
  "name": "Judit Giravent",
  "email": "judit@example.com",
  "password": "mi_password_segura",
  "date": "2024-08-25T10:30:00.000Z",
  "__v": 0
}

Ejemplo: Listar usuarios
Request:

GET /api/users

Response (200 OK):

[
  {
    "_id": "507f1f77bcf86cd799439011",
    "name": "Judit Giravent",
    "email": "judit@example.com",
    "password": "mi_password_segura",
    "date": "2024-08-25T10:30:00.000Z",
    "__v": 0
  }
]

📊 Modelo de datos
User
Campo	Tipo	Requerido	Único	Default
name	String	✅	❌	—
email	String	✅	✅	—
password	String	✅	❌	—
date	Date	❌	❌	Date.now
⚙️ Instalación y ejecución
Requisitos previos
Node.js ≥ 18.x → descargar

MongoDB ≥ 6.x → descargar o cuenta en MongoDB Atlas

1. Clonar el repositorio
bash
git clone https://github.com/jdthgp27/API-RESTful-Gesti-n-de-Usuarios.git
cd API-RESTful-Gesti-n-de-Usuarios
2. Instalar dependencias
bash
npm install
Esto instalará:

express — framework HTTP

mongoose — ODM de MongoDB

dotenv — variables de entorno

nodemon — auto-reload (dev)

3. Configurar variables de entorno
Copia el archivo de ejemplo:

bash
cp .env.example .env
Edita .env con tu configuración:

env
MONGO_URI=mongodb://localhost:27017/user-management
PORT=5000
Si usas MongoDB Atlas:

env
MONGO_URI=mongodb+srv://<usuario>:<password>@cluster0.xxxxx.mongodb.net/user-management
PORT=5000
4. Arrancar el servidor
Modo producción:

bash
npm start
Modo desarrollo (auto-reload con nodemon):

bash
npm run dev
5. Verificar que funciona
Salida esperada en consola:

text
Server running on port 5000
MongoDB Connected
Si ves esos dos mensajes, la API está corriendo correctamente.

🧪 Testing manual
Crear un usuario (con curl)
bash
curl -X POST http://localhost:5000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Judit","email":"judit@test.com","password":"123456"}'
Salida:

json
{
  "_id": "...",
  "name": "Judit",
  "email": "judit@test.com",
  "password": "123456",
  "date": "...",
  "__v": 0
}
Listar usuarios
bash
curl http://localhost:5000/api/users
Con Postman / Insomnia
Crear petición POST a http://localhost:5000/api/users

Body → Raw → JSON

Pegar el JSON del ejemplo

Enviar

⚠️ Limitaciones conocidas
Esta API es una versión inicial con fines educativos. Para producción habría que añadir:

🔒 Encriptación de contraseñas con bcrypt

🔑 Autenticación JWT para proteger endpoints

✅ Validación de datos con express-validator o Joi

🚦 Rate limiting con express-rate-limit

🧪 Tests automatizados con jest y supertest

📖 Documentación con Swagger/OpenAPI

📄 Documentación adicional
📘 Guía completa de la API

🏗️ Diagrama de arquitectura

🚧 Trabajo futuro
□ Añadir endpoints de actualización y eliminación (PUT, DELETE)
□ Implementar autenticación con JWT
□ Encriptar contraseñas con bcrypt
□ Añadir tests automatizados
□ Documentar con Swagger
👤 Autor
Judit Giravent Pineda

GitHub: @jdthgp27

Email: jdthgp27@gmail.com

📄 Licencia
Este proyecto está bajo la Licencia MIT.

⭐ Si te resulta útil, ¡dale una estrella al repositorio!




