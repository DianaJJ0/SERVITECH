# 🚀 ServiTech Web

ServiTech es una plataforma web para conectar usuarios con expertos en tecnología, permitiendo agendar asesorías, realizar pagos seguros, gestionar mensajería y administrar usuarios y expertos desde un panel de administración. El sistema incluye autenticación, videollamadas, pagos integrados y un flujo completo para clientes y expertos.

---

## 📦 Estructura del Proyecto

```
SERVITECH1/
├── backend/
│   ├── src/
│   │   ├── config/           # Configuración de base de datos y entorno
│   │   ├── models/           # Modelos Mongoose (usuarios, expertos, categorías)
│   │   ├── routes/           # Rutas API REST (usuarios, expertos, categorías, pagos)
│   │   └── app.js            # Servidor Express principal
│   ├── .env                  # Variables de entorno (MongoDB, JWT, puerto, etc.)
│   ├── .env.example          # Ejemplo de configuración de entorno
│   ├── inicializar.js        # Script para datos iniciales (categorías, usuarios demo)
│   ├── package.json          # Dependencias Node.js
│
├── views/
│   ├── assets/
│   │   ├── css/              # Estilos CSS
│   │   ├── js/               # Scripts JS
│   │   ├── img/              # Imágenes y multimedia
│   ├── admin/                # Vistas y recursos del panel de administración
│   ├── componentes/          # Componentes EJS reutilizables (header, footer, navbar)
│   ├── *.ejs                 # Vistas principales (login, registro, index, expertos, calendario, pagos, etc.)
│
├── README.md                 # Documentación
└── install_windows.bat       # Instalador rápido para Windows
```

---

## 🖥️ Instalación y Uso en Otro PC

### 1. Requisitos Previos

- **Node.js** v18 o superior
- **MongoDB** v6 o superior (instalado y corriendo localmente)
- **MongoDB Compass** (instalado)
- **Git** (para clonar el repositorio)

---

### 2. Instalación en Linux (Ubuntu/Debian)

```bash
# Instala dependencias del sistema
sudo apt update && sudo apt install -y nodejs npm mongodb git

# Clona el repositorio
git clone https://github.com/DianaJJ0/servitechWeb.git
cd servitechWeb/SERVITECH1/backend

# Instala dependencias del backend
npm install

# Configura las variables de entorno
cp .env.example .env
nano .env
# Ejemplo de configuración:
# MONGODB_URI=mongodb://localhost:27017/servitech
# JWT_SECRET=clave_secreta
# SESSION_SECRET=otra_clave
# PORT=3001

# Inicializa datos básicos (opcional)
node inicializar.js

# Inicia el servidor backend
node src/app.js
# O en modo desarrollo con reinicio automático:
npx nodemon src/app.js
```

#### Instalar nodemon globalmente (opcional)

```bash
npm install -g nodemon
nodemon src/app.js
```

---

### 3. Instalación en Windows 10/11

```powershell
# Instala Node.js, MongoDB y Git desde sus sitios oficiales

# Clona el repositorio
git clone https://github.com/DianaJJ0/servitechWeb.git
cd servitechWeb/SERVITECH1/backend

# Instala dependencias del backend
npm install

# Configura las variables de entorno
# Copia .env.example a .env y edítalo con Notepad o VS Code

# Ejemplo:
# MONGODB_URI=mongodb://localhost:27017/servitech
# JWT_SECRET=clave_secreta
# SESSION_SECRET=otra_clave
# PORT=3001

# Inicializa datos básicos (opcional)
node inicializar.js

# Inicia el servidor backend
node src/app.js
# O en modo desarrollo con reinicio automático:
npx nodemon src/app.js
```

#### Instalar nodemon globalmente (opcional)

```powershell
npm install -g nodemon
nodemon src/app.js
```

---

### 🗄️ Iniciar la base de datos con MongoDB Compass en Linux

1. Abre MongoDB Compass desde el menú de aplicaciones o ejecuta `mongodb-compass` en la terminal.
2. En la pantalla de inicio, ingresa la URI de conexión:  
   `mongodb://localhost:27017/servitech`
3. Haz clic en "Connect" para conectarte.
4. Si la base de datos no existe, se creará automáticamente al ejecutar el backend o el script de inicialización.
5. Puedes visualizar, crear y editar colecciones desde la interfaz de Compass.

---

### 🗄️ Iniciar la base de datos con MongoDB Atlas y Compass en Linux

1. Ingresa a [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) y crea una cuenta (si no tienes una).
2. Crea un nuevo cluster gratuito y espera a que esté listo.
3. En "Database Access", crea un usuario con contraseña y permisos de lectura/escritura.
4. En "Network Access", agrega tu IP pública o permite acceso desde cualquier IP (`0.0.0.0/0`).
5. Copia la URI de conexión del cluster (formato:  
   `mongodb+srv://dianacjj23:<db_password>@adso2873441.e4hnh5b.mongodb.net/servitech?retryWrites=true&w=majority`)
