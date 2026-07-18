# 🧠 AI Cognitive Agents - Prompt Engineering Patterns

Este repositorio es una colección documentada de los patrones de ingeniería de prompts, arquitecturas de contexto y guardrails que utilizo para diseñar agentes cognitivos en entornos de producción (principalmente integrados con automatizaciones en **n8n** y flujos *Human-in-the-Loop*).

> **Nota de Privacidad:** La lógica de negocio específica y los nombres de empresas en los archivos han sido abstraídos para proteger la confidencialidad de la arquitectura real de los clientes.

## 🏗️ Metodología de Diseño

Todos los prompts en este repositorio están estructurados para interactuar directamente con código o plataformas de orquestación, priorizando la consistencia y la seguridad sobre la creatividad libre.

### Patrones Base Aplicados
* **Structured Output Pattern:** Se fuerza a los modelos a devolver respuestas en formatos programáticos estrictos (ej. JSON) para permitir el enrutamiento lógico en los siguientes nodos del flujo.
* **Template Pattern:** Se utiliza inyección de variables (como `{{datos}}`) para pasar el contexto dinámico al modelo.
* **Chain of Thought (CoT):** Se obliga a los agentes a generar un `"razonamiento"` en su salida JSON antes de emitir una decisión, reduciendo las alucinaciones.

### Guardrails (Reglas de Seguridad) Implementados
1. **Comerciales:** Prohibición explícita de inventar precios o cerrar tratos sin validación humana.
2. **De Formato:** Instrucciones negativas para evitar que la IA rompa el análisis de datos (ej. prohibición de Markdown alrededor de los objetos JSON).
3. **Escalamiento:** Reglas claras para derivar la conversación a un operador humano en caso de complejidad o frustración del usuario.

---

## 📂 Directorio de Agentes y Patrones

A continuación, se listan los prompts organizados por su caso de uso dentro de un embudo de negocio o ecosistema e-commerce.

### 💼 Ventas y Cualificación (Lead Scoring)
Agentes diseñados para actuar como primer filtro en embudos de adquisición, evaluando la viabilidad técnica y comercial del prospecto.
* 🤖 [Agente de Cualificación de Leads B2B](./sales-and-qualification/lead-qualification-agent.md): Analiza el mensaje, extrae datos, califica al lead (Scoring) y devuelve el resultado en JSON para su ruteo en n8n.

### 🎧 Soporte al Cliente (E-commerce)
Agentes enfocados en la resolución rápida de dudas logísticas y operativas utilizando inyección de contexto RAG (Retrieval-Augmented Generation).
* 📦 [Agente de Soporte y Seguimiento de Órdenes](./customer-support/order-tracking-agent.md): Traduce datos crudos del ERP/E-commerce usando RAG, aplica políticas de tienda y detecta frustración (análisis de sentimiento) para escalar a operadores humanos.
* 🔄 [Asistente de Políticas de Reembolso](./customer-support/refund-policy-assistant.md): Motor lógico que evalúa reglas de negocio estrictas (tiempos de compra, categorías excluidas) para aprobar, rechazar educadamente o escalar devoluciones de productos.
)*

### 🍽️ Hospitalidad y Retail (Retail & Hospitality)
Agentes diseñados para maximizar el ticket promedio y optimizar la rotación de inventario en tiempo real (Yield Management).
* 🍔 [Agente de Recomendación Gastronómica](./hospitality-and-retail/restaurant-recommendation-agent.md): Cruza intenciones y preferencias del usuario con bases de datos de inventario POS, priorizando proactivamente artículos con alto stock sin perder la naturalidad conversacional.

### 🔄 Human-in-the-Loop (HITL)
Prompts especializados en el análisis de sentimiento y orquestación de transiciones seguras entre la IA y los operadores humanos.

* 🚦 [Enrutador de Escalamiento por Sentimiento](./human-in-the-loop/sentiment-escalation-router.md): Actúa como "semáforo inteligente". Analiza el tono del cliente, el historial de fallos del bot y el segmento (ej. VIP) para derivar la conversación a un operador humano antes de generar una mala experiencia.
* 
