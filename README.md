# Experiencias Únicas

Experiencias Únicas es una plataforma web de servicios turísticos que conecta visitantes con anfitriones locales para ofrecer experiencias personalizadas. La aplicación está construida con **React + Vite** en el frontend y **Node.js + Express** en el backend. Se utiliza **Supabase** como base de datos y **Docker + Nginx** para la contenerización y gestión de proxy inverso.

---

## Estructura del Proyecto

experiencias-unicas/
│
├─ .github/ # Workflows y acciones de GitHub
├─ nginx/ # Configuración de Nginx
│ └─ default.conf
├─ node_modules/ # Dependencias del proyecto (gitignore)
├─ public/ # Archivos estáticos del frontend
├─ respaldo/ # Carpeta de respaldo opcional
├─ scripts/ # Scripts auxiliares
├─ server/ # Backend
│ ├─ src/ # Código fuente del backend
│ ├─ test/ # Tests (Supertest / Jest)
│ ├─ package.json
│ ├─ package-lock.json
│ └─ Dockerfile
├─ .gitignore
├─ capacitor.config.json # Configuración Capacitor
├─ docker-compose.yml
├─ Dockerfile.frontend # Dockerfile para el frontend
├─ eslint.config.js
├─ index.html # Entrada principal del frontend
├─ package.json # Package del frontend
├─ package-lock.json
├─ README.md
├─ vercel.json
└─ vite.config.js # Configuración de Vite

yaml
---

## Requisitos

- Docker y Docker Compose
- Node.js >= 20 (para desarrollo local)
- Git
- Navegador moderno (Chrome, Edge, Firefox)

---

## Clonar el Proyecto


git clone https://github.com/GabrielReyes3/experiencias-unicas.git
cd experiencias-unicas
Levantar el Proyecto con Docker
Construir y levantar los contenedores:

docker compose up --build -d
Verificar que los contenedores estén corriendo:


docker compose ps
Puertos expuestos:

Frontend: http://localhost:5173

Backend: http://localhost:3001 (internamente 3000)

Nginx (proxy inverso): http://localhost

Comprobar Funcionamiento del Proxy Inverso
Acceder a http://localhost/ en el navegador para cargar el frontend.

El frontend hace peticiones a /api/* que son redirigidas por Nginx al backend (/api/health, /api/service, /api/booking).

Puedes verificar la conexión directa al backend con:


curl http://localhost:3001/api/health
Respuesta esperada:

json
{
  "status": "ok",
  "env": "development"
}
Ejecutar Tests de Integración (Supertest)
Ingresar al backend:


cd server
Instalar dependencias (si no está hecho en Docker):


npm install
Ejecutar los tests:

npm test
Tests incluidos:

GET /api/health → Verifica que el endpoint de salud responde status: ok.

GET /api/__test/services → Verifica que la lista de servicios inicial existe.

POST /api/__test/services → Crea un nuevo servicio y lo valida con GET.

Variables de Entorno
Backend .env 

VITE_API_URL=http://localhost/api
Notas
Nginx se configura como proxy inverso y redirige /api/ al backend y / al frontend.

Docker Compose levanta 3 servicios: backend, frontend y nginx.

Se incluyen pruebas de integración usando Supertest en el backend.

Autor
Gabriel Reyes

Proyecto desarrollado como MVP para gestión de experiencias turísticas locales.