# Asistente de reservas con IA para centros de buceo

Boceto interactivo de un asistente de WhatsApp y web para centros de buceo y deportes acuáticos. Se abre `index.html` en el navegador: sin servidor, sin claves y con datos inventados.

**[▶ Probar la demo](https://miguelpalaciosgg.github.io/asistente-reservas-ia/)**

## Qué enseña
Cuatro conversaciones guionizadas en un móvil y, al lado, el panel **«Por dentro»** con lo que consulta el asistente antes de contestar:

| Conversación | Qué se ve |
|---|---|
| Bautizo · cliente nuevo | Precio desde el catálogo, plazas libres del sábado, enlace de reserva ya rellenado y reserva pagada con Bizum |
| Cliente que vuelve | Memoria por cliente: sabe su certificación, sus inmersiones y que prefiere la mañana |
| En inglés | Contesta en el idioma del cliente y el enlace abre la reserva en inglés |
| Pasar a una persona | Pregunta médica: el asistente no la contesta, avisa al centro y sigue una instructora |

## Cómo está pensado
- **Catálogo en vivo con tool use**: la IA no tiene los precios copiados en el prompt; llama a herramientas (`catalogo`, `huecos`, `presupuesto`) que leen la API pública del motor de reservas. Si cambia un precio o se llena una salida, el asistente lo sabe.
- **Memoria por cliente**: en WhatsApp por número de teléfono (lo da la API de Meta); en la web, por cookie. Resumen por conversación y borrado programado (RGPD).
- **Lleva a la reserva**: no cobra en el chat; manda el enlace del widget con actividad, día, hora y personas, y el pago va por la pasarela del centro (tarjeta o Bizum). La reserva queda marcada con origen «Asistente».
- **Paso a una persona**: herramienta `pasar_a_persona(motivo)` para salud, quejas, grupos o cuando el cliente lo pide; el bot se calla y el equipo sigue desde su panel.
- **Coste**: con un modelo pequeño (Claude Haiku), del orden de décimas de céntimo por conversación.

## Historia
La primera versión (2025) era un chatbot web en Node.js con Gemini y Firestore, con memoria de conversación por cliente y la información del centro en un JSON. Este boceto es el rediseño: catálogo en vivo en lugar de datos copiados a mano, WhatsApp, paso a persona y medición de reservas.

---
Centro, precios, nombres y enlaces de la demo son ficticios.
