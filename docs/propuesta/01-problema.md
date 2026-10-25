# Problema, usuarios y propuesta de valor

## Introducción

«Presupuestando» es una propuesta de aplicación web *mobile-first* para profesionales autónomos de oficios que trabajan fuera de una oficina. El problema que se quiere validar es si crear y compartir un presupuesto desde el lugar de trabajo, y archivar el justificante de un gasto en el momento, resulta hoy innecesariamente lento o difícil para este perfil.

La existencia y magnitud de ese problema aún no se han demostrado mediante entrevistas, encuestas ni datos cuantitativos del equipo. Por tanto, las afirmaciones sobre frecuencia, pérdida de ventas y dificultades con las herramientas actuales se consideran **hipótesis de investigación**, no resultados observados. El equipo no presentará las personas ficticias ni las referencias de proveedores como evidencia de usuarios.

## 1. Necesidad e hipótesis

- **Problema que se investigará:** los profesionales de oficios pueden posponer la preparación y el envío de presupuestos hasta volver a la oficina, y pueden perder o tardar en archivar tickets físicos.
- **Usuarios potenciales:** autónomos y pequeños negocios de electricidad, fontanería, reformas y climatización que preparan presupuestos y registran gastos durante visitas de trabajo.
- **Frecuencia e impacto:** pendientes de medir. No se dispone todavía de una muestra que permita afirmar cuántos presupuestos se retrasan, cuántos justificantes se pierden ni el coste económico asociado.
- **Hipótesis de valor:** una experiencia móvil con pocos campos y controles táctiles grandes puede reducir el tiempo necesario para crear y compartir un presupuesto, y facilitar el archivo de una fotografía de un ticket.

### Evidencia disponible y pendiente

La información de producto de los competidores confirma que existen herramientas de gestión con presupuestos y gastos; no demuestra que sean difíciles de usar ni que los usuarios pierdan ventas. La libreta y WhatsApp son una alternativa observada en el planteamiento del equipo, pero falta documentar entrevistas u observaciones que confirmen su uso.

**Trabajo de investigación pendiente antes de afirmar que el problema está validado:**

1. Entrevistar al menos a cinco autónomos de oficios distintos que hayan preparado presupuestos en el último mes.
2. Preguntar por el proceso más reciente, los pasos y herramientas utilizadas, el tiempo aproximado, los retrasos, los tickets perdidos y las consecuencias; evitar sugerir la respuesta o presentar la aplicación antes de conocer su proceso.
3. Registrar fecha, perfil no identificable, preguntas, respuestas anonimizadas y método de síntesis en el repositorio. No recopilar nombres de clientes, datos fiscales ni documentos financieros.
4. Distinguir citas textuales anonimizadas de interpretaciones del equipo y buscar también casos que contradigan la hipótesis.
5. Resumir el número de participantes y patrones observados, sin generalizar la muestra a todos los autónomos. Si se recogen datos, añadirlos a esta sección antes de la entrega final.

## 2. Usuarios objetivo y casos de uso

Las siguientes personas son **arquetipos hipotéticos**, elaborados para orientar el diseño y pendientes de validación con usuarios reales.

### Persona 1: Paco, 52 años, electricista autónomo (hipótesis)

- **Contexto:** atiende trabajos en domicilios y se desplaza entre clientes y proveedores; su familiaridad con herramientas de gestión móvil aún debe comprobarse.
- **Necesidades:** preparar un presupuesto claro durante o inmediatamente después de una visita; guardar el justificante de un gasto asociado al trabajo.
- **Frustraciones por validar:** volver a introducir datos al final de la jornada, teclear con el móvil en un entorno de trabajo y tener que recordar dónde guardó un ticket.
- **Objetivos:** compartir una propuesta comprensible desde el lugar de trabajo y encontrar después el gasto asociado al mismo trabajo.
- **Casos de uso:** acceder a su cuenta, crear un presupuesto con conceptos e importes, generar un enlace temporal para consultarlo y compartirlo por WhatsApp; fotografiar un ticket y asociarlo al presupuesto.

### Persona 2: Elena, 41 años, clienta particular (hipótesis)

