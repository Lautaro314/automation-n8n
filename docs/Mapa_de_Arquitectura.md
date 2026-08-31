# Entregable 1: Mapa de Arquitectura del Sistema
**Proyecto:** Ecosistema IA n8n + Gemini
**Autor:** Lautaro Frioni | **Fecha:** Agosto 2026

---

## 1. Resumen Ejecutivo del Flujo
El sistema implementa una arquitectura modular de automatización desacoplada y orientada a eventos. Su propósito principal es procesar solicitudes entrantes de clientes a través de correo electrónico (Gmail), procesar su intención utilizando Google Gemini 1.5 Flash, persistir los estados transaccionales en una base de datos dinámica (Airtable) y someter las respuestas redactadas a una validación humana previa (Telegram HITL) antes de su despacho final.

## 2. Diagrama de Arquitectura Lógica

| Fase | Nodo n8n / Componente | Tecnología / API | Función Operativa |
| :--- | :--- | :--- | :--- |
| **1. Entrante** | Gmail Trigger | OAuth 2.0 / Gmail API | Disparador pasivo por webhook que captura correos en tiempo real. |
| **2. Razonamiento** | AI Agent + Gemini Model | Google Gemini 1.5 Flash | Extrae entidades, analiza intención y redacta propuesta comercial. |
| **3. Persistencia 1** | Create a record | Airtable API (Base REGEN) | Crea fila inicial en la tabla `LEADS` con estado "Nuevo". |
| **4. Notificación** | Send a text message | Telegram Bot API | Envía alerta al operador con propuesta y botones [Aprobar] / [Rechazar]. |
| **5. Pausa HITL** | Wait Node | n8n Webhook Listener | Detiene la ejecución del flujo de forma asíncrona a la espera de firma. |
| **6. Evaluación** | Switch Node | n8n Internal Logic | Bifurca el camino según la decisión tomada (Aprobado / Rechazado). |
| **7. Aprobado** | Send Email + Update Record | Gmail API + Airtable API | Envía correo al cliente y actualiza Airtable a "Completado". |
| **8. Rechazado** | Update Record | Airtable API | Actualiza Airtable a "Descartado" sin despachar correo. |

## 3. Componentes Clave de la Arquitectura
* **Trigger Inteligente:** En lugar de hacer *polling*, se utiliza un trigger de eventos directos para reducir ejecuciones en inactividad.
* **Motor de Razonamiento:** Procesa dinámicamente `{{ $json.body }}` reduciendo alucinaciones mediante instrucciones del sistema.
* **Human-in-the-Loop:** El nodo `Wait` congela la ejecución hasta recibir el callback firmado desde Telegram.
