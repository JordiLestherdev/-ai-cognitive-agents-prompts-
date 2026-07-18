### Escenario 1: Solicitud Denegada (Fuera de tiempo)
* Datos Inyectados: Fecha Compra: 2026-05-10 | Fecha Actual: 2026-07-18 | Producto: Zapatos | Estado: Sin usar.

{
  "estado_resolucion": "denegado",
  "respuesta_cliente": "Hola. Entiendo que deseas devolver los zapatos. Lamentablemente, nuestra política permite devoluciones hasta 30 días después de la compra. Como tu orden es del 10 de mayo, el plazo ha expirado y no puedo procesar el reembolso. Lamento mucho los inconvenientes que esto te pueda causar.",
  "razonamiento_politica": "Denegado por Regla 1. Han pasado más de 60 días desde la Fecha de Compra (2026-05-10) hasta la Fecha Actual, excediendo la ventana permitida de 30 días."
}

### Escenario 2: Solicitud Escalada (Producto dañado de fábrica)
* Datos Inyectados: Fecha Compra: 2026-07-15 | Fecha Actual: 2026-07-18 | Producto: Licuadora | Estado: Dañado de fábrica.

{
  "estado_resolucion": "escalar_humano",
  "respuesta_cliente": "Siento muchísimo que tu licuadora haya llegado con daños de fábrica. Esto no es normal. Voy a transferir tu caso de inmediato a nuestro equipo de garantías para que te den una solución y programen el reemplazo o reembolso lo antes posible.",
  "razonamiento_politica": "Escalado por Regla 3. El producto está dentro de la ventana de 30 días, pero al ser reportado como 'dañado de fábrica', requiere revisión de un agente humano de garantías."
}