- **Contexto:** recibe una propuesta de un profesional para un trabajo en su domicilio y la consulta desde su teléfono.
- **Necesidades:** consultar desde el móvil el desglose y el importe de un presupuesto recibido.
- **Frustraciones por validar:** buscar la información entre mensajes o tener que instalar una aplicación o crear una cuenta para consultar una propuesta.
- **Objetivos:** acceder a la información acordada mediante un enlace y poder conservarla.
- **Caso de uso incluido en el MVP:** abrir el enlace temporal y consultar el presupuesto sin registrarse. Aceptar o rechazar queda fuera del MVP y se considera una ampliación.

## 3. Competencia y alternativas

La comparación separa características que los proveedores anuncian de observaciones de reseñas. Las páginas comerciales describen sus propios productos; no demuestran demanda ni facilidad de uso. Las reseñas son experiencias individuales, no una muestra representativa.

| Alternativa | Fortalezas documentadas | Limitaciones conocidas / no verificadas | Oportunidad que se investigará |
|---|---|---|
| **Holded** | Su página de precios anuncia presupuestos, facturas, contactos y funciones financieras en una suite para empresas. La App Store mostraba 4,5/5 sobre 551 valoraciones en la consulta del 25 de octubre de 2026. | La amplitud de funciones y planes puede ser más de lo requerido por el MVP, pero no demuestra complejidad ni mala adaptación móvil. Algunas reseñas individuales mencionan incidencias de visualización de documentos y cámara; son autoseleccionadas y no representativas. | Probar en móvil el tiempo y los pasos para crear y compartir un presupuesto; preguntar a autónomos si necesitan una herramienta más acotada o prefieren la amplitud existente. |
| **FacturaDirecta** | Su web anuncia facturación, presupuestos y gastos, además de un plan gratuito con límites publicados de facturas, clientes y productos. | Los límites del plan no permiten concluir nada sobre facilidad de uso, requisitos de ficha de cliente o calidad de la experiencia móvil; no se ha realizado una prueba del producto. | Comparar el mismo escenario de creación y consulta desde móvil, registrando tareas y pasos sin presuponer el resultado. |
| **FactuPro** | Su guía comercial anuncia creación y envío de facturas por WhatsApp y registro de gastos con fotos de tickets. Esto confirma que existe oferta comercial que combina mensajería y gastos. | Es contenido del proveedor; sus afirmaciones sobre rapidez, automatización y público objetivo no son una evaluación independiente. El producto anuncia facturas y automatización que no forman parte del MVP de Presupuestando. | Comparar el alcance y probar si la asociación explícita ticket-presupuesto aporta valor frente al flujo anunciado por el proveedor. |
| **SinTrámite** | Su guía comercial describe captura móvil y organización de tickets en el teléfono, con filtros y exportación. | La guía publica estimaciones económicas, pero no muestra una metodología independiente ni una muestra que permita tratarlas como datos representativos. La solución se describe como local al teléfono, distinta de un archivo compartido con presupuestos. | Validar si guardar el ticket junto al presupuesto resuelve una necesidad que un archivo de gastos independiente no cubre. |
| **Libreta y WhatsApp** | Alternativa manual hipotética: flexible y no exige adoptar una nueva herramienta; estas ventajas deben confirmarse con participantes. | Puede dejar información repartida entre papel y conversaciones, pero el equipo todavía no ha observado ni medido ese comportamiento con usuarios. | Preguntar qué herramientas usan realmente y cómo recuperan presupuestos y justificantes, antes de atribuir fallos a esta alternativa. |

Como evidencia cualitativa exploratoria, la ficha de Holded en la App Store mostraba, al consultarla el 25 de octubre de 2026, una valoración global de 4,5/5 sobre 551 valoraciones y algunas reseñas individuales que mencionan problemas de visualización de documentos o de acceso a la cámara. Son comentarios autoseleccionados sobre incidencias concretas; no demuestran que la aplicación sea generalmente difícil ni que los usuarios objetivo compartan esa experiencia. Las páginas de FactuPro y SinTrámite sirven para documentar oferta comercial, no como investigación independiente de usuarios.

**Propuesta de valor, pendiente de validación:** «Para profesionales de oficios que preparan presupuestos y guardan gastos durante su jornada, Presupuestando ofrece un recorrido web móvil para consultar un presupuesto mediante un enlace temporal de solo lectura y asociar la fotografía de un ticket al trabajo, sin que el cliente necesite una cuenta». No se afirma que sea la única solución que usa WhatsApp o captura tickets; su diferenciación propuesta es el alcance acotado a presupuestos y la asociación del gasto al trabajo, aspectos que deben compararse y validarse.

