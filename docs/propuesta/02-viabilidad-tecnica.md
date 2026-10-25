# Viabilidad Técnica · Equipo 1

## Introducción
Este documento evalúa la viabilidad de «Presupuestando», una aplicación web *mobile-first* para profesionales de oficios. El MVP prioriza el alta e inicio de sesión del técnico, la creación de un presupuesto, su consulta mediante un enlace temporal de solo lectura, su preparación para compartir por WhatsApp y la captura y asociación de un ticket. El equipo aún debe validar el problema con usuarios y realizar pruebas de concepto para confirmar la viabilidad temporal. La arquitectura propuesta usa MongoDB Atlas, Express, React con Vite y Node.js.

## 1. Análisis de Requisitos Funcionales y Priorización (MoSCoW)

### Must have
1. Registrar una cuenta de técnico con correo y contraseña.
2. Iniciar sesión como técnico desde un navegador móvil.
3. Crear y guardar un presupuesto con los datos mínimos del cliente y una o más líneas de concepto.
4. Generar un enlace aleatorio temporal que permita consultar ese presupuesto en modo de solo lectura y sin cuenta.
5. Preparar un mensaje de WhatsApp con el enlace; el técnico confirma el envío desde la aplicación de mensajería.
6. Capturar o seleccionar y subir una fotografía de un ticket desde el navegador móvil.
7. Asociar el ticket subido a un presupuesto propio.

### Should have
8. Aceptar o rechazar un presupuesto desde su enlace público.
9. Consultar el histórico de presupuestos y su estado.
10. Consultar el total mensual de gastos archivados.

### Could have
11. Calcular el beneficio neto de un trabajo restando los tickets asociados al total presupuestado.
12. Descargar un presupuesto aceptado en formato PDF.

### Won't have
13. Integrar con cuentas bancarias para la conciliación de pagos.
14. Gestionar el inventario y stock físico de los materiales del almacén.

El catálogo contiene 14 requisitos: 7 Must (50 %), 3 Should, 2 Could y 2 Won't. Las funcionalidades Won't se documentan como exclusiones y no forman parte de la entrega. El máximo de Must de la guía es la mitad del total.

## 2. Producto Mínimo Viable (MVP)

El MVP se compone estrictamente de estos 7 requisitos Must:

- RF-01: registrar la cuenta del técnico.
- RF-02: iniciar sesión.
- RF-03: crear y guardar un presupuesto con cliente y conceptos.
- RF-04: emitir un enlace temporal de solo lectura para consultar el presupuesto.
- RF-05: preparar el enlace en un mensaje de WhatsApp que el técnico debe confirmar.
- RF-06: capturar o seleccionar y subir una fotografía del ticket.
- RF-07: asociar el ticket al presupuesto propio.

La consulta pública de solo lectura es parte del comportamiento de RF-04: un enlace que no muestra el presupuesto no cumple el requisito. La aceptación o el rechazo por parte del cliente son RF-08 (Should) y no están incluidos en el MVP.

### Requisito no funcional

- **NF-01 (fotografías):** antes de subir la imagen, la aplicación intentará reducir su tamaño a menos de 500 KB sin perder la legibilidad del texto principal. Se comprobará con la muestra definida en OBJ-04; si no se alcanza el umbral, se informará del resultado real en la evaluación y no se afirmará que se ha cumplido.

### Recorrido mínimo del usuario:
- **Acceso:** Abre la aplicación web en el navegador del teléfono móvil e inicia sesión con su cuenta.
- **Creación:** Tras diagnosticar una avería in situ, crea un nuevo presupuesto introduciendo los datos del cliente y seleccionando líneas de gasto básicas mediante iconos rápidos (material y mano de obra).
- **Consulta y envío:** Genera un enlace público temporal de solo lectura; el cliente puede abrir y consultar el presupuesto sin registrarse. El técnico abre WhatsApp con el mensaje preparado y confirma personalmente el envío.
- **Registro de gasto:** Al salir hacia el almacén de suministros, pulsa el botón de captura rápida y fotografía el ticket físico de papel usando la cámara del navegador móvil.
- **Asociación:** Asocia esa fotografía al presupuesto recién emitido, dejando el gasto registrado y archivado en la nube sin necesidad de ordenador de escritorio.

## 3. Requisitos Técnicos: Frontend, Backend e Infraestructura

### 3.1 Frontend (React)
La aplicación será una web pensada para el móvil (*mobile-first*), con botones grandes y concebida para teclear lo mínimo. Existirán una vista privada del técnico y una vista pública de solo lectura para el cliente, accesible mediante token temporal. Se utilizará Vite para compilar el proyecto de React, junto con las siguientes herramientas:

- **Navegación (React Router):** Gestión de rutas SPA (`/login`, `/panel`, `/nuevo-presupuesto`) y la ruta pública parametrizada (`/p/:token`), que es la que abre el cliente desde WhatsApp.
- **Gestión del estado (Zustand):** Se unifica la gestión del estado global en Zustand por su ligereza y simplicidad frente a Redux o Context, manteniendo el usuario con sesión activa y el borrador del presupuesto mientras se navega entre pantallas.
- **Estilos y componentes de interfaz (CSS nativo + lucide-react):** Se descarta cualquier framework CSS externo (como Tailwind CSS, Bootstrap o MUI) para evitar sobrecarga de dependencias y garantizar un rendimiento óptimo en pantallas táctiles de gama baja. Se utilizará CSS nativo mediante variables CSS (`:root`) para temas/paleta y CSS Modules para encapsular estilos por componente. `lucide-react` aportará los iconos táctiles de los conceptos (material, mano de obra, desplazamiento).
- **Peticiones al backend (Axios):** Cliente HTTP para comunicar con la API de Express. La sesión del técnico se mantendrá mediante cookie `HttpOnly`, `Secure` y `SameSite=Lax`; el JavaScript del navegador no leerá ni guardará el JWT en `localStorage` o Zustand. Las mutaciones protegidas deberán aplicar controles CSRF apropiados a la estrategia de cookies.
- **Formularios (React Hook Form):** Control y validación ligera en formularios de login y registro.
- **Sin biblioteca:** La foto del ticket se invoca con `<input type="file" capture="environment">`, que abre la cámara del teléfono móvil de forma estándar, y el envío se realiza mediante la API de enlaces de WhatsApp (`wa.me/?text=...`).

### 3.2 Backend (Node.js + Express)
El servidor expondrá una API REST consumida por el frontend mediante Axios:
- **Autenticación y Seguridad (JWT + bcrypt):** El servidor valida un JWT de corta duración en cada petición protegida; la contraseña se almacena con hash y salt mediante **bcrypt**, nunca en texto claro. Se establecerán límites de intentos para el inicio de sesión y se validará que el técnico autenticado sea propietario del presupuesto o ticket solicitado.
- **Permisos y Roles:**
  - *Técnico (Autenticado):* Requiere JWT válido. Permite crear presupuestos, subir tickets y consultarlos.
  - *Cliente (Invitado):* Ruta pública de solo lectura. El enlace contiene un token aleatorio de alta entropía y fecha de caducidad; la base de datos almacena el hash del token, no el token original. El servidor rechaza tokens inválidos o caducados y no permite cambiar el presupuesto mediante este enlace en el MVP. La página no cargará recursos de terceros y se configurará una política de referencia que no filtre el token a otros sitios.
- **Gestión de ficheros (Multer):** Middleware para procesar peticiones `multipart/form-data`. Se limitará el tamaño de la carga, se comprobará el contenido real del archivo y se aceptarán únicamente formatos de imagen previstos; no se confiará solo en la extensión o en el `Content-Type` enviado por el cliente.
- **Servicios externos (Cloudinary):** El servidor sube las imágenes a Cloudinary y guarda la URL devuelta. La página oficial consultada publica 25 créditos mensuales en el plan gratuito; los créditos se consumen según recursos del servicio y no equivalen a una cantidad fija de imágenes. El equipo debe medir el uso estimado y revisar límites antes del despliegue.

### 3.3 Base de Datos (MongoDB Atlas)
MongoDB encaja como candidato para los documentos de presupuesto porque cada presupuesto puede contener un conjunto variable de conceptos, que se consulta junto al presupuesto. Las relaciones entre propietario, presupuesto y tickets se mantienen mediante referencias. El modelo se revisará con datos de prueba antes de implementarse.

**1. Colección `usuarios`**
- `_id`: ObjectId
- `email`: String (único)
- `password_hash`: String (hash de contraseña con bcrypt, no cifrado reversible)
- `nombre_fiscal`: String (nombre visible para el cliente en el presupuesto)
- `telefono`: String (teléfono de contacto comercial del técnico)
- Índice único en `email`.

**2. Colección `presupuestos`**
- `_id`: ObjectId
- `usuario_id`: ObjectId (referencia al autor en `usuarios`)
- `cliente_nombre`: String (nombre del cliente receptor)
- `cliente_telefono`: String opcional, solo si es necesario para preparar el envío y con datos sintéticos en la demo.
- `conceptos`: Array de objetos `[{ descripcion: String, cantidad: Number, precio_unitario_centimos: Integer }]`, embebidos porque se crean y consultan como parte del presupuesto.
- `total_centimos`: Integer; importes en céntimos para evitar errores de coma flotante.
- `estado`: String (MVP: `['Borrador', 'Pendiente']`; aceptar/rechazar queda para RF-08).
- `token_acceso_hash`: String (hash del token aleatorio, con índice único).
- `expira_en`: Date (fecha de caducidad del enlace temporal)
- `fecha_creacion`: Date
- Índices para listar por `usuario_id` y fecha, y localizar el token. Los presupuestos no se borrarán automáticamente al caducar el enlace.

**3. Colección `tickets`**
- `_id`: ObjectId
- `usuario_id`: ObjectId (referencia a `usuarios`)
- `presupuesto_id`: ObjectId (referencia a `presupuestos` para asociarlo al trabajo)
- `url_imagen`: String (URL segura devuelta por Cloudinary)
- `fecha_subida`: Date
- Índice por `usuario_id` y `presupuesto_id`.

El importe OCR o manual de un ticket no forma parte del MVP; se necesitará si se implementa RF-11. La API comprobará que el presupuesto asociado pertenece al usuario autenticado.
![IMAGEN DIAGRAMA2](../img/diagrama2.jpg)

### 3.4 Infraestructura
- **Frontend (Vercel Hobby):** plan publicado a 0 USD con límites mensuales de uso y condiciones de elegibilidad; validar las condiciones aplicables al uso educativo antes de desplegar.
- **Backend (Render Free):** 750 horas gratuitas mensuales por *workspace* y suspensión del servicio gratuito tras 15 minutos sin tráfico; el arranque puede tardar alrededor de un minuto. Render advierte que sus instancias gratuitas no se deben usar para aplicaciones de producción.
- **Base de datos (MongoDB Atlas Free):** clúster gratuito con 512 MB; regiones y configuración limitadas. No asumir el límite de conexiones citado en borradores anteriores, ya que no se ha verificado en la documentación consultada.
- **Almacenamiento multimedia (Cloudinary Free):** 25 créditos mensuales publicados, sujetos a consumo de almacenamiento, transformación y entrega.
- **Riesgo operativo:** el primer usuario puede experimentar un arranque lento tras la suspensión de Render. La interfaz mostrará progreso, permitirá reintentar y dará un error explícito si no se recupera. Un *health check* automático no evita la suspensión ni debe usarse para mantener artificialmente despierto el plan gratuito.

Los precios y límites cambian. Para que la cookie de sesión no dependa de cookies de terceros, se evaluará exponer la API bajo el mismo origen del frontend mediante un proxy `/api` o, en su defecto, usar dominios propios del mismo sitio y comprobar la política de cookies en Safari y Chrome. Los cambios mutables requerirán protección CSRF. Fuentes oficiales consultadas el 25 de octubre de 2026: [Vercel pricing](https://vercel.com/pricing), [Render Free instances](https://render.com/docs/free), [Atlas Free cluster limitations](https://www.mongodb.com/docs/atlas/reference/free-shared-limitations/) y [Cloudinary pricing](https://cloudinary.com/pricing). Coste inicial de los planes gratuitos descritos: 0 USD, condicionado a elegibilidad, consumo dentro de límites y posibles impuestos o servicios adicionales. Revisar las condiciones vigentes antes de desplegar.

![IMAGEN DIAGRAMA1](../img/diagrama1.jpg)

## 4. Evaluación de Capacidades del Equipo

### 4.1 Inventario de habilidades (Persona × Tecnología)

| Persona | HTML/CSS | JavaScript/React | Node.js/Express | MongoDB | Git/DevOps | Diseño UX |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Dylan Bauti Huelva** | Avanzado | Intermedio | Básico | Intermedio | Intermedio | Básico |
| **Rocío Luque Montes** | Avanzado | Avanzado | Intermedio | Intermedio | Intermedio | Avanzado |
| **Manuel Amado Rodríguez** | Intermedio | Intermedio | Intermedio | Intermedio | Intermedio | Básico |
| **José Luis Yuani Barea** | Intermedio | Básico | Básico | Básico | Básico | Intermedio |

### 4.2 Lagunas de conocimiento
- **Captura y subida de imágenes (Multer + Cloudinary):** Procesamiento de `multipart/form-data` y delegación a Cloudinary desde el backend.
- **Autenticación con JWT:** Implementación de middlewares en Express y gestión segura de tokens en cliente.
- **Gestión de estado global con Zustand:** Manejo del almacén de datos del presupuesto sin recurrir a Context o Redux.
- **Despliegues en Render y Vercel:** Configuración de variables de entorno seguras, políticas de CORS y conexión con MongoDB Atlas en producción.

### 4.3 Viabilidad temporal
El alcance de siete Must parece abordable para cuatro integrantes, pero la viabilidad temporal no está demostrada todavía. Antes de comprometer fechas, el equipo debe realizar una prueba de concepto de autenticación, enlace temporal, carga móvil de imagen y despliegue, y actualizar la estimación con el tiempo disponible en el calendario del módulo.

## 5. Identificación de Riesgos Técnicos

| ID | Riesgo | Probabilidad / Impacto | Mitigación preventiva |
| :--- | :--- | :--- | :--- |
| **R-01** | Bloqueo en la implementación de subida de fotos (Cámara -> Express -> Cloudinary). | Media / Alto | Elaborar en la primera semana una prueba de concepto aislada (PoC) en un script básico antes de acoplarlo a la aplicación principal. |
| **R-02** | Pérdida de código o conflictos graves al integrar cambios (*Merge Conflicts*). | Alta / Alto | Flujo estricto de ramas (`develop` y ramas de tarea). Bloqueo de commits directos y exigencia de PR con al menos una revisión aprobada (*Approve*). |
| **R-03** | Errores de CORS o fallos en variables de entorno detectados tarde en producción. | Media / Alto | Despliegue de un "Hola Mundo" completo conectando Vercel, Render y MongoDB Atlas durante los primeros días de desarrollo. |
| **R-04** | Latencia excesiva o sensación de app colgada por el arranque en frío de Render. | Alta / Medio | Mostrar un estado de carga y permitir reintentar; probar cuánto tarda el primer acceso. No depender de peticiones periódicas para eludir la suspensión del plan gratuito. |
| **R-05** | Falta de tiempo al final de la iteración para terminar las funcionalidades. | Media / Crítico | Priorización estricta del MVP: congelar cualquier funcionalidad *Should* o *Could* hasta que los 7 requisitos *Must have* estén 100% operativos. |
