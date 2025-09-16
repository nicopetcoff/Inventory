# Inventory Manager PWA

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18-blue.svg)](https://reactjs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-12%2B-blue.svg)](https://www.postgresql.org/)

## 📖 Descripción

**Inventory Manager PWA** es una aplicación web progresiva desarrollada para la gestión eficiente de inventarios. La aplicación permite realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre productos de inventario de manera intuitiva y con capacidades offline.

Este proyecto fue desarrollado como parte de un trabajo universitario para demostrar el uso de tecnologías web modernas y patrones de desarrollo de aplicaciones progresivas, con una arquitectura robusta que incluye PostgreSQL como base de datos.

## ✨ Características

- 📱 **Progressive Web App (PWA)**: Funciona tanto en navegadores como aplicación instalable
- 🔄 **Operaciones CRUD completas**: Crear, leer, actualizar y eliminar productos
- 💾 - **SQLite3**: Base de datos SQL ligera
- 🎨 **Interfaz moderna**: Diseño responsivo con Tailwind CSS
- ⚡ **API RESTful**: Backend robusto con Express.js
- 📊 **Gestión de categorías**: Organización de productos por categorías
- 🔍 **Datos de ejemplo**: Productos precargados para pruebas


## �🛠️ Tecnologías Utilizadas

### Frontend
- **React 18**: Biblioteca de JavaScript para construir interfaces de usuario
- **Tailwind CSS**: Framework de CSS para diseño responsivo
- **Font Awesome**: Iconografía moderna
- **Service Workers**: Para funcionalidad offline

### Backend
- **Node.js**: Entorno de ejecución de JavaScript
- **Express.js**: Framework web para Node.js
- **PostgreSQL**: Base de datos relacional robusta y escalable
- **CORS**: Middleware para Cross-Origin Resource Sharing

### Herramientas de Desarrollo
- **Nodemon**: Herramienta de desarrollo para reinicio automático
- **Babel**: Transpilador de JavaScript

## 📋 Prerrequisitos

Antes de ejecutar este proyecto, asegúrate de tener instalado:

- [Node.js](https://nodejs.org/) (versión 18 o superior)
- [npm](https://www.npmjs.com/) (incluido con Node.js)
- [PostgreSQL](https://www.postgresql.org/) (versión 12 o superior)
- Un navegador web moderno

## 🚀 Instalación y Configuración

### 1. Clonar el repositorio
```bash
git clone https://github.com/nicopetcoff/Inventory.git
cd Inventory
```

### 2. Instalar dependencias
```bash
npm install
```

### 3. Configurar PostgreSQL

#### Opción A: Instalación local
1. Instala PostgreSQL desde [postgresql.org](https://www.postgresql.org/download/)
2. Crea una base de datos llamada `inventory_db`
3. Configura las variables de entorno (opcional):

```bash
# Windows PowerShell
$env:DB_USER="postgres"
$env:DB_PASSWORD="tu_contraseña"
$env:DB_NAME="inventory_db"
$env:DB_HOST="localhost"
$env:DB_PORT="5432"
```

#### Opción B: Usando Docker
```bash
docker run --name postgres-inventory -e POSTGRES_PASSWORD=password -e POSTGRES_DB=inventory_db -p 5432:5432 -d postgres:13
```

### 4. Ejecutar la aplicación
```bash
npm start
```

La aplicación estará disponible en: `http://localhost:80`

## 📚 Uso

### Operaciones Disponibles

1. **Ver productos**: La página principal muestra todos los productos del inventario
2. **Agregar producto**: Crear nuevos productos con información detallada
3. **Editar producto**: Modificar información de productos existentes
4. **Eliminar producto**: Remover productos del inventario
5. **Filtrar por categoría**: Organizar productos por categorías

### Estructura de Producto

Cada producto contiene los siguientes campos:
- **Nombre**: Nombre del producto
- **Categoría**: Clasificación del producto
- **Cantidad**: Stock disponible
- **Precio**: Precio unitario
- **Descripción**: Información adicional del producto

## 🏗️ Estructura del Proyecto

```
inventory/
├── public/
│   ├── app.js              # Aplicación React principal
│   ├── index.html          # Página HTML base
│   ├── manifest.json       # Configuración PWA
│   └── sw.js              # Service Worker
├── server.js              # Servidor Express y API con PostgreSQL
├── package.json           # Configuración del proyecto
├── LICENSE               # Licencia del proyecto
└── README.md             # Documentación
```

### 📊 Esquema de Base de Datos (PostgreSQL)

```sql
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  category VARCHAR(100) NOT NULL,
  quantity INTEGER NOT NULL,
  price DECIMAL(10,2) NOT NULL,
  description TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## � Variables de Entorno

El proyecto utiliza las siguientes variables de entorno para la configuración de PostgreSQL:

| Variable | Valor por defecto | Descripción |
|----------|-------------------|-------------|
| `DB_USER` | `postgres` | Usuario de PostgreSQL |
| `DB_PASSWORD` | `password` | Contraseña de PostgreSQL |
| `DB_NAME` | `inventory_db` | Nombre de la base de datos |
| `DB_HOST` | `localhost` | Host del servidor PostgreSQL |
| `DB_PORT` | `5432` | Puerto de PostgreSQL |
| `PORT` | `80` | Puerto del servidor web |

### Configuración de variables en Windows PowerShell:
```powershell
$env:DB_USER="tu_usuario"
$env:DB_PASSWORD="tu_contraseña"
$env:DB_NAME="inventory_db"
```

## 🔌 API Endpoints

La aplicación expone los siguientes endpoints REST:

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/products` | Obtener todos los productos |
| GET | `/api/products/:id` | Obtener un producto específico |
| POST | `/api/products` | Crear un nuevo producto |
| PUT | `/api/products/:id` | Actualizar un producto existente |
| DELETE | `/api/products/:id` | Eliminar un producto |

### Ejemplo de Producto (JSON)
```json
{
  "id": 1,
  "name": "Laptop Pro",
  "category": "Electronics",
  "quantity": 15,
  "price": 1299.99,
  "description": "High-performance laptop",
  "created_at": "2025-09-14T10:30:00.000Z",
  "updated_at": "2025-09-14T10:30:00.000Z"
}
```

## 📱 Funcionalidades PWA

- **Instalable**: Puede instalarse como aplicación nativa
- **Offline**: Funciona sin conexión a internet (próximamente)
- **Responsivo**: Se adapta a diferentes tamaños de pantalla
- **Manifest**: Configuración completa de metadatos PWA

## 🧪 Scripts Disponibles

- `npm start`: Inicia el servidor de desarrollo
- `npm test`: Ejecuta las pruebas (pendiente implementación)

## 🔧 Solución de Problemas

### Problemas comunes con PostgreSQL:

1. **Error de conexión a PostgreSQL:**
   - Verifica que PostgreSQL esté ejecutándose
   - Comprueba las credenciales en las variables de entorno
   - Asegúrate de que la base de datos `inventory_db` existe

2. **Puerto 80 ocupado:**
   - En Windows, el puerto 80 puede estar ocupado por IIS
   - Cambia la variable de entorno: `$env:PORT="3000"`
   - O ejecuta como administrador

3. **Permisos en puerto 80:**
   - En sistemas Unix/Linux, el puerto 80 requiere privilegios de administrador
   - Ejecuta con `sudo npm start` o usa un puerto diferente

### Comandos útiles para PostgreSQL:

```powershell
# Verificar si PostgreSQL está ejecutándose
Get-Service postgresql*

# Conectar a PostgreSQL desde línea de comandos
psql -U postgres -d inventory_db

# Crear la base de datos manualmente
createdb -U postgres inventory_db
```