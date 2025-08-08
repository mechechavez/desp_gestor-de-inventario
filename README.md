# 📦 Gestor de Inventario UTM

Sistema completo de gestión de inventario desarrollado como proyecto académico para la materia de Diseño de Sistemas Informáticos de la Facultad de Ciencias Informáticas - Universidad Técnica de Manabí.

## 🏗️ Arquitectura del Proyecto

```
gestor-de-inventario/
├── frontend/          # Aplicación React + TypeScript
│   ├── components/    # Componentes React reutilizables
│   ├── pages/         # Páginas de la aplicación
│   ├── context/       # Context API para estado global
│   ├── utils/         # Utilidades y helpers
│   └── types.ts       # Tipos TypeScript compartidos
├── backend/           # API REST con Node.js + TypeScript
│   ├── src/
│   │   ├── config/    # Configuración de DB y servicios
│   │   ├── controllers/ # Controladores de rutas
│   │   ├── models/    # Modelos MongoDB con Mongoose
│   │   ├── routes/    # Rutas de la API REST
│   │   ├── middleware/ # Middleware personalizado
│   │   └── types/     # Tipos TypeScript del backend
│   └── package.json
├── docker-compose.yml # Orquestación de contenedores
├── mongo-init.mongodb.js # Script de inicialización de BD
└── README.md
```

## 🚀 Tecnologías

### 🐳 Containerización
- **Docker** - Containerización de aplicaciones
- **Docker Compose** - Orquestación de servicios
- **Nginx** - Servidor web para producción

### Frontend
- **React 19.1.0** con **TypeScript**
- **Vite** - Build tool y dev server
- **Tailwind CSS** - Framework CSS
- **React Router DOM** - Navegación
- **Context API** - Gestión de estado global

### Backend
- **Node.js** con **TypeScript**
- **Express.js** - Framework web
- **MongoDB 7.0** - Base de datos NoSQL
- **Mongoose** - ODM para MongoDB
- **JWT** - Autenticación y autorización
- **bcrypt** - Encriptación de contraseñas

### DevOps y Herramientas
- **Docker Multi-stage builds** - Optimización de imágenes
- **MongoDB 7.0** - Base de datos containerizada
- **Mongo Express** - Interfaz de administración web
- **TypeScript** - Tipado estático
- **ESLint** - Linter de código

## 📋 Características

- ✅ **Gestión completa de productos** (CRUD)
- ✅ **Sistema de categorías**
- ✅ **Control de movimientos** (entradas/salidas)
- ✅ **Dashboard con métricas**
- ✅ **Reportes y estadísticas**
- ✅ **Sistema de usuarios y roles**
- ✅ **Alertas de stock bajo**
- ✅ **Exportación de datos**
- ✅ **Interfaz responsive**

## 🛠️ Instalación y Configuración

### Prerrequisitos
- **Docker** y **Docker Compose** (Requerido)
- **Git** (Opcional - para clonar)

### 🚀 Instalación Rápida con Docker (Recomendada)

```bash
# 1. Clonar el repositorio
git clone <repository-url>
cd gestor-de-inventario

# 2. Ejecutar todo el sistema con un comando
docker-compose up --build

# ¡Listo! Acceder a:
# Frontend: http://localhost
# Backend API: http://localhost:5000
# Mongo Express: http://localhost:8081
```

### � Instalación Manual (Solo para Desarrollo)

#### 1. Clonar el repositorio
```bash
git clone <repository-url>
cd gestor-de-inventario
```

#### 2. Iniciar MongoDB con Docker
```bash
docker-compose up -d mongo mongo-express
# MongoDB: http://localhost:27017
# Mongo Express: http://localhost:8081
```

#### 3. Configurar y ejecutar Backend
```bash
cd backend
npm install
npm run dev
# API corriendo en http://localhost:5000
```

#### 4. Configurar y ejecutar Frontend
```bash
cd frontend
npm install
npm run dev
# App corriendo en http://localhost:5173
```

### 🔧 Configuración Manual

### 2. Configurar Backend
```bash
cd backend
npm install
cp .env.example .env
# Editar .env con tus configuraciones
npm run dev
```

### 3. Configurar Frontend
```bash
cd frontend
npm install
# Editar .env.local si es necesario
npm run dev
```

## 🏃‍♂️ Ejecución

### 🐳 Con Docker (Recomendado - Producción)

