# 🌎 Experiencias Únicas

**Plataforma web de servicios turísticos que conecta visitantes con anfitriones locales**

Experiencias Únicas es una aplicación full-stack moderna que permite a los usuarios descubrir y reservar experiencias turísticas auténticas ofrecidas por anfitriones locales. La plataforma facilita conexiones significativas entre viajeros y comunidades locales, promoviendo un turismo más personalizado y sostenible.

## ✨ Características Principales

- 🔍 **Exploración de Servicios**: Descubre experiencias turísticas únicas ofrecidas por anfitriones locales
- 📅 **Sistema de Reservas**: Reserva y gestiona tus experiencias de forma sencilla
- 👥 **Perfiles de Anfitriones**: Conecta directamente con guías y anfitriones locales
- 🎨 **Interfaz Moderna**: Diseño responsive y amigable construido con React
- 🔒 **API RESTful**: Backend robusto con endpoints seguros y bien documentados
- 🐳 **Contenerización**: Despliegue simplificado con Docker y Nginx

## 🛠️ Stack Tecnológico

### Frontend
- **React 18** con **Vite** - Framework y herramienta de construcción
- **Capacitor** - Para capacidades móviles nativas

### Backend
- **Node.js** con **Express** - Servidor y API REST
- **Supabase** - Base de datos y autenticación

### DevOps
- **Docker** & **Docker Compose** - Contenerización
- **Nginx** - Proxy inverso y servidor web
- **Supertest** & **Jest** - Testing de integración

## 📁 Estructura del Proyecto

```
experiencias-unicas/
│
├── .github/                 # Workflows y acciones de GitHub
├── nginx/                   # Configuración de Nginx
│   └── default.conf        # Configuración del proxy inverso
├── public/                  # Archivos estáticos del frontend
├── scripts/                 # Scripts auxiliares
├── server/                  # Backend de la aplicación
│   ├── src/                # Código fuente del backend
│   ├── test/               # Tests de integración (Supertest/Jest)
│   ├── package.json
│   └── Dockerfile
├── docker-compose.yml       # Configuración de servicios Docker
├── Dockerfile.frontend      # Dockerfile para el frontend
├── capacitor.config.json    # Configuración de Capacitor
├── vite.config.js          # Configuración de Vite
├── package.json            # Dependencias del frontend
└── README.md
```

## 🚀 Inicio Rápido

### Prerrequisitos

- **Docker** y **Docker Compose** instalados
- **Node.js** >= 20 (para desarrollo local)
- **Git**
- Navegador web moderno

### Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/GabrielReyes3/experiencias-unicas.git
cd experiencias-unicas
```

2. **Configurar variables de entorno**

Crear archivo `.env` en la raíz con:
```env
VITE_API_URL=http://localhost/api
```

3. **Levantar el proyecto con Docker**
```bash
docker compose up --build -d
```

4. **Verificar que los contenedores estén corriendo**
```bash
docker compose ps
```

### 🌐 Puertos y Acceso

Una vez levantados los contenedores, la aplicación estará disponible en:

- **Frontend**: http://localhost:5173
- **Backend (directo)**: http://localhost:3001
- **Nginx (proxy inverso)**: http://localhost

> **Nota**: Se recomienda acceder a través de Nginx (http://localhost) para que el proxy inverso redirija correctamente las peticiones API.

## 🔍 Verificación del Sistema

### Comprobar el Backend

```bash
curl http://localhost:3001/api/health
```

**Respuesta esperada:**
```json
{
  "status": "ok",
  "env": "development"
}
```

### Comprobar el Proxy Inverso

1. Abre http://localhost/ en tu navegador
2. El frontend debería cargar correctamente
3. Las peticiones a `/api/*` serán redirigidas automáticamente al backend

## 🧪 Testing

El proyecto incluye tests de integración usando Supertest y Jest.

### Ejecutar los Tests

```bash
cd server
npm install
npm test
```

### Tests Incluidos

- ✅ **GET /api/health** - Verifica que el endpoint de salud responde correctamente
- ✅ **GET /api/__test/services** - Verifica la lista de servicios inicial
- ✅ **POST /api/__test/services** - Crea un nuevo servicio y valida su creación

## 🐳 Comandos Docker Útiles

```bash
# Levantar los servicios
docker compose up -d

# Ver logs en tiempo real
docker compose logs -f

# Detener los servicios
docker compose down

# Reconstruir las imágenes
docker compose up --build -d

# Ver el estado de los contenedores
docker compose ps

# Limpiar volúmenes y reconstruir
docker compose down -v
docker compose up --build -d
```

## 📦 Servicios Docker

El proyecto utiliza tres servicios principales:

1. **backend** - API REST en Node.js/Express
2. **frontend** - Aplicación React con Vite
3. **nginx** - Proxy inverso que enruta las peticiones

## 🔧 Configuración de Nginx

Nginx actúa como proxy inverso:

- Peticiones a `/` → Redirige al frontend
- Peticiones a `/api/` → Redirige al backend

Configuración en `nginx/default.conf`

## 🌱 Desarrollo Local (sin Docker)

### Frontend
```bash
npm install
npm run dev
```

### Backend
```bash
cd server
npm install
npm run dev
```


## 📝 Licencia

Este proyecto es un MVP desarrollado con fines educativos y de demostración.

## 👤 Autor

**Gabriel Reyes**

- GitHub: [@GabrielReyes3](https://github.com/GabrielReyes3)