### Protocolo de entrevistas y registro de resultados

**Muestra prevista:** al menos cinco profesionales autónomos de oficios distintos que hayan preparado un presupuesto en el último mes. Para comprobar el caso del cliente, realizar además pruebas de consulta con al menos cinco personas que hayan recibido o solicitado presupuestos de servicios domésticos. Las muestras son exploratorias, no representativas.

**Guion neutral para profesionales:**

1. Cuéntame la última vez que preparaste un presupuesto después de visitar a un cliente. ¿Qué ocurrió, paso a paso?
2. ¿Qué herramientas utilizaste y en qué dispositivo?
3. ¿Cuánto tiempo transcurrió entre la visita y el envío? ¿Qué hizo que tardara ese tiempo?
4. ¿Qué información necesitaste y qué parte te resultó más laboriosa?
5. ¿Qué hiciste la última vez que compraste material para un trabajo? ¿Cómo guardaste el justificante?
6. En los últimos tres meses, ¿recuerdas algún presupuesto que no pudieras enviar cuando querías o algún justificante que no pudieras localizar? Si no, anotar «no recuerda».
7. ¿Qué consecuencias tuvo ese caso, si las hubo?
8. ¿Qué solución utilizas hoy y qué te funciona bien de ella?
9. ¿Qué cambiarías primero de tu proceso actual?
10. ¿Hay algo de tu proceso que haga que una herramienta móvil o un enlace compartible no te sirva?

No mostrar la idea del equipo hasta terminar las preguntas sobre el proceso actual. Registrar también respuestas que contradigan la hipótesis. Con autorización, se puede cronometrar un escenario de uso del prototipo después de la entrevista; separar siempre el relato retrospectivo de la observación directa.

**Plantilla anonimizada para completar tras las entrevistas** —no rellenar con estimaciones ni respuestas inventadas:

| Código | Perfil general (sin nombre/empresa) | Fecha | Proceso/herramientas descritos | Tiempo declarado (si lo recuerda) | Problema o evidencia concreta | Contraejemplo / qué funciona hoy |
|---|---|---|---|---|---|---|
| P-01 | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente |
| P-02 | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente |
| P-03 | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente |
| P-04 | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente |
| P-05 | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente | Pendiente |

Antes de publicar el resumen, quitar nombres, teléfonos, ubicaciones precisas, datos de clientes y cualquier dato fiscal. Indicar el número real de entrevistas, fechas, método de selección, patrones y desacuerdos; no extrapolar porcentajes de una muestra pequeña.

**Prueba de competencia pendiente:** usar el mismo escenario en cada producto al que el equipo tenga acceso legítimo: crear un presupuesto de ejemplo, compartirlo/consultarlo desde un móvil y localizar el gasto o ticket. Registrar producto, plan, fecha, dispositivo, resultado de cada paso y aquello que no se pudo probar. No intentar evadir planes de pago ni atribuir como limitación algo que no se haya comprobado.

### Fuentes consultadas

- Holded, [planes y características](https://www.holded.com/es/precios), consultado el 25 de octubre de 2026.
- Holded, [ficha y reseñas de la aplicación en App Store](https://apps.apple.com/es/app/holded-facturaci%C3%B3n-y-mucho-m%C3%A1s/id1369704574?see-all=reviews), consultada el 25 de octubre de 2026.
- FacturaDirecta, [planes y características](https://www.facturadirecta.com/pequenos-negocios/precios/), consultado el 25 de octubre de 2026.
- FactuPro, [guía comercial sobre facturación por WhatsApp](https://factupro.es/blog/facturar-por-whatsapp), consultada el 25 de octubre de 2026.
- SinTrámite, [guía comercial para organizar tickets](https://sintramite.es/organizar-tickets-autonomos), consultada el 25 de octubre de 2026.

Las páginas de producto respaldan únicamente las características y condiciones que publican; no se usan como evidencia de satisfacción, facilidad de uso o demanda. No se adopta la estimación monetaria publicada por SinTrámite como un dato validado, porque la fuente consultada no aporta una metodología independiente ni una muestra. La valoración de App Store y las reseñas pueden cambiar con el tiempo.
