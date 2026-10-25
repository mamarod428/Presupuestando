# Fase 4 · Recursos · Equipo 1

## Introducción
La Fase 4 detalla la organización humana, tecnológica y metodológica del equipo para el desarrollo del proyecto. Define los roles técnicos, el reparto de responsabilidades por módulo de negocio, el herramental de desarrollo normalizado y los flujos de gestión en Git para asegurar una integración continua limpia durante todo el ciclo de vida del software.

## 1. Las personas

### Roles técnicos

| Persona | Rol | De qué responde |
| :--- | :--- | :--- |
| Dylan Bauti Huelva (@dbauhue1708) | Frontend Lead & UX | Revisa PR de `client/` en rotación; responde de React, navegación, estado y accesibilidad móvil. |
| Rocío Luque Montes (@lmrocio) | Frontend Developer & Usabilidad | Implementa las vistas de técnico y cliente, formularios y flujo de cámara; participa en pruebas con usuarios. |
| Manuel Amado Rodríguez (@mamarod428) | Backend Lead & Auth | Revisa PR de `server/` en rotación; responde de la API, autenticación y carga de ficheros. |
| José Luis Yuani Barea (@jyuanib) | Database Manager & QA/DevOps | Responde del diseño de MongoDB, integración de almacenamiento, pruebas y despliegues. |

### Responsables por módulo

| Módulo | Requisitos (RF del MVP) | Responsable | Apoyo |
| :--- | :--- | :--- | :--- |
| Autenticación y Usuarios | RF-01, RF-02 | Manuel | Dylan |
| Gestión de Presupuestos y enlace público | RF-03, RF-04, RF-05 | Dylan | Rocío |
| Captura y asociación de tickets | RF-06, RF-07 | José Luis | Manuel |

### Comunicación
El canal principal de comunicación diaria, normas de convivencia y resolución de bloqueos están definidos en nuestro [docs/CONTRATO.md](../CONTRATO.md).

## 2. La tecnología

### Stack, servicios y APIs
El stack técnico MERN (MongoDB, Express, React, Node.js), junto con las bibliotecas auxiliares y sus correspondientes límites en capas gratuitas, están detallados y justificados en [02-viabilidad-tecnica.md](02-viabilidad-tecnica.md).

Versiones de referencia consultadas el **25 de octubre de 2026** para planificar la UD1 (versiones publicadas en el registro de npm, no instaladas en este repositorio):

| Componente | Versión de referencia | Uso |
|---|---:|---|
| [Node.js](https://nodejs.org/en/about/previous-releases) | 24.22.1 LTS | Runtime común, fijado mediante `.nvmrc`/`.node-version`. |
| [React](https://registry.npmjs.org/react/latest) / [React DOM](https://registry.npmjs.org/react-dom/latest) | 19.3.1 | Interfaz web. |
| [Vite](https://registry.npmjs.org/vite/latest) | 8.3.5 | Servidor de desarrollo y compilación. |
| [@vitejs/plugin-react](https://registry.npmjs.org/@vitejs%2fplugin-react/latest) | 6.1.2 | Integración React/HMR con Vite. |
| [React Router DOM](https://registry.npmjs.org/react-router-dom/latest) | 7.18.4 | Navegación SPA. |
| [Zustand](https://registry.npmjs.org/zustand/latest) | 5.0.16 | Estado de interfaz no sensible. |
| [Axios](https://registry.npmjs.org/axios/latest) | 1.20.0 | Cliente HTTP. |
| [React Hook Form](https://registry.npmjs.org/react-hook-form/latest) | 7.91.0 | Formularios. |
| [lucide-react](https://registry.npmjs.org/lucide-react/latest) | 1.61.0 | Iconografía. |
| [Express](https://registry.npmjs.org/express/latest) | 5.3.0 | API REST. |
| [Mongoose](https://registry.npmjs.org/mongoose/latest) | 9.11.4 | Modelos y acceso a MongoDB. |
| [Multer](https://registry.npmjs.org/multer/latest) | 2.5.0 | Recepción de carga multipart. |
| [Cloudinary SDK](https://registry.npmjs.org/cloudinary/latest) | 2.11.0 | Subida de imágenes desde el servidor. |
| [bcrypt](https://registry.npmjs.org/bcrypt/latest) | 6.0.0 | Hash de contraseñas. |
| [jsonwebtoken](https://registry.npmjs.org/jsonwebtoken/latest) | 9.0.3 | Tokens de sesión del servidor. |
| [Vitest](https://registry.npmjs.org/vitest/latest) | 5.0.5 | Pruebas frontend. |
| [Jest](https://registry.npmjs.org/jest/latest) | 30.5.2 | Pruebas backend. |
| [Supertest](https://registry.npmjs.org/supertest/latest) | 7.3.1 | Pruebas HTTP de la API. |
| [ESLint](https://registry.npmjs.org/eslint/latest) | 10.13.0 | Análisis estático y estilo. |
| [Prettier](https://registry.npmjs.org/prettier/latest) | 3.9.10 | Formato compartido. |

Son versiones de referencia, no una orden de instalar ciegamente la última versión. Al iniciar la implementación, el equipo comprobará compatibilidad entre Node, Vite, plugins y ESLint; instalará versiones compatibles, guardará las dependencias exactas en los archivos de bloqueo (`package-lock.json`) y actualizará esta tabla. Cada nombre de paquete enlaza a la ficha `latest` consultada en el registro npm; la página de [versiones LTS de Node.js](https://nodejs.org/en/about/previous-releases) identifica su versión y estado de soporte.

### Herramientas de desarrollo

| Para qué | Herramienta |
| :--- | :--- |
| Editor e Inspección de código | VS Code estandarizado con extensiones de ESLint y Prettier. |
| Entorno de ejecución | Node.js 24.22.1 LTS (misma versión para todos, fijada en archivo de versión y CI). |
| Pruebas de API REST | Bruno / Postman para validación de endpoints HTTP y tokens JWT. |
| Testing Frontend | Vitest para pruebas unitarias y de componentes en React. |
| Testing Backend | Jest + Supertest para pruebas de integración de la API Express. |
| Consistencia de estilo | ESLint y Prettier, con configuración compartida y comprobación en CI antes de integrar. |

## 3. La gestión

### Tablero
La gestión de tareas y el seguimiento del sprint se realiza mediante un tablero Kanban en GitHub Projects, vinculado directamente a los Issues del repositorio.

### Ramas
- **Estructura:** La rama `main` contiene el código estable de producción. La rama `develop` actúa como base de integración.
- **Workflow:** Cada funcionalidad o corrección se desarrolla en una rama independiente creada desde `develop` con la nomenclatura `feature/<número-issue>-<tarea>` o `fix/<número-issue>-<tarea>`.
- **Integración:** Las tareas vuelven a `develop` únicamente mediante Pull Request (PR) aprobado. Al finalizar cada sprint, se realiza un PR de `develop` a `main`.
- **Protección:** La protección de `main` y `develop` es un requisito que debe comprobarse en Settings de GitHub: PR obligatorio, al menos una aprobación de una persona distinta del autor y bloqueo del push directo. No se afirma aquí que ya esté configurada.

### Estructura de carpetas
El proyecto se organiza en la raíz en dos carpetas principales más la documentación:
- `client/`: contendrá la aplicación frontend en React.
- `server/`: contendrá la aplicación backend con Node.js y Express.
- `docs/`: documentación de la propuesta, contratos y especificaciones del proyecto.