```bash
# Opción 1: Construcción y ejecución completa
docker-compose up --build

# Opción 2: Ejecución en segundo plano  
docker-compose up -d --build

# Opción 3: Solo servicios específicos
docker-compose up mongo mongo-express  # Solo base de datos
```

**Accesos:**
- 🌐 **Aplicación Web:** http://localhost
- 🚀 **API REST:** http://localhost:5000
- 🗄️ **MongoDB:** localhost:27017
- 🔧 **Mongo Express:** http://localhost:8081

### 💻 Desarrollo Local (Solo para desarrolladores)

Si quieres modificar el código y ver cambios en tiempo real:

1. **Iniciar solo la base de datos:**
   ```bash
   docker-compose up -d mongo mongo-express
   # MongoDB en http://localhost:27017
   # Mongo Express en http://localhost:8081
   ```

2. **Iniciar Backend en modo desarrollo:**
   ```bash
   cd backend
   npm install
   npm run dev
   # API en http://localhost:5000 con hot-reload
   # Health check: http://localhost:5000/health
   ```

3. **Iniciar Frontend en modo desarrollo:**
   ```bash
   cd frontend  
   npm install
   npm run dev
   # App en http://localhost:5173 con hot-reload
   ```

### 🏭 Producción

Para despliegue en servidor de producción:

```bash
# Construcción optimizada para producción
docker-compose up -d --build

# Verificar estado
docker-compose ps

# Monitorear logs
docker-compose logs -f
```

## 🔧 Configuración

### 🐳 Docker Services

El proyecto incluye `docker-compose.yml` con:
- **MongoDB 7.0** - Base de datos principal
- **Mongo Express** - Interfaz web para administrar MongoDB

```bash
# Iniciar servicios
docker-compose up -d

# Ver logs
docker-compose logs mongodb

# Detener servicios
docker-compose down
```

### Variables de Entorno

#### Backend (.env)
```env
PORT=5000
MONGODB_URI=mongodb://admin:admin123@localhost:27017/gestor_inventario?authSource=gestor_inventario
JWT_SECRET=tu_jwt_secret_muy_seguro
FRONTEND_URL=http://localhost:5173
```

#### Frontend (.env.local)
```env
VITE_API_URL=http://localhost:5000/api
```

### 👤 Usuario por Defecto

```
Email: admin@utm.edu.ec
Password: admin123
Rol: Administrador
```

## 📊 API Endpoints

### Autenticación
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| POST | `/api/auth/login` | Iniciar sesión |
| POST | `/api/auth/logout` | Cerrar sesión |

### Productos
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/products` | Listar productos |
| POST | `/api/products` | Crear producto |
| PUT | `/api/products/:id` | Actualizar producto |
| DELETE | `/api/products/:id` | Eliminar producto |

### Categorías
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/categories` | Listar categorías |
| POST | `/api/categories` | Crear categoría |
| PUT | `/api/categories/:id` | Actualizar categoría |
| DELETE | `/api/categories/:id` | Eliminar categoría |

### Movimientos
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/movements` | Listar movimientos |
| POST | `/api/movements` | Registrar movimiento |

### Sistema
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/health` | Estado del servidor |

## 🎯 Funcionalidades Principales

### Dashboard
- Métricas en tiempo real
- Productos con stock bajo
- Movimientos recientes
- Estadísticas de inventario

### Gestión de Productos
- CRUD completo con validaciones
- Categorización avanzada
- Control de stock en tiempo real
- Códigos de barras únicos
- Gestión de proveedores

### Reportes
- Resumen completo de inventario
- Análisis de valor por categoría
- Alertas de stock bajo
- Exportación de datos a CSV

### Sistema de Usuarios
- Roles diferenciados (admin/usuario)
- Autenticación JWT segura
- Gestión completa de permisos
- Sesiones persistentes

## 🔐 Seguridad

- **Autenticación JWT** con tokens seguros
- **Encriptación bcrypt** para contraseñas
- **Validación de datos** en frontend y backend
- **CORS configurado** para APIs
- **Headers de seguridad** implementados
- **Variables de entorno** para datos sensibles

## 🐳 Despliegue con Docker (Recomendado)

### 📦 Sistema Completamente Containerizado

Este proyecto está completamente dockerizado, lo que significa que **puedes ejecutarlo en cualquier computador** que tenga Docker instalado, sin necesidad de instalar Node.js, MongoDB u otras dependencias.

### 🚀 Instalación de Requisitos

