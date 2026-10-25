# Objetivos y alcance

**Equipo:** Equipo 1

**Proyecto:** Presupuestando

## Introducción

Esta fase fija los resultados medibles y límites del proyecto. El alcance funcional se deriva de los siete requisitos Must del [MVP en la viabilidad técnica](02-viabilidad-tecnica.md); mantener ambos documentos sincronizados es una condición de entrega.

## 1. Objetivos

### Objetivo general

Facilitar a profesionales autónomos de oficios la creación y consulta de presupuestos y el archivo de tickets de gasto desde el móvil durante su jornada.

### Objetivos SMART

| ID | Objetivo | Indicador y umbral de éxito | Método y plazo |
|---|---|---|---|
| **OBJ-01** | Reducir el esfuerzo de preparar y compartir un presupuesto desde el lugar de trabajo. | Al menos 4 de 5 participantes completan la tarea en menos de 3 minutos. | Cronometrar una tarea con cada uno de cinco autónomos de oficios distintos, antes de la defensa final. Anotar errores y abandonos. |
| **OBJ-02** | Facilitar el archivo inmediato de un ticket de gasto asociado al trabajo correspondiente. | Al menos 4 de 5 participantes completan la tarea en menos de 30 segundos, con conectividad 4G o equivalente. | Cronometrar una tarea con cada uno de los mismos cinco autónomos, antes de la defensa final; separar captura, carga y asociación en el registro. |
| **OBJ-03** | Facilitar al cliente la consulta del presupuesto recibido sin crear una cuenta. | Al menos 4 de 5 participantes abren y localizan el total y los conceptos en menos de 1 minuto. | Prueba de usabilidad con al menos cinco personas que representen a clientes, desde teléfonos propios, antes de la defensa final. No incluye aprobar o rechazar. |
| **OBJ-04** | Reducir el tamaño de las fotografías para facilitar su envío por datos móviles sin perder legibilidad. | En al menos 9 de 10 imágenes de prueba, el archivo enviado pesa menos de 500 KB y el texto principal del ticket sigue siendo legible. | Medir el tamaño y comprobar legibilidad de diez fotos tomadas con al menos tres móviles distintos antes de la defensa final. Si no se logra el umbral, documentar la limitación y no afirmar que el objetivo se cumplió. |

Los instrumentos de prueba registrarán tiempo, dispositivo/navegador, calidad de conectividad y resultado de cada tarea; no guardarán nombres ni datos personales innecesarios. Los resultados se presentarán como observaciones de una muestra pequeña, no como evidencia estadísticamente representativa.

## 2. Alcance

### MVP: siete requisitos Must

El MVP coincide exactamente con RF-01 a RF-07 de [02-viabilidad-tecnica.md](02-viabilidad-tecnica.md):

1. Registro de cuenta de técnico.
2. Inicio de sesión del técnico.
3. Creación y guardado de presupuesto con datos mínimos de cliente y conceptos.
4. Enlace temporal de solo lectura para consultar el presupuesto sin cuenta.
5. Preparación del mensaje de WhatsApp con el enlace, con confirmación de envío por el técnico.
6. Captura o selección y subida de una fotografía de ticket.
7. Asociación del ticket a un presupuesto propio.

### Plataforma

- Aplicación web adaptable a móviles; no se desarrollarán aplicaciones nativas.
- Se realizarán pruebas en navegadores móviles Chrome y Safari disponibles para el equipo; la compatibilidad no se dará por garantizada sin probar dispositivos reales.
- Se publicará un prototipo educativo si las condiciones vigentes de los servicios elegidos lo permiten. No se presentará como sistema de producción ni como herramienta de cumplimiento fiscal.

### Usuarios y datos

- Un rol autenticado: técnico/autónomo.
- Cliente final sin cuenta, con acceso de solo lectura mediante enlace de alta entropía y caducidad.
- Para la demo se usarán datos de prueba. Las fotos reales de tickets solo se usarán con autorización explícita, minimizadas y con los datos fiscales o personales ocultos. No se subirán documentos de terceros ni credenciales.
- Los datos y fotografías de prueba se eliminarán al finalizar la evaluación, conforme a un procedimiento documentado.

## 3. Fuera del alcance de esta versión

| Funcionalidad | Motivo |
|---|---|
| Aceptar o rechazar presupuestos desde el enlace (RF-08) | Es una ampliación Should; el enlace del MVP es de solo lectura. |
| Historial de presupuestos y listado mensual de gastos (RF-09 y RF-10) | Funciones Should posteriores al recorrido mínimo. |
| Cálculo de beneficio y exportación PDF (RF-11 y RF-12) | Funciones Could que no son necesarias para probar la hipótesis principal. |
| Conciliación bancaria y pagos dentro de la app (RF-13) | Requiere integraciones, permisos y medidas adicionales que no caben en el alcance educativo. |
| Inventario y control de stock (RF-14) | No resuelve el recorrido mínimo y ampliaría la interfaz y el modelo de datos. |
| Aplicaciones nativas, facturación fiscal oficial e integraciones de gestoría | Fuera del objetivo de prototipo y no justificadas por los Must definidos. |

## 4. Ampliaciones futuras

Orden propuesto, condicionado a la validación del MVP:

1. Aceptar o rechazar un presupuesto (RF-08).
2. Consultar el historial y totales mensuales (RF-09 y RF-10).
3. Introducir importe de tickets para calcular márgenes y generar exportaciones (RF-11 y RF-12).
4. Evaluar integraciones fiscales solo tras validar necesidad y requisitos legales.