6. Abre MongoDB Compass y pega la URI en el campo de conexión.
7. Haz clic en "Connect" para conectarte y gestionar la base de datos.
8. Actualiza la variable `MONGODB_URI` en tu archivo `.env` con la URI de Atlas.

---

## ⚙️ Comandos Clave

- Instalar dependencias:  
  `npm install`
- Inicializar datos de prueba:  
  `node inicializar.js`
- Iniciar servidor backend:  
  `node src/app.js`
- Iniciar servidor con nodemon (desarrollo):  
  `npx nodemon src/app.js`  
  o si está instalado globalmente:  
  `nodemon src/app.js`

---

## 🌐 Acceso a la Aplicación

Abre tu navegador y visita:

- http://localhost:3001/           (Landing page)
- http://localhost:3001/admin/admin.html (Panel de administración)

---

## 🛠️ Backend

- **Express.js:** Servidor web y API REST.
- **Mongoose:** Modelos y conexión a MongoDB.
- **Rutas:** Endpoints para usuarios, expertos, categorías, pagos y mensajería.
- **Autenticación:** JWT y sesiones.
- **Inicialización:** Script para poblar categorías y usuarios de prueba.
- **Configuración:** Variables en `.env` (MongoDB, JWT, puerto, etc.)

---

## 🎨 Frontend (views/)

- **EJS:** Plantillas dinámicas para las vistas.
- **Assets:** Archivos CSS, JS y multimedia.
- **Flujo usuario:** Registro → Login → Selección de experto → Calendario → Pago → Chat.
- **Panel admin:** Gestión de usuarios y expertos.
- **Componentes:** Header, footer, navbar y otros reutilizables en `/componentes`.
- **Personalización:** Puedes editar los archivos `.ejs` y los assets para adaptar el diseño.

---

## 🔗 Endpoints Principales

- `POST /api/usuarios/login` — Inicio de sesión
- `POST /api/usuarios` — Registro de usuario
- `GET /api/categorias` — Listado de categorías
- `GET /api/expertos` — Listado de expertos
- `POST /api/pse/crear-transaccion` — Iniciar pago
- `GET /api/mensajeria/conversaciones` — Conversaciones usuario

---

## 🧑‍💻 Autor

**Diana Carolina Jiménez**  
GitHub: [@DianaJJ0](https://github.com/DianaJJ0)

---

## 🏆 Estado Actual

- Backend y frontend operativos
- Mensajería y pagos integrados
- Estructura lista para escalar y agregar nuevas funcionalidades

---

## ❓ Preguntas Frecuentes

**¿Por qué me sale error con `npm install`?**  
Asegúrate de estar en la carpeta `backend` y que exista el archivo `package.json`.

**¿Cómo cambio el puerto?**  
Edita la variable `PORT` en el archivo `.env`.

**¿Cómo inicializo datos de prueba?**  
Ejecuta `node inicializar.js` en la carpeta `backend`.

**¿Cómo accedo al sistema?**  
Abre tu navegador y visita `http://localhost:3001/`.

**¿Cómo uso nodemon para desarrollo?**  
Instala nodemon con `npm install -g nodemon` y ejecuta `nodemon src/app.js` para reinicio automático del servidor al hacer cambios.

---

## 🛠️ Solución de problemas: Instalación de nodemon en Linux

Si al instalar nodemon globalmente ves un error de permisos (`EACCES`), ejecuta el comando con `sudo`:

```bash
sudo npm install -g nodemon
```

O instala nodemon localmente en tu proyecto y ejecútalo con `npx` (no requiere permisos especiales):

```bash
npm install --save-dev nodemon
npx nodemon src/app.js
```

---

## 🗄️ Solución de problemas de conexión a MongoDB Atlas

Si el backend no se conecta a la base de datos Atlas, revisa lo siguiente:

1. **Usuario y contraseña:**  
   Verifica que el usuario y la contraseña en tu URI sean correctos y tengan permisos en Atlas.

2. **IP permitida:**  
   En Atlas, ve a "Network Access" y agrega tu IP pública o permite acceso desde cualquier IP (`0.0.0.0/0`).

3. **URI en `.env`:**  
   La variable `MONGODB_URI` debe tener la URI de Atlas, sin espacios ni caracteres extra.

4. **Prueba la URI en MongoDB Compass:**  
   Si no conecta en Compass, revisa el mensaje de error para identificar si es problema de autenticación o red.

5. **Reinicia el backend después de cualquier cambio en `.env`.**

6. **Revisa los logs del backend:**  
   Si ves `bad auth : authentication failed`, revisa usuario/contraseña y permisos en Atlas.

---

