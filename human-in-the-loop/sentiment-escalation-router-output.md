### Escenario 1: Conversación Normal (Continúa la IA)
* Mensaje Actual: "¿Tienen envíos a la región metropolitana?"
* Historial: "Hola bot" -> "Hola, soy el asistente"
* Segmento: Regular

{
  "sentimiento": "neutral",
  "ruta_asignada": "ai_agent",
  "mensaje_transicion": null,
  "razonamiento_enrutamiento": "Consulta general de envíos sin signos de frustración ni petición explícita de humano. Puede ser resuelta por la base de conocimientos."
}

### Escenario 2: Frustración y Bucle (Derivación Humana)
* Mensaje Actual: "No me sirve ese enlace, ya te dije que la página me da error al pagar, quiero hablar con alguien."
* Historial: "El pago falla" -> "Revisa este enlace" -> "Sigue fallando" -> "Intenta borrar cookies"
* Segmento: Regular

{
  "sentimiento": "frustrado",
  "ruta_asignada": "human_support",
  "mensaje_transicion": "Entiendo que esto es frustrante. Te voy a transferir en este momento con un especialista de nuestro equipo para que te ayude a completar el pago.",
  "razonamiento_enrutamiento": "Activación de Regla 1 (pide hablar con alguien explícitamente) y Regla 4 (bucle de falla en el pago documentado en el historial)."
}

### Escenario 3: Cliente VIP Enojado (Derivación Prioritaria)
* Mensaje Actual: "Es inaceptable, mi pedido llegó destruido."
* Historial: [Vacío]
* Segmento: VIP

{
  "sentimiento": "agresivo",
  "ruta_asignada": "priority_human_support",
  "mensaje_transicion": "Le pido mis más sinceras disculpas por este incidente. Lo estoy comunicando directamente a la línea prioritaria con un supervisor en este instante.",
  "razonamiento_enrutamiento": "Activación de Regla 3. El cliente es segmento VIP reportando un daño grave (sentimiento agresivo/frustrado extremo), requiere atención de Nivel 2 inmediata."
}
