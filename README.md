# Ecosistema de Automatización IA Autónomo para Negocios

Proyecto final integrador que implementa un flujo automatizado de extremo a extremo para la gestión y validación de reservas, combinando procesamiento de lenguaje natural, memoria relacional, control de errores y validación humana (HITL).

## 🚀 Stack Tecnológico Utilizado
* **Orquestador:** Make (Escenarios automatizados con ruteo condicional).
* **Base de Datos / Memoria:** Airtable (Gestión de registros, estados y control relacional).
* **Procesamiento de IA:** Google Gemini AI (Extracción estructurada de lenguaje natural desde correos).
* **Canal de Salida:** Gmail API (Notificaciones automatizadas y alertas de control).

---

 1. Arquitectura del Sistema
El diagrama completo de arquitectura detallando triggers, enrutadores, APIs y nodos de IA se encuentra disponible en formato PDF en el archivo [`arquitectura_final.pdf`](./arquitectura_final.pdf).

### Componentes Clave:
1. **Trigger Inteligente:** Monitoreo activo de la bandeja de entrada de Gmail mediante *Watch Emails*.
2. **Cerebro (IA):** Extracción automatizada de variables críticas (`nombre_cliente`, `email_cliente`, `fecha_hora`, `# comensales`) utilizando Google Gemini.
3. **Memoria (Airtable):** Almacenamiento persistente con un campo de control de estados para gobernar el flujo de las reservas.
4. **Resiliencia:** Incorporación de un manejador de errores tipo *Resume* ante fallos en las conexiones.
5. **Human-in-the-Loop (HITL):** El sistema detiene las acciones críticas enviando una alerta interna, requiriendo que un operador valide y actualice el estado en Airtable antes de emitir la respuesta definitiva al cliente.



 2. Matriz de Costos y Optimización de Modelos

| Tarea del Proceso | Modelo de IA Seleccionado | Justificación Técnica de la Elección | Costo Estimado (Por 1M de Tokens) | Ahorro / Beneficio Operativo |
| :--- | :--- | :--- | :--- | :--- |
| **Procesamiento de Lenguaje Natural (NLP)** <br> *(Extracción de datos del correo de reserva)* | **Google Gemini Flash / Pro** | Ideal para tareas de extracción rápida y estructuración de texto no estructurado. Ofrece una excelente ventana de contexto con baja latencia. | Bajo (aprox. $0.07 - $0.50 USD por millón de tokens de entrada) | **70% de ahorro** frente a modelos pesados, optimizando la ejecución en Make para volumen medio. |
| **Análisis Masivo o Lotes (Batch)** <br> *(Opcional para auditoría o reportes)* | **Google Gemini Flash (Modo Batch)** | Pensado para procesar registros históricos o logs acumulados en Airtable fuera de hora pico. | Tarifa reducida al 50% en llamadas por lotes. | **50% de reducción adicional** en costos operativos a escala. |
| **Tareas Complejas de Razonamiento** <br> *(Validación de políticas o excepciones)* | *No requerido / Descartado* | Para este flujo transaccional de reservas, un modelo de razonamiento avanzado implicaría un costo innecesario de hasta 10 veces más por token. | Alto ($3.00 - $15.00 USD por millón de tokens) | Evita el sobrecosto innecesario en tareas repetitivas y estructuradas. |

> **Conclusión de Costos:** Para este ecosistema se seleccionó la familia de modelos **Google Gemini** a través de Make por su alta eficiencia. Al tratarse de un flujo transaccional de extracción de datos de reservas, Gemini Flash ofrece la velocidad y precisión requeridas con un costo por token significativamente menor que alternativas de alta gama, garantizando la viabilidad económica del proyecto.



 Enlaces y Evidencias
* **Blueprint del Escenario:** Disponible en el archivo [`blueprint_final.json`](./blueprint_final.json).
* **Evidencias Visuales:** Capturas del funcionamiento del escenario y la base de datos disponibles en el repositorio.
*  **LINK AIRTABLE: https://airtable.com/invite/l?inviteId=invun0YuHjKONikW0&inviteToken=9cd73b7e3385f24eb281a7da537c1e1e6bff938f90dd13054725902d3381d90a&utm_medium=email&utm_source=product_team&utm_content=transactional-alerts
