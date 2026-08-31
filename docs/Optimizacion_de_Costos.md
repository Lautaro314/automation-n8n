# Entregable 3: Matriz de Optimización de Costos de IA
**Modelo Seleccionado:** Google Gemini 1.5 Flash (Google AI Studio)

---

## 1. Matriz Comparativa de Modelos LLM

| Modelo de IA | Costo Input (1M) | Costo Output (1M) | Latencia | Evaluación |
| :--- | :--- | :--- | :--- | :--- |
| **Gemini 1.5 Flash** | **$0.075 USD** | **$0.300 USD** | **~0.8s** | **SELECCIONADO:** Balance ideal velocidad/precio. |
| GPT-4o-mini | $0.150 USD | $0.600 USD | ~1.1s | 100% más costoso en input. |
| Claude 3.5 Sonnet | $3.000 USD | $15.000 USD | ~2.4s | Sobredimensionado (40x más costoso). |

## 2. Proyección Financiera por Volumen Mensual

| Volumen | Gemini 1.5 Flash | GPT-4o-mini | Claude 3.5 Sonnet | Ahorro vs. Claude |
| :--- | :--- | :--- | :--- | :--- |
| **1,000 Consultas** | $0.098 USD | $0.195 USD | $4.50 USD | **97.8% de Ahorro** |
| **10,000 Consultas** | $0.975 USD | $1.950 USD | $45.00 USD | **$44.02 USD / mes** |
| **50,000 Consultas** | $4.875 USD | $9.750 USD | $225.00 USD | **$220.12 USD / mes** |

## 3. Políticas de Eficiencia
1. **Límite de Tokens:** Configuración de `max_tokens: 300` para evitar respuestas extensas e imprevistos.
2. **Filtrado previo:** Descarte de mails automáticos antes de invocar la API del LLM.
