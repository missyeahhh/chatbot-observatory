# Rúbrica 1: accesibilidad

**v1.0, 23/8/2026.** Criterios propuestos por Claude, vetados y aprobados por Sol el mismo día.

Mide una sola cosa: **si una persona que no usa el mouse, o no ve la pantalla, puede abrir el chat, hablar y salir.**

Cada criterio se ancla a un criterio de éxito de WCAG 2.2, para que todo hallazgo cite norma y no opinión.

## Alcance, y por qué es un recorte

Entra lo que se puede probar desde una Mac con Safari, sin cuenta en el sitio y sin hardware adicional.

Fuera de alcance en v1, por costo, no por falta de interés:

- Lectores de pantalla en Windows (NVDA, JAWS). Son los más usados por personas ciegas, pero requieren una máquina Windows. Decidido por Sol el 23/8: v1 usa solo VoiceOver en Safari, y lo declara como límite en cada ficha.
- Navegación por voz y switch access.
- Modo oscuro y preferencias de movimiento reducido.

## Escala

Por criterio: **2 cumple, 1 parcial, 0 falla, n/a no se pudo probar.**

**Regla dura: `n/a` nunca se cuenta como 0.** El puntaje se expresa como "X sobre Y aplicables", nunca sobre un máximo teórico. Misma regla que la rúbrica 3.

## Los cinco criterios

### A1. Llegar y abrir por teclado

**Qué mide:** si el chat existe para quien navega con Tab.

**Prueba:** desde la barra de direcciones, Tab hasta el botón que abre el chat. Enter o Space. Ver dónde queda el foco.

| nota | condición |
|---|---|
| 2 | el launcher recibe foco, se abre con Enter o Space, y el foco entra al widget (campo de texto o primer control) |
| 1 | se abre, pero el foco queda afuera y hay que tabular hasta encontrarlo |
| 0 | el launcher no recibe foco, o recibe foco y no responde al teclado |

**Evidencia:** captura con el anillo de foco visible sobre el launcher, y cantidad de Tabs desde la barra de direcciones.

**WCAG:** 2.1.1 Keyboard, 2.4.3 Focus Order.

### A2. Salir sin quedar atrapada

**Qué mide:** si el widget devuelve el control.

**Prueba:** con el chat abierto, Esc. Después, Tab 20 veces seguidas. Después cerrar con el botón y ver dónde queda el foco.

| nota | condición |
|---|---|
| 2 | Esc cierra, Tab sale del widget hacia la página, y al cerrar el foco vuelve al launcher |
| 1 | se puede salir, pero solo por una de las vías, o el foco se pierde al cerrar (vuelve al inicio de la página) |
| 0 | el foco queda atrapado dentro del widget sin forma de salir por teclado |

**Evidencia:** transcript de teclas (Esc, Tab x N) y captura de dónde quedó el foco.

**WCAG:** 2.1.2 No Keyboard Trap.

### A3. Screen reader

**Qué mide:** si el chat se puede usar sin ver la pantalla.

**Prueba:** VoiceOver en Safari (Cmd + F5). Abrir el chat, mandar un mensaje, esperar la respuesta, recorrer los controles con VO + flecha derecha.

| nota | condición |
|---|---|
| 2 | el widget tiene nombre, la respuesta del bot se anuncia sola al llegar, y cada botón dice qué hace |
| 1 | se puede operar, pero falta una de las tres: sin nombre, o la respuesta no se anuncia y hay que ir a buscarla, o hay botones "button" sin etiqueta |
| 0 | VoiceOver no entra al widget, o lee el contenido como un bloque sin estructura |

**Evidencia:** grabación de audio o transcript de lo que VoiceOver lee, con el momento exacto de la respuesta del bot.

**WCAG:** 4.1.2 Name, Role, Value. 4.1.3 Status Messages.

**Límite declarado:** solo VoiceOver en Safari. Un resultado de 2 acá no garantiza NVDA ni JAWS.

### A4. Contraste y zoom

**Qué mide:** si el texto se lee con baja visión.

**Prueba:** medir el contraste del texto del bot y del texto del usuario contra su fondo con una herramienta (el inspector de Safari lo muestra en Elements > Styles, o cualquier contrast checker). Después, zoom del navegador al 200%.

| nota | condición |
|---|---|
| 2 | todo texto del chat a 4.5:1 o más, y al 200% no se corta ni se superpone nada |
| 1 | contraste cumple pero el 200% rompe el layout, o al revés |
| 0 | texto por debajo de 4.5:1 en las burbujas del bot o del usuario |

**Evidencia:** los valores medidos por cada tipo de texto, y captura al 200%.

**WCAG:** 1.4.3 Contrast (Minimum), 1.4.4 Resize Text.

### A5. Timeouts

**Qué mide:** si el tiempo juega en contra de quien es lento.

**Prueba:** escribir medio mensaje sin mandar. Dejar la sesión quieta 10 minutos. Volver.

| nota | condición |
|---|---|
| 2 | no vence, o avisa antes de vencer y deja extender, y lo escrito sigue ahí |
| 1 | vence sin aviso pero lo escrito y el historial siguen |
| 0 | vence sin aviso y se pierde lo escrito o el historial |

**Evidencia:** hora de inicio y de vuelta, captura del estado al volver.

**WCAG:** 2.2.1 Timing Adjustable.

## Lo que NO entra en esta rúbrica

- Si el bot entiende lo que se le dice. Eso es calidad de respuesta, no accesibilidad.
- Si la página que rodea al chat es accesible. Se audita el widget, no el sitio.

## Protocolo de corrida

1. **Safari limpio**, sin extensiones, ventana a 1280 px de ancho.

2. **Orden fijo:** A1, A2, A4, A5 en una sesión. A3 en otra sesión aparte, porque VoiceOver cambia cómo se comporta el foco y contaminaría A1 y A2.

3. **Una sola corrida alcanza.** A diferencia de la rúbrica 3, acá el comportamiento es determinista: el widget es el mismo código cada vez. Una falla se documenta con captura y no necesita segunda corrida.

4. **Captura de cada 0.** Sin captura no hay hallazgo.

## Costo

Entre 25 y 35 minutos por sitio, de los cuales 10 son la espera de A5, que corre en paralelo con otra cosa.

Para 6 a 8 sitios: **entre 3 y 4 horas.** Coincide con el bloque "Rúbricas 1 y 2" de `plan.md` solo si la rúbrica 2 se corre en la misma sesión por sitio, que es lo previsto.