#### Windows
```bash
# Descargar e instalar Docker Desktop
# https://www.docker.com/products/docker-desktop/
# Docker Compose se incluye automáticamente
```

#### macOS
```bash
# Descargar e instalar Docker Desktop
# https://www.docker.com/products/docker-desktop/
# Docker Compose se incluye automáticamente
```

#### Linux (Ubuntu/Debian)
```bash
# Instalar Docker y Docker Compose
sudo apt update
sudo apt install docker.io docker-compose

# Agregar usuario al grupo docker
sudo usermod -aG docker $USER
newgrp docker
```

### 🏃‍♂️ Ejecución Rápida (Un solo comando)

```bash
# Clonar el proyecto
git clone <repository-url>
cd gestor-de-inventario

# ¡Ejecutar todo el sistema!
docker-compose up --build
```

**¡Y listo!** El sistema completo estará funcionando en:
- 🌐 **Frontend:** http://localhost
- 🚀 **API Backend:** http://localhost:5000  
- 🗄️ **MongoDB:** localhost:27017
- 🔧 **Mongo Express:** http://localhost:8081

### 📋 Servicios Docker Incluidos

```yaml
# docker-compose.yml - Arquitectura completa
services:
  # Servicio Backend (API Node.js/Express)
  backend:
    build: ./backend           # Construye desde Dockerfile
    ports: ["5000:5000"]      # Puerto para la API REST
    depends_on: [mongo]       # Depende de la base de datos MongoDB
    restart: always           # Reinicio automático
    
  # Servicio Frontend (React/Vite con Nginx)  
  frontend:
    build: ./frontend         # Construye desde Dockerfile
    ports: ["80:80"]         # Puerto para la aplicación web
    depends_on: [backend]    # Depende del backend
    restart: always          # Reinicio automático
    
  # Servicio de base de datos (MongoDB)
  mongo:
    image: mongo:7.0         # MongoDB versión 7.0
    ports: ["27017:27017"]   # Puerto MongoDB
    volumes:
      - mongodb_data:/data/db              # Persistencia de datos
      - ./mongodb/init:/docker-entrypoint-initdb.d  # Scripts de inicialización
    restart: always
    
  # Servicio de administración de MongoDB (Mongo Express)
  mongo-express:
    image: mongo-express     # Interfaz web para administrar MongoDB
    ports: ["8081:8081"]     # Puerto para interfaz web de administración
    depends_on: [mongo]      # Depende de MongoDB
    restart: always

# Red personalizada para comunicación entre contenedores
networks:
  app-network:
    driver: bridge

# Volúmenes para persistir los datos de la base de datos
volumes:
  mongodb_data:
```

### 🔧 Comandos Docker Útiles

#### Gestión de Servicios
```bash
# Iniciar todos los servicios
docker-compose up

# Iniciar en modo detached (segundo plano)
docker-compose up -d

# Construir y ejecutar (recomendado)
docker-compose up --build

# Ver estado de contenedores
docker-compose ps

# Ver logs de todos los servicios
docker-compose logs -f

# Ver logs de un servicio específico
docker-compose logs -f backend
docker-compose logs -f frontend
docker-compose logs -f mongo
```

#### Gestión de Datos
```bash
# Detener servicios sin eliminar datos
docker-compose stop

# Reiniciar servicios
docker-compose restart

# Detener y eliminar contenedores (mantiene volúmenes)
docker-compose down

# Eliminar TODO incluyendo volúmenes (¡CUIDADO!)
docker-compose down -v

# Limpiar imágenes no utilizadas
docker system prune -f
```

### 📁 Estructura Docker

```
gestor-de-inventario/
├── docker-compose.yml          # Configuración principal de servicios
├── .env                        # Variables de entorno
├── backend/
│   ├── Dockerfile             # Imagen del backend
│   ├── .dockerignore          # Archivos ignorados en build
│   └── src/                   # Código fuente
├── frontend/
│   ├── Dockerfile             # Imagen del frontend  
│   ├── .dockerignore          # Archivos ignorados en build
│   └── components/            # Código fuente
├── .vscode/
│   └── settings.json          # Configuración VS Code
└── mongodb/
    └── init/                  # Scripts de inicialización DB
```

### 🔒 Variables de Entorno (.env)

```env
# MongoDB Configuration
MONGO_ROOT_USER=admin
MONGO_ROOT_PASS=secretpassword

# Mongo Express Configuration  
ME_USER=admin
ME_PASS=adminpass

# Backend Configuration
JWT_SECRET=tu_jwt_secret_muy_seguro
NODE_ENV=production
```

