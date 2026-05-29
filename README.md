# 🔐 CiberBot — Asesor Personal de Seguridad Digital

Proyecto final de la materia **Herramientas de Inteligencia Artificial**
Universidad Cooperativa de Colombia · 2025

---

## 📌 Descripción

**CiberBot** es una página web con un chatbot impulsado por IA (Claude de Anthropic)
que ayuda a usuarios comunes a protegerse en internet. Responde preguntas sobre
contraseñas, phishing, malware, redes WiFi públicas y privacidad en redes sociales.

---

## 🧱 Estructura de Datos: Cola (Queue)

El historial de conversación se gestiona con una **Cola FIFO** (First In, First Out):

- Capacidad máxima: **10 mensajes**
- Cuando se llena, el mensaje más antiguo se elimina automáticamente (dequeue)
- La cola completa se envía a la API de Claude como contexto de conversación
- Panel visual con 10 slots muestra el estado de la cola en tiempo real

```
Operaciones implementadas:
  enqueue(msg) → Agrega al final
  dequeue()    → Elimina el primero
  size()       → Cuenta los elementos
  isEmpty()    → Verifica si está vacía
```

---

## 🚀 Cómo usar

1. Clona el repositorio
2. Abre `index.html` en el navegador
3. Reemplaza `TU_API_KEY_AQUI` en el código por tu API key de Anthropic

### GitHub Pages
1. Sube el repo a GitHub
2. Settings → Pages → Branch: main → Save
3. Accede en: `https://tu-usuario.github.io/nombre-repo/`

---

## 📁 Archivos

```
/
├── index.html   → Chatbot completo con Cola implementada
├── README.md    → Este archivo
└── AGENTS.md    → Documentación de los agentes de IA utilizados
```

---

## ✅ Criterios de aceptación

- [x] Chatbot responde preguntas sobre ciberseguridad
- [x] Historial gestionado con Cola (Queue) FIFO
- [x] Panel visual del estado de la cola en tiempo real
- [x] Interfaz responsiva (desktop y móvil)
- [x] Publicado en GitHub Pages
- [x] Código con comentarios en español
- [x] Botones de temas rápidos

---

*Proyecto Final · Herramientas de IA · Universidad Cooperativa de Colombia · 2025*
