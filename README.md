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
Copiar código

---

## Requisitos

- Docker y Docker Compose
- Node.js >= 20 (para desarrollo local)
- Git
- Navegador moderno (Chrome, Edge, Firefox)

---

## Clonar el Proyecto

```bash
git clone https://github.com/GabrielReyes3/experiencias-unicas.git
cd experiencias-unicas
Levantar el Proyecto con Docker
Construir y levantar los contenedores:

bash
Copiar código
docker compose up --build -d
Verificar que los contenedores estén corriendo:

bash
Copiar código
docker compose ps
Puertos expuestos:

Frontend: http://localhost:5173

Backend: http://localhost:3001 (internamente 3000)

Nginx (proxy inverso): http://localhost

Comprobar Funcionamiento del Proxy Inverso
Acceder a http://localhost/ en el navegador para cargar el frontend.

El frontend hace peticiones a /api/* que son redirigidas por Nginx al backend (/api/health, /api/service, /api/booking).

Puedes verificar la conexión directa al backend con:

bash
Copiar código
curl http://localhost:3001/api/health
Respuesta esperada:

json
Copiar código
{
  "status": "ok",
  "env": "development"
}
Ejecutar Tests de Integración (Supertest)
Ingresar al backend:

bash
Copiar código
cd server
Instalar dependencias (si no está hecho en Docker):

bash
Copiar código
npm install
Ejecutar los tests:

bash
Copiar código
npm test
Tests incluidos:

GET /api/health → Verifica que el endpoint de salud responde status: ok.

GET /api/__test/services → Verifica que la lista de servicios inicial existe.

POST /api/__test/services → Crea un nuevo servicio y lo valida con GET.

Variables de Entorno
Backend .env (ejemplo):

ini
Copiar código
PORT=3000
SUPABASE_URL=https://<tu-supabase-url>.supabase.co
SUPABASE_KEY=<tu-supabase-key>
JWT_SECRET=supersecreto123
JWT_EXPIRES_IN=1h
NODE_ENV=development
Frontend .env (si aplica):

ini
Copiar código
VITE_API_URL=http://localhost/api
Notas
Nginx se configura como proxy inverso y redirige /api/ al backend y / al frontend.

Docker Compose levanta 3 servicios: backend, frontend y nginx.

Se incluyen pruebas de integración usando Supertest en el backend.

Autor
Gabriel Reyes

Proyecto desarrollado como MVP para gestión de experiencias turísticas locales.