# Entregable 2: Manual Operativo de Datos
**Proyecto:** Ecosistema IA n8n + Gemini | **Base:** Airtable (REGEN)

---

## 1. Diccionario de Datos — Tabla: LEADS

| Campo | Tipo de Dato | Opciones | Descripción y Uso en n8n |
| :--- | :--- | :--- | :--- |
| **NOMBRE** | Single line text | Requerido | Remitente extraído del encabezado `From`. |
| **Contacto** | Email | Formato Email | Dirección de correo del cliente para respuesta. |
| **Mensaje** | Long text | Texto Completo | Cuerpo original de la consulta enviada. |
| **Estado** | Single select | Nuevo, En proceso, Completado, Descartado | Estado del pipeline (Dashboard). |
| **Prioridad** | Single select | Alta, Media, Baja | Clasificación generada por el nodo AI Agent. |
| **Respuesta IA** | Long text | Rich Text | Borrador de respuesta generado por Gemini. |
| **Producto consultado** | Link to record | Relación -> PRODUCTO | Vinculación con el catálogo maestro. |

## 2. Payloads JSON de Transferencia de Datos

### Payload de Entrada (Gmail Trigger -> AI Agent):
json
{
"id": "19198a4f2e291bff6",
"from": "Lautaro Frioni lauti.tatengue@hotmail.com",
"subject": "Consulta por stock de zapatillas deportivas",
"body": "Hola buenas dias! Te consulto... tenés zapatillas deportivas Nike en talle 42?"
}

### Payload de Salida (AI Agent -> Airtable / Telegram):
json
{
"output": "Hola Lautaro, ¡buenos días! Contamos con zapatillas deportivas Nike en stock...",
"priority": "Alta",
"product_detected": "recR1QldLzT3DV9J9"
}


### Payload de Callback (Telegram -> Switch Node):
json
{
"query": {
"data": "action=approve&record_id=recAzss0UUWmgcgQf"
}
}

