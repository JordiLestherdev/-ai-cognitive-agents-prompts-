### Contexto Simulado en n8n:
* Mensaje: "Hola, tengo mucha hambre, quiero algo salado y rápido, que no tenga carne."
* Intención: "busca_recomendacion"
* Preferencias: "vegetariano, salado"
* Inventario Inyectado: 
  - Ensalada César (Stock: 2, Etiquetas: vegetariano, fresco)
  - Macarrones con Queso Trufado (Stock: 45, Etiquetas: vegetariano, salado, caliente)
  - Hamburguesa de Res (Stock: 15, Etiquetas: carne, salado)

### Salida del LLM (JSON Generado):
{
  "platillo_seleccionado": "Macarrones con Queso Trufado",
  "respuesta_cliente": "¡Perfecto para ese antojo! Te recomiendo muchísimo nuestros Macarrones con Queso Trufado; están recién horneados, súper cremosos y con el toque perfecto de sal. ¿Te los agrego a tu orden para que salgan de inmediato?",
  "razonamiento_logico": "El usuario pidió algo salado y sin carne. Aunque la ensalada encaja, los macarrones coinciden perfectamente con 'salado' y 'vegetariano', y tienen un stock crítico de 45 unidades frente a las 2 de la ensalada, priorizando la rotación del inventario.",
  "requiere_accion_humana": false
}
