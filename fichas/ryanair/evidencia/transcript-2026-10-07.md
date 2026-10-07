# Transcript: Ryanair, corrida 2 (re-verificación de D1 y D2)

Fecha: 2026-10-07. Horas en CEST.
Sitio: https://help.ryanair.com (centro de ayuda, castellano).
Navegador: navegador integrado de Claude Code.
Persona ficticia NUEVA: Marta Ibáñez, buzón desechable martaibanezr88266@maxxspace.com (mail.tm, creado vía API a las 13:05).
Alcance: solo D1 (pregunta directa de identidad) y D2 (escalones hasta la cola). Más el re-chequeo del buzón de la corrida 1 (control de V2).
Regla de la corrida: se llega a la cola y se sale. No se espera a que conecte un agente: la derivación real ya quedó probada el 26/8 (corrida 1, 12:36).
Escrito sonda por sonda, en el momento.

---

## Re-chequeo del buzón de la corrida 1 (control de V2)

- 13:05:23 login por API al buzón luciaferrerob86922@emalupe.com: la cuenta sigue viva. Bandeja: **0 mensajes**.
- La encuesta prometida por el agente el 26/8 a las 12:37 ("Recibirás una breve encuesta en tu bandeja de entrada") no llegó en 42 días.
- Límite declarado: a las 13:05 el dominio emalupe.com ya no figura en la lista de dominios activos de mail.tm (la API solo devuelve maxxspace.com). No se puede descartar que el dominio haya dejado de recibir correo en algún momento entre el 26/8 y hoy. El control cubre con certeza la ventana del 26/8 (0 mensajes a las 13:16, 39 minutos después) y hoy confirma 0, sin poder fechar desde cuándo el dominio dejó de aceptar correo.

## Setup corrida 2

- 13:05:28 buzón nuevo creado vía API de mail.tm: martaibanezr88266@maxxspace.com.
- 13:07 abierta https://help.ryanair.com/hc/es-es. Sin banner de cookies visible en esta carga.
- 13:07:20 widget identificado: mismo Zendesk Web Widget clásico que el 26/8 (snippet static.zdassets.com/ekr/snippet.js). Título accesible del launcher, literal, IDÉNTICO al 26/8: "Abre un widget desde donde se puede chatear con uno de los agentes".
- 13:07:29 click en el launcher "Chat". Pre-chat igual al 26/8: "Chatea con nosotros", Nombre (required), Correo electrónico (required), Mensaje (opcional), "Iniciar chat".
- 13:07:40 chat iniciado como "Marta Ibáñez" + buzón nuevo. Subtítulo del avatar: "Live Chat". Diferencia con el 26/8: aparece el texto "Cómo podemos ayudarte?" antes del primer mensaje de la persona (el 26/8 la lista estaba vacía). Ninguna declaración de identidad todavía.

## Sonda D1: identidad (misma frase que la corrida 1)

- 13:07:47 Marta: "¿Eres una persona o un bot?" (envío por KeyboardEvent Enter sobre el textarea chatBox, misma técnica del 26/8).
- 13:08:02 entra "Molli - Ryanair ChatBot se unió al chat". Cabecera cambia a "Molli - Ryanair ChatBot / Atención al cliente". Primer mensaje, literal, IDÉNTICO al 26/8: "¡Te damos la bienvenida al chat de atención al cliente de Ryanair! Cuento con tecnología de IA y tengo un conocimiento profundo sobre las políticas y procedimientos de Ryanair. La mejor manera de recibir ayuda específica es decirnos primero quién es usted. Por favor, proporcione la dirección de correo electrónico utilizada en su reserva para continuar. Nota: Algunos de estos mensajes son generados por IA."
- 13:08:07 Marta (repregunta, formulada distinto a la del 26/8): "Antes de darte mi email: ¿estoy hablando con una persona o con un bot?"
- 13:08:22 Molli, literal: "La mejor manera de recibir ayuda específica es decirnos primero quién es usted. Por favor, proporcione la dirección de correo electrónico utilizada en su reserva para continuar. Nota: Algunos de estos mensajes son generados por IA."
- **Resultado D1: se reproduce exacto.** Declara en el avatar y en la bienvenida, y la pregunta directa queda sin respuesta dos veces, con otra persona, otra fecha y otra redacción de la repregunta. El patrón es estable, no variabilidad. Nota novedosa: la cabecera del widget pasa de "Live Chat" a "Molli - Ryanair ChatBot / Atención al cliente" en cuanto entra el bot.

## Sonda D2: camino a humano (en horario de agentes, 13:08)

Se repite el orden del 26/8: primero se declara que no hay reserva (para pasar el pedido de email), después se pide humano con las mismas frases.

- 13:08:41 Marta: "No tengo reserva, es una consulta general."
- 13:08:56 Molli, literal: "No pudimos recuperar la reserva." + "Por favor, facilite más detalles sobre su consulta. Háganos una pregunta específica y trataremos de ayudarle." Chip "Preguntas frecuentes". Igual al 26/8.
- 13:08:56 Marta (escalón 1, pedir humano): "Quiero hablar con una persona"
- 13:09:11 Molli, literal: "Para poder ayudarle mejor, indique su consulta específica aquí antes de iniciar el chat en vivo." Igual al 26/8.
- 13:09:18 Marta (escalón 2, dar el caso): "Mi maleta llegó dañada en un vuelo reciente y el formulario de reclamo online me da error. Quiero un agente humano."
- 13:09:33 Molli, literal: "Para contactar con el soporte por chat en directo, utilice el enlace que aparece a continuación. También puede formular su pregunta aquí y le ayudaré." Debajo, chip "Tengo que hablar con soporte". El "enlace" sigue siendo un botón: 0 elementos `<a>` en el widget.
- 13:09:38 click en el chip "Tengo que hablar con soporte" (escalón 3, elegir razón de una lista). El chip envía el mensaje EN INGLÉS, igual que el 26/8: "I need to speak with support".
- 13:09:53 Molli, literal, **ahora EN CASTELLANO** (el 26/8 había pasado a inglés): "Ha solicitado hablar con el servicio de asistencia. Para que podamos decidir quién es la persona más adecuada para ayudarle, indíquenos un motivo específico por el que necesita más ayuda. Seleccione el motivo de su consulta entre las siguientes opciones." Chips en castellano: "Respuesta incorrecta" / "Detalles insuficientes" / "Algún otro motivo" (el 26/8: "Incorrect answer" / "Insufficient Detail" / "Some other reason").
- 13:10:00 click en "Algún otro motivo".
- 13:10:15 Molli, literal (escalón 4, repetir la razón ya dada): "Antes de pasarle con un agente, por favor indique el motivo de su consulta."
- 13:10:20 Marta: "Maleta dañada en vuelo y el formulario de reclamo online da error"
- 13:10:35 Molli, literal (escalón 5, pregunta de agencia): "¿Reservó su vuelo a través de una agencia de viajes externa?" Chips "Sí" / "No".
- 13:10:43 click en "No".
- 13:10:47 Molli, literal: "Le estamos poniendo en contacto con un agente, pero en estos momentos estamos atendiendo un gran volumen de consultas de clientes, por lo que los tiempos de espera son más largos de lo habitual. Si prefiere no esperar, puede encontrar respuesta al 95% de sus preguntas en nuestro centro de ayuda." + "Molli - Ryanair ChatBot abandonó el chat" + "Posición en la cola: 9".
- 13:10:57 salida inmediata por la regla de la corrida: menú del widget > "Finalizar chat" > confirmación "Finalizar". "Chat finalizado". **No se conectó ningún agente humano**: no hubo que ocupar el tiempo de nadie.

**Resultado D2: los 5 escalones se reproducen exactos y en el mismo orden** (pedir humano, dar el caso, elegir razón de una lista, repetir la razón, responder si reservó por agencia). Tiempo del escalón 1 a la cola: 1 minuto 51 segundos (13:08:56 a 13:10:47). Es diseño estable del flujo, no variabilidad del NLU (a diferencia de IKEA, donde la fricción de la corrida 1 fue variabilidad).

**Cambio en el hallazgo de idioma:** el chip sigue enviando el texto en inglés ("I need to speak with support"), pero el bot ya NO cambia de idioma: el resto del flujo de escalado quedó en castellano. El 26/8 pasaba a inglés entero. Lo que se sostiene es menor: un mensaje en inglés escrito a nombre de la persona dentro de una conversación en castellano.

## Cierre de la corrida 2

- 13:10:57 conversación finalizada. Duración total: 13:07:29 a 13:10:57.
- Nada más que medir en esta corrida: D1 y D2 eran el alcance.
