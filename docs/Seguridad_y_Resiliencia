# Entregable 4: Documentación de Seguridad y Resiliencia
**Estándar:** GDPR Compliant / HITL Validated

---

## 1. Minimización de Datos y Privacidad
* **Filtrado de Payloads:** Solo se transmite al LLM el texto del mensaje (`Mensaje`), omitiendo metadatos sensibles.
* **Privacidad de API:** API empresarial de Google AI Studio con garantía de no uso de datos para reentrenamiento.

## 2. Manejo de Errores (Error Handling) en Airtable
* **Typecasting Activado:** `options.typecast = true` para procesar saltos de línea y Markdown sin fallar.
* **Identificador Único Nativo:** Búsqueda y actualización por `record_id` nativo (`rec...`) de Airtable para prevenir escrituras cruzadas.

## 3. Mitigación del "Efecto Metralleta" (Protocolo HITL)
1. **Aislamiento:** La IA nunca responde directamente al cliente; crea una propuesta guardada en borrador.
2. **Notificación:** Envío del borrador al canal de Telegram para auditoría del operador.
3. **Congelamiento (Wait):** El flujo retiene el execution state sin agotar tiempos de timeout.
4. **Despacho:** Salida de correo habilitada únicamente tras recibir la interacción directa del botón `[Aprobar]`.
