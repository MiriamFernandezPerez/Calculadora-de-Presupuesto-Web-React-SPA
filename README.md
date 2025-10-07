# 📊 Calculadora de Presupuesto Web - React SPA

## 🔹 Descripción general

**Calculadora de Presupuesto** es una aplicación web construida con **React** que permite a los usuarios crear, gestionar y almacenar presupuestos para servicios digitales.

La aplicación es una **SPA (Single Page Application)** que calcula presupuestos basados en tres servicios principales:

- 💻 Desarrollo Web  
- 🔍 Consultoría SEO  
- 📈 Campañas de Google Ads  

Los presupuestos se pueden almacenar en el navegador (`localStorage`), ordenar, buscar y compartir mediante parámetros en la URL.

---

## ⚙️ Capacidades clave

| Capacidad | Descripción | Componente principal |
|-----------|------------|-------------------|
| ✅ Selección de servicios | Elige entre Web (500€), SEO (300€), Ads (200€) | `Presupuestos.js` |
| 🛠 Configuración de extras web | Número de páginas e idiomas adicionales | `PanelStyle`, `BotonControles` |
| 🧮 Cálculo de precios | Total en tiempo real: servicios base + extras | Gestión de estado en `Presupuestos.js` |
| 💾 Persistencia de presupuestos | Guardado con metadatos (nombre, cliente, fecha) | `guardarPresupuesto` |
| 📋 Gestión de presupuestos | Ver, ordenar y buscar presupuestos guardados | `Lista` |
| 🌐 Estado compartido | Compartir presupuestos mediante URL | `useSearchParams` |
| ℹ️ Modales informativos | Ayuda contextual para páginas e idiomas | `ModalStyle` |

---

## 🧩 Pila tecnológica

**React Ecosystem:**

- react: ^18.2.0  
- react-dom: ^18.2.0  
- react-router-dom: ^6.4.3  
- react-scripts: 5.0.1  

**Estilos:**

- styled-components: ^5.3.6  
- Bootstrap 5.2.2 (CDN)  
- Font Awesome (CDN)  

**Testing:**

- @testing-library/react  
- @testing-library/jest-dom  
- @testing-library/user-event  

**Sistema de construcción:**

```bash
npm start   # Servidor de desarrollo
npm build   # Build de producción
npm test    # Pruebas unitarias
```

## 🏛 Arquitectura

### 🔹 Entrada y enrutamiento

La aplicación sigue una arquitectura **SPA** con **react-router-dom**:

- `/` → `Home.js` (página de bienvenida)  
- `/presupuestos` → `Presupuestos.js` (calculadora y lista de presupuestos)

### 🔹 Componentes principales

- `Home.js` → Página inicial con navegación  
- `Presupuestos.js` → Gestión de servicios, cálculo y almacenamiento  
- `Lista` → Visualización de presupuestos guardados  
- `ModalStyle` → Ayuda contextual  

---

## 🗃 Gestión de estados y persistencia

### 🔹 Variables de estado y localStorage

| Variable      | Tipo      | Clave `localStorage` | Objetivo                                 |
|---------------|----------|---------------------|-----------------------------------------|
| total         | número   | 'total'             | Total de servicios base                  |
| webChecked    | booleano | 'webChecked'        | Estado del servicio Web                  |
| seoChecked    | booleano | 'seoChecked'        | Estado del servicio SEO                  |
| adsChecked    | booleano | 'adsChecked'        | Estado del servicio Ads                  |
| paginas       | número   | 'paginas'           | Número de páginas adicionales           |
| idiomas       | número   | 'idiomas'           | Número de idiomas adicionales           |
| totalExtras   | número   | 'totalExtras'       | Cálculo extra: `(paginas × idiomas) × 30` |
| nombrePto     | string   | 'nombrePto'         | Nombre del presupuesto                   |
| cliente       | string   | 'cliente'           | Nombre del cliente                        |
| id            | número   | 'id'                | ID autoincremental                        |
| date          | string   | 'date'              | Fecha de creación                         |
| modal         | booleano | —                   | Visibilidad de modal general              |
| modalPag      | booleano | —                   | Modal info páginas                        |
| modalId       | booleano | —                   | Modal info idiomas                        |

### 🔹 Funciones principales

- `handleInputChange` → Cambios en checkboxes y campos de texto  
- `handleNumberChange` → Cambios en campos numéricos  
- `handleClick` → Incrementar/decrementar páginas o idiomas  
- `handleModal` → Abrir/cerrar modales  
- `guardarPresupuesto` → Guardar presupuestos en `localStorage`  

---

## 💾 Persistencia de datos

1. **Estado actual:** sincronizado con `localStorage` usando `useEffect`  
2. **Matriz de presupuestos guardados:** cada presupuesto es un objeto con:

```json
{
  "id": "1",
  "nombrePresupuesto": "Proyecto Web",
  "nombreCliente": "Cliente XYZ",
  "web": "true",
  "seo": "false",
  "ads": "true",
  "paginas": "5",
  "idiomas": "2",
  "fecha": "07/10/2025",
  "total": "800",
  "totalExtras": "300"
}
```

## 🌐 Compartir y navegar

- **Navegación declarativa:** `<Link to='/presupuestos'>`  
- **Navegación programática:** `window.location.reload()` tras guardar  
- **Sincronización de parámetros en URL:** `/presupuestos?web=true&paginas=5&idiomas=2`  

---

## 📂 Estructura de archivos

src/

├─ pages/

│ ├─ Home.js

│ └─ Presupuestos.js

├─ components/

│ ├─ PanelStyle.js

│ ├─ BotonControles.js

│ └─ ModalStyle.js

├─ App.js

└─ index.js


---

## 🔗 Instalación y uso

```bash
# Clonar repositorio
git clone https://github.com/MiriamFernandezPerez/sprint7-reactII.git
cd sprint7-reactII

# Instalar dependencias
npm install

# Ejecutar servidor de desarrollo
npm start
```

