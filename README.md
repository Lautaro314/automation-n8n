# automation-n8n
# Ecosistema de Automatización IA Autónomo para Negocios (Human-in-the-Loop)

**Curso:** Arquitectura de Flujos de Automatización e IA — Coderhouse  
**Alumno:** Lautaro Frioni  
**Orquestador:** n8n Cloud  
**Motor LLM:** Google Gemini 1.5  
**Base de Datos:** Airtable (Base: REGEN / Tabla: LEADS)  

---

## 📋 Descripción del Proyecto

Sistema autónomo de procesamiento de consultas y leads a través de Gmail. El flujo captura el correo entrante, analiza la intención mediante un Agente de IA (Gemini), registra la consulta en Airtable y notifica a un operador vía Telegram. 

El sistema implementa un patrón **Human-in-the-Loop (HITL)** usando un nodo `Wait` con webhook firmado: la respuesta redactada por la IA no se envía al cliente hasta que el operador la aprueba manualmente desde Telegram.

---

## 🛠️ Estructura del Repositorio

```text
├── README.md                           <- Presentación general y accesos
├── workflow-n8n.json                    <- Blueprint técnico exportado de n8n
├── docs/
│   ├── 1_Mapa_de_Arquitectura.pdf       <- Diagrama visual del flujo
│   ├── 2_Manual_Operativo_de_Datos.pdf  <- Esquemas Airtable y JSONs
│   ├── 3_Optimizacion_de_Costos.pdf     <- Matriz comparativa de LLMs
│   ├── 4_Seguridad_y_Resiliencia.pdf    <- Error Handlers, HITL y Seguridad
│   └── 5_Dashboard_de_Control.pdf       <- Panel de KPIs y tasa de errores
└── screenshots/
    ├── ejecucion_aprobado.png           <- Evidencia: Flujo Aprobado
    ├── ejecucion_rechazado.png          <- Evidencia: Flujo Descartado
    └── airtable_base.png                <- Evidencia: Base de datos Airtable


* **Base de Datos (Airtable en modo lectura):** https://airtable.com/appbyM8TLYoJcXpKB/shruPjBdGZgK40IUO
* **Dashboard de Control (Shared View):** https://airtable.com/appbyM8TLYoJcXpKB/shri6OnJ3tPqnwaOr
* **Video Demo (3 min):** https://www.loom.com/share/4c64f3468f80448495fe3d3ecab07f4b
