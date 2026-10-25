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

- **Necesidades:** preparar un presupuesto claro durante o inmediatamente después de una visita; guardar el justificante de un gasto asociado al trabajo.
- **Frustraciones por validar:** volver a introducir datos al final de la jornada, teclear con el móvil y tener que recordar dónde guardó un ticket.
- **Objetivos:** compartir una propuesta comprensible desde el lugar de trabajo y encontrar después el gasto asociado.
- **Casos de uso:** acceder a su cuenta, crear un presupuesto con conceptos e importes, generar un enlace temporal para consultarlo y compartirlo por WhatsApp; fotografiar un ticket y asociarlo al presupuesto.

### Persona 2: Elena, 41 años, clienta particular (hipótesis)

- **Necesidades:** consultar desde el móvil el desglose y el importe de un presupuesto recibido.
- **Frustraciones por validar:** tener que instalar una aplicación o crear una cuenta para consultar una propuesta.
- **Objetivos:** acceder a la información acordada mediante un enlace y poder conservarla.
- **Caso de uso incluido en el MVP:** abrir el enlace temporal y consultar el presupuesto sin registrarse. Aceptar o rechazar queda fuera del MVP y se considera una ampliación.

## 3. Competencia y alternativas

La comparación separa características que los proveedores anuncian de observaciones de reseñas. Las páginas comerciales describen sus propios productos; no demuestran demanda ni facilidad de uso. Las reseñas son experiencias individuales, no una muestra representativa.

| Alternativa | Características documentadas | Oportunidad que se investigará |
|---|---|---|
| **Holded** | Su página de precios presenta una suite de gestión para pequeñas empresas y enumera, entre otras funciones, presupuestos, facturas, contactos y herramientas financieras. La oferta depende del plan. | Comprobar con autónomos si necesitan una herramienta más acotada para generar y compartir un presupuesto desde el móvil, o si la solución actual ya les resulta suficiente. |
| **FacturaDirecta** | La página oficial presenta facturación, presupuestos y gastos; el plan gratuito publicado incluye límites de facturas, clientes y productos. Los límites y precios pueden cambiar. | Comparar el número de pasos necesarios para crear y compartir un presupuesto en un teléfono, sin asumir que la aplicación actual sea inadecuada. |
| **FactuPro** | En su propia guía comercial anuncia un servicio de facturación por WhatsApp que también registra gastos a partir de fotos de tickets. Es una señal de que la combinación WhatsApp + gastos ya tiene oferta comercial, no una prueba independiente de su adopción o eficacia. | Comparar alcance y recorrido: FactuPro anuncia generación de facturas y automatización; el MVP de Presupuestando se limita a presupuestos de solo lectura y asociación de fotos, sin facturación fiscal ni OCR. Verificar en una prueba de producto antes de atribuir ventajas. |
| **SinTrámite** | Su guía comercial describe captura y organización móvil de facturas/tickets y presenta estimaciones sobre el impacto de extraviarlos. No publica allí una metodología independiente que permita tratar esas cifras como medición representativa. | Comparar si un archivo vinculado a un presupuesto resuelve una necesidad distinta de guardar el gasto en el propio teléfono; validar con usuarios. |
| **Libreta y WhatsApp** | Alternativa manual: notas en papel y comunicación directa por mensajería. El equipo aún debe verificar su uso, ventajas e inconvenientes mediante entrevistas. | Evaluar si un enlace consultable y un archivo de tickets asociado a cada trabajo aportan suficiente valor frente a una alternativa flexible y familiar. |

Como evidencia cualitativa exploratoria, la ficha de Holded en la App Store mostraba, al consultarla el 25 de octubre de 2026, una valoración global de 4,5/5 sobre 551 valoraciones y algunas reseñas individuales que mencionan problemas de visualización de documentos o de acceso a la cámara. Son comentarios autoseleccionados sobre incidencias concretas; no demuestran que la aplicación sea generalmente difícil ni que los usuarios objetivo compartan esa experiencia. La página de FactuPro sirve como evidencia de oferta comercial existente en este ámbito, no como investigación de usuarios.

**Propuesta de valor, pendiente de validación:** «Para profesionales de oficios que preparan presupuestos y guardan gastos durante su jornada, Presupuestando ofrece un recorrido web móvil para consultar un presupuesto mediante un enlace temporal de solo lectura y asociar la fotografía de un ticket al trabajo, sin que el cliente necesite una cuenta». No se afirma que sea la única solución que usa WhatsApp o captura tickets; su diferenciación propuesta es el alcance acotado a presupuestos y la asociación del gasto al trabajo, aspectos que deben compararse y validarse.

### Fuentes consultadas

- Holded, [planes y características](https://www.holded.com/es/precios), consultado el 25 de octubre de 2026.
- Holded, [ficha y reseñas de la aplicación en App Store](https://apps.apple.com/es/app/holded-facturaci%C3%B3n-y-mucho-m%C3%A1s/id1369704574?see-all=reviews), consultada el 25 de octubre de 2026.
- FacturaDirecta, [planes y características](https://www.facturadirecta.com/pequenos-negocios/precios/), consultado el 25 de octubre de 2026.
- FactuPro, [guía comercial sobre facturación por WhatsApp](https://factupro.es/blog/facturar-por-whatsapp), consultada el 25 de octubre de 2026.
- SinTrámite, [guía comercial para organizar tickets](https://sintramite.es/organizar-tickets-autonomos), consultada el 25 de octubre de 2026.

Las páginas de producto respaldan únicamente las características y condiciones que publican; no se usan como evidencia de satisfacción, facilidad de uso o demanda. No se adopta la estimación monetaria publicada por SinTrámite como un dato validado, porque la fuente consultada no aporta una metodología independiente ni una muestra. La valoración de App Store y las reseñas pueden cambiar con el tiempo.