### 🚀 Despliegue en Producción

#### Para Servidor Local
```bash
# Clonar proyecto
git clone <repository-url>
cd gestor-de-inventario

# Configurar variables de entorno para producción
cp .env.example .env
nano .env  # Editar con valores seguros

# Desplegar
docker-compose up -d --build

# Verificar estado
docker-compose ps
docker-compose logs -f
```

#### Para Servidor Remoto
```bash
# En el servidor de producción
git clone <repository-url>
cd gestor-de-inventario

# Configurar firewall (si es necesario)
sudo ufw allow 80    # Frontend
sudo ufw allow 5000  # API Backend
sudo ufw allow 8081  # Mongo Express (solo si necesitas admin)

# Desplegar
docker-compose up -d --build
```

### 🔄 Portabilidad Total

#### ✅ Ventajas del Despliegue Docker:

1. **🚀 Instalación Instantánea**
   - Un solo comando: `docker-compose up --build`
   - No necesitas instalar Node.js, MongoDB, npm, etc.

2. **📦 Portabilidad Completa**
   - Funciona en Windows, macOS, Linux
   - Mismo comportamiento en todos los entornos
   - "Funciona en mi máquina" → "Funciona en cualquier máquina"

3. **🔧 Cero Configuración Manual**
   - Base de datos se configura automáticamente
   - Redes entre contenedores auto-gestionadas
   - Dependencias resueltas automáticamente

4. **🔒 Aislamiento Seguro**
   - No afecta el sistema anfitrión
   - Cada servicio en su propio contenedor
   - Fácil limpieza y eliminación

5. **📊 Monitoreo Simple**
   - Logs centralizados con `docker-compose logs`
   - Estado de servicios con `docker-compose ps`
   - Reinicio automático en caso de fallos

### 🎯 Llevar a Otro Computador

Para ejecutar este proyecto en **cualquier otro computador**:

1. **Instalar Docker** en el computador destino
2. **Copiar la carpeta** completa del proyecto
3. **Ejecutar:** `docker-compose up --build`

**¡Eso es todo!** No necesitas instalar nada más.

### 🐳 Docker

## 🧪 Testing

```bash
# Backend
cd backend
npm test

# Frontend
cd frontend
npm test
```

## 📝 Estado del Proyecto

✅ **COMPLETAMENTE FUNCIONAL** - Sistema de inventario en producción

### ✅ Características Implementadas
- [x] **Frontend React + TypeScript** optimizado
- [x] **Backend Node.js + Express** robusto
- [x] **Base de datos MongoDB** con Docker
- [x] **Autenticación JWT** completa
- [x] **CRUD productos y categorías** funcional
- [x] **Sistema de movimientos** implementado
- [x] **Dashboard con métricas** en tiempo real
- [x] **Reportes y exportación** operativos
- [x] **Interfaz responsive** optimizada
- [x] **Configuraciones de desarrollo** listas

### 🔧 Optimizaciones Recientes
- [x] **Docker Compose** para MongoDB
- [x] **Scripts de inicialización** de base de datos
- [x] **Configuraciones TypeScript** optimizadas
- [x] **ESLint rules** ajustadas para desarrollo
- [x] **Estructura de archivos** limpia y organizada

### �️ Desarrollo Local

```bash
# Clonar tu fork
git clone https://github.com/mechechavez/desp_gestor-de-inventario.git
cd gestor-de-inventario

# Instalar dependencias
cd backend && npm install
cd ../frontend && npm install

# Iniciar servicios
docker-compose up -d
cd backend && npm run dev &
cd frontend && npm run dev
```

---

### 🏆 Proyecto Académico - Universidad Técnica de Manabí

**Sistema de Gestión de Inventario** desarrollado para la materia de **Diseño de Sistemas Informáticos** de la **Facultad de Ciencias Informáticas**. Implementado con las mejores prácticas y tecnologías modernas: Docker, MongoDB, React y Node.js.

#### 🎓 Información Académica
- **Universidad:** Universidad Técnica de Manabí (UTM)
- **Facultad:** Ciencias Informáticas  
- **Materia:** Diseño de Sistemas Informáticos
- **Tecnologías:** React, Node.js, MongoDB, Docker, TypeScript
- **Integrantes:** Mercedes Carmen Chavez Hidalgo - Jaime David Cevallos Rivera - Fernando Guillermo Garay Delgado
