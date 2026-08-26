# Guion único: accesibilidad IKEA + Ryanair

Una sola sentada. Safari limpio, sin extensiones, ventana a 1280px.

Corrección 27/8: Ryanair A1, A2, A4 y A5 ya se corrieron a mano el 26/8, en la sesión que se cortó dos veces (ver `handoff-2026-08-26-piloto-ryanair-parcial.md`). No se repiten. Solo falta A3.

## Bloque 1: sin VoiceOver (A1, A2, A4, A5)

Solo IKEA. Ryanair ya está corrido, resultados en el handoff del 26/8, listos para volcar a `ficha.md`.

- [ ] A1. Tab desde la barra de direcciones hasta el launcher. Enter o Space. ¿Dónde queda el foco?
- [ ] A2. Chat abierto, Esc. Tab x20. Cerrar con botón. ¿Dónde queda el foco?
- [ ] A4. Contraste (Elements > Styles o contrast checker) + zoom 200%.
- [ ] A5. Escribir medio mensaje sin mandar. Dejar 10 min quieto. Volver.

### Referencia: lo que ya dio Ryanair en A1, A2, A4, A5 (no repetir)

- A2: de las dos vías de salida solo funciona Esc. Minimizar deja el foco en un elemento sin acción.
- A4 contraste: todo por encima de 4.5:1 (mínimo 4.84:1).
- A4 zoom: **layout roto al 200%**, texto cortado y escondido. Literal tuyo: "imposible usar así".
- A1 y A5: registrados con tus palabras literales en el transcript, faltan pasar a la ficha.

## Bloque 2: con VoiceOver (A3)

Separado del bloque 1 a propósito: VoiceOver cambia el foco y contamina A1/A2 si se mezcla en el mismo sitio. Entre sitios distintos no hay ese problema, por eso van juntos acá.

Cmd + F5 para activar VoiceOver.

### IKEA

- [ ] Abrir el chat, mandar un mensaje, esperar respuesta.
- [ ] Recorrer controles con VO + flecha derecha.
- [ ] ¿Tiene nombre el widget? ¿Se anuncia sola la respuesta? ¿Cada botón dice qué hace?

### Ryanair

- [ ] Mismo procedimiento que IKEA.

Cmd + F5 de nuevo para desactivar VoiceOver al terminar.

## Al cerrar

- Cada 0 necesita captura, si no no hay hallazgo.
- Volcar resultados a `fichas/ikea/ficha.md` (Rúbrica 1) y `fichas/ryanair/ficha.md` (cuando exista).
- Costo estimado: 30 a 40 min total (IKEA completo 25-35, más A3 de Ryanair solo, 5-10 min).

Fuente del método: `metodo/rubrica-accesibilidad.md`.
