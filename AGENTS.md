# AGENTS.md — CiberBot

Este archivo documenta cómo se usó inteligencia artificial (IA)
para construir el proyecto, qué prompts se usaron y qué aportó
cada agente al resultado final.

---

## Agente 1 — Arquitecto de la Estructura de Datos

| Atributo | Detalle |
|----------|---------|
| Herramienta | Claude Sonnet 4.6 (claude.ai) |
| Rol asignado | Diseñador e implementador de la Cola (Queue) |
| Etapa del proyecto | Desarrollo del código fuente (index.html) |
| Modo de uso | Conversación iterativa con prompts específicos |

### Funciones desempeñadas

**1. Diseñar la Cola como estructura de datos central**

El código base no tenía ninguna estructura de datos definida.
El agente propuso usar una Cola FIFO (First In, First Out) para
manejar el historial de conversación. Explicó por qué una Cola
es la elección correcta: los mensajes más antiguos deben salir
primero cuando se supera la capacidad, exactamente como funciona
una fila en la vida real.

**2. Implementar las operaciones fundamentales de la Cola**

El agente implementó las cuatro operaciones:
enqueue(item) agrega al final con .push(),
dequeue() elimina el primero con .shift(),
size() retorna messageQueue.length,
isEmpty() verifica si el arreglo está vacío.
Explicó que .shift() en JavaScript remueve el índice 0 y
desplaza todos los demás, comportándose exactamente como
una operación dequeue de una Cola clásica.

**3. Integrar la Cola con la API de Claude**

El agente diseñó cómo los mensajes de la cola se envían como
historial de conversación en cada petición a la API. Al mandar
messageQueue completo en el campo messages, la IA recibe
contexto de los últimos 10 intercambios sin superar el límite
de tokens ni perder coherencia en la conversación.

**4. Implementar el panel visual de la Cola en tiempo real**

El agente diseñó el sistema de 10 slots que se iluminan según
cuántos mensajes hay en la cola. Implementó initQueuePanel()
para crear los slots al cargar la página, y renderQueuePanel()
para actualizar colores y contador tras cada enqueue o dequeue.
Esto hace visible la estructura de datos durante la demo.

**5. Comentarios explicativos en el código**

El agente escribió todos los comentarios del bloque de la Cola
en español accesible, explicando qué es FIFO, por qué se usa
.shift() y cómo se conecta la estructura con la API, sin asumir
conocimiento previo de estructuras de datos.

---

## Agente 2 — Desarrollador de Interfaz

| Atributo | Detalle |
|----------|---------|
| Herramienta | Claude Sonnet 4.6 (claude.ai) |
| Rol asignado | Implementador de la interfaz visual del chatbot |
| Etapa del proyecto | Diseño y maquetación del index.html |
| Modo de uso | Prompt de especificación completa y revisión iterativa |

### Funciones desempeñadas

**1. Diseñar la identidad visual de CiberBot**

El agente eligió una estética de ciberseguridad con paleta oscura:
fondo casi negro (#060610), acentos en cyan eléctrico (#00c9ff)
y violeta (#7c5cfc). Usó tipografías Syne para titulares y
Space Mono para etiquetas técnicas, creando contraste entre
lo legible y lo técnico sin usar fuentes genéricas como Arial.

**2. Construir el sistema de mensajes con animaciones**

El agente implementó las burbujas de chat con animación fadeUp
(aparecen desde abajo con opacidad), el indicador de escritura
con tres puntos animados en keyframes bounce, y el scroll
automático al último mensaje con scrollTop = scrollHeight.
Explicó que la animación debe estar en la clase .msg y no en
el bubble para que incluya también el avatar.

**3. Implementar los botones de temas rápidos**

Para mejorar la experiencia el agente creó cinco botones con
función sendQuick(text) que inyectan una pregunta predefinida
sin que el usuario tenga que escribir. Explicó que estos botones
reducen la fricción de entrada, especialmente en móvil, y
demuestran los temas que el bot domina de forma inmediata.

**4. Implementar el badge de estado de conexión**

El agente agregó el indicador 🟢 Listo / 🟡 Procesando / 🔴 Error
que cambia en tiempo real según el estado del fetch a la API.
Explicó que deshabilitar el botón de envío durante el procesamiento
previene que el usuario envíe mensajes duplicados mientras espera.

**5. Hacer el diseño responsivo**

El agente usó max-width: 760px con margen automático para centrar
el chat, flex-wrap en los badges y botones de temas para que
colapsen en móvil, y unidades rem en lugar de px fijos para que
el texto escale con las preferencias del navegador del usuario.

---

## Agente 3 — Redactor de Documentación Académica

| Atributo | Detalle |
|----------|---------|
| Herramienta | Claude Sonnet 4.6 (claude.ai) |
| Rol asignado | Redactor del documento académico del proyecto |
| Etapa del proyecto | Documentación, criterios de aceptación y fases |
| Modo de uso | Solicitud estructurada siguiendo el rubric del curso |

### Funciones desempeñadas

**1. Redactar la problemática y solución propuesta**

El agente elaboró el párrafo que describe la brecha de conocimiento
en ciberseguridad entre usuarios comunes en Colombia, conectando
el problema con patrones globales de ataques y planteando el
chatbot como solución accesible. Justificó por qué un chatbot
es mejor que una guía estática: es interactivo, personalizado
y disponible en cualquier momento.

**2. Ampliar la problemática con contexto real**

El agente profundizó el problema mencionando reportes del Centro
Cibernético de la Policía Nacional sobre el incremento de delitos
informáticos en Colombia, y estadísticas globales que muestran
que más del 80% de brechas de datos involucran contraseñas débiles.
Esto le da peso académico a la justificación del proyecto.

**3. Definir los criterios de aceptación**

El agente construyó una tabla con 7 criterios verificables, cada
uno con una condición de éxito concreta y medible. Explicó que
los criterios deben ser binarios (se cumple o no) para que puedan
evaluarse objetivamente durante la sustentación sin ambigüedades.

**4. Estructurar las fases del proyecto**

El agente organizó el desarrollo en 4 fases cronológicas con
tareas específicas por semana, siguiendo una estructura de
proyecto de ingeniería de software: Investigación, Diseño,
Desarrollo y Publicación. Esto facilita mostrar el proceso
completo durante la presentación.

**5. Generar el README y el AGENTS.md**

El agente produjo los archivos de documentación del repositorio
asegurando que el proyecto esté presentado de forma profesional
en GitHub, con instrucciones de instalación, descripción de la
estructura de datos y los comandos exactos para publicar en
GitHub Pages.

---

## Reflexión del estudiante

Dividir el trabajo de IA en tres agentes con roles distintos
fue más efectivo que hacer todo en una sola conversación.
El Agente 1 se enfocó en que la estructura de datos funcionara
correctamente. El Agente 2 se enfocó en que la interfaz fuera
clara y usable. El Agente 3 se enfocó en que el documento
académico tuviera rigor y estructura.

La parte más importante del proceso no fue recibir el código,
sino entender por qué se eligió una Cola y no otra estructura,
cómo se conecta con la API y qué significa FIFO en la práctica.
Sin esa comprensión no habría sido posible defender el proyecto
en la sustentación ni responder preguntas sobre las decisiones
técnicas tomadas.

---

*Documento generado como parte del Proyecto Final
CiberBot — Herramientas de Inteligencia Artificial
Universidad Cooperativa de Colombia, 2025.*
