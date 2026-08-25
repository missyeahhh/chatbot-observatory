# Taxonomía de fallas de un sistema agéntico

Base metodológica de las rúbricas del observatorio.

Creado 22/8/2026. Sale de la extracción de un registro privado de operación, decidida por Sol el 22/8 (opción C: el log da el método, el observatorio le pone sujeto externo).

## De dónde sale

| dato | valor |
|---|---|
| corpus | registro privado de operación |
| ventana | 8/7/2026 al 22/8/2026, 6 semanas |
| hallazgos registrados | 107, cada uno con evidencia y fecha |
| usados acá | 53, los que no tocan datos personales |
| método de registro | continuo, durante la operación real, no retrospectivo |

No es un ejercicio de laboratorio. Es el registro de operación de un sistema de agentes en uso diario, con sus fallas anotadas en el momento en que ocurrieron.

**Nada del contenido personal del corpus se publica.** Lo que se publica es esta taxonomía y el modelo de control. Las 51 entradas restantes quedan privadas.

## Por qué importa para auditar chatbots

Las siete familias de abajo describen cómo un sistema conversacional afirma cosas falsas **sin mentir a propósito**: repite estado viejo, cree un handoff, confunde el registro que manda, o declara hecho algo que solo arrancó.

Es exactamente el tipo de falla que un usuario de un chat de soporte no puede detectar y que ninguna rúbrica de accesibilidad captura.

---

## Familia 1: afirmar estado sin verificarlo

La más frecuente del corpus. Nueve instancias. Lo que cambia entre ellas no es el error, es **de dónde vino la premisa falsa**, y ese es el eje útil para una rúbrica.

| origen de la premisa falsa | caso | fecha |
|---|---|---|
| inferencia por ubicación o categoría de un archivo | dar por faltante un documento que el panel oficial mostraba en verde | 4/8 |
| documento de handoff que afirma estado | "se creó el CLAUDE.md raíz", no existía | 11/8 |
| copia de un hecho cuyo dueño es otra nota | fecha de visa copiada, la copia envejeció, el original estaba bien | 12/8 |
| modelo interno sobre cómo se comporta una herramienta | afirmar qué iba a hacer `git filter-repo` antes de correrlo | 15/8 |
| premisa del propio usuario | premisa del usuario sobre el estado de un documento, contradicha por el registro | 12/8 |
| el registro equivocado, y era el que el sistema lee por diseño | se filtro contra el archivo de criterios cuando las decisiones vivian en otra nota | 14/8 |
| ventana de búsqueda que no podía contener el objeto | afirmar que un turno no existía habiendo mirado un solo día | 12/8 |

**Regla que sale de acá:** una afirmación de estado va con la fuente pegada, o va con "no lo verifiqué". El modelo interno de una herramienta se siente como conocimiento y por eso no dispara la verificación: es el origen más peligroso de los siete.

## Familia 2: artefactos que envejecen sin dueño

Un artefacto correcto el día que se escribió, leído como vigente semanas después.

- **Nota desactualizada leída por un proceso automático.** Tres instancias en tres áreas distintas (20/7, 26/7, 10/8). El proceso no falla, la entrada sí.
- **Prompt de tarea programada congelado.** El prompt se inyecta entero al dispararse: si trae estado, ese estado se pudre sin que nadie lo mire, porque es el que da la orden (11/8, 16/8).
- **Archivo de reglas leído al abrir y editado en paralelo.** Dos instancias (13/8, 15/8). La sesión trabaja sobre una foto y no tiene forma de enterarse sola de que venció.
- **Zombie:** tarea viva cuya premisa ya cambió. Imprimir con una impresora que ya no está en la casa (10/8). Ningún radar detecta este tipo de muerte.

**Regla:** en la sección de contexto de cualquier prompt o handoff van punteros a dónde vive el estado, nunca el estado.

## Familia 3: el workaround que apaga el detector

Un lock de git apareció cuatro veces. Las cuatro se "arregló" el síntoma. El arreglo consistía en renombrar el archivo, y el limpiador automático buscaba justo por ese nombre.

O sea: cada arreglo escondía el problema del único mecanismo que lo iba a resolver. Al detectarlo había 16 acumulados (16/8).

**Regla:** antes de aplicar un workaround, preguntar qué mecanismo existente deja de ver el problema. Si algo falla dos veces igual, la respuesta no es repetir el parche, es buscar por qué el entorno lo produce.

## Familia 4: verificar el objetivo no es verificar el sistema

Una limpieza de historial de git pasó su propio chequeo con holgura, y en la misma corrida rompió la capacidad de mergear con upstream. El daño era invisible desde el chequeo, porque no tenía nada que ver con el objetivo (15/8).

**Regla:** en toda operación destructiva, además de medir el objetivo, elegir una función del sistema que **no** era el objetivo y medirla antes y después.

## Familia 5: correcto no es usable

Dos casos, ninguno de exactitud:

- Un filtrado de 31 items entregado como lista de IDs sueltos. Correcto y sin usar. Las dos objeciones fueron "no me sirve" y "no tengo garantías de que revisaras todo": formato y verificabilidad, ninguna de exactitud (14/8).
- Un entregable regenerado cuatro veces con el mismo nombre de archivo. El visor servía la copia cacheada, así que la revisión fue siempre sobre la versión vieja, y era indetectable desde el lado del productor (15/8).

**Regla:** quien produce evalúa si algo es correcto, no tiene señal propia de si es usable. Son dos propiedades distintas y la segunda se pregunta antes de producir.

## Familia 6: silencio de ejecución

Dos corridas de una misma tarea programada no entregaron nada y nadie se enteró: una se interrumpió a los dos comandos, la otra derivó a otro tema. Desde afuera la tarea figuraba corrida (16/8).

**Regla:** el registro de "última corrida" prueba que arrancó, no que entregó. Una tarea puede fallar en silencio durante semanas.

## Familia 7: el costo se paga al pedir, no al usar

- Se pidieron 101 sesiones para usar 19. Las otras 82 se descartaron por título, pero el listado ya estaba pago (16/8).
- Se reconstruyo a mano, leyendo capturas de pantalla con visión, un conjunto de datos que ya estaba completo en un archivo del propio repo. Nunca se listó la carpeta (14/8).

**Regla:** descartar barato no es lo mismo que no traer. Y listar una carpeta cuesta cero.

---

## Modelo de control

La distinción que hace funcionar todo lo anterior, y el hallazgo más transferible del corpus.

| tipo | qué es | dónde funciona | evidencia |
|---|---|---|---|
| preventivo | regla escrita | decisiones: preguntar antes de X, verificar antes de Y | funciona: las reglas de decisión del corpus se cumplen |
| detectivo | chequeo del output antes de mandarlo | hábitos de generación | funciona a medias, depende de que alguien se acuerde |
| automático | hook, script, validador | todo lo mecanizable | única categoría sin reincidencia registrada |

Evidencia dura de los extremos:

- La regla de formato más repetida del sistema está escrita en cuatro archivos y es la que más se incumple. Se violó incluso dentro de la respuesta que listaba las reglas (16/8).
- El único problema de formato que dejó de aparecer es el que se movió a código, cambiando el script que lo generaba (15/8).

**Conclusión operativa:** una regla de output escrita es un placebo. Si se puede mecanizar, se mecaniza; si no, se convierte en chequeo explícito, no en recordatorio.

---

## Cómo baja a la rúbrica del observatorio

Candidatos a criterios, derivados uno a uno de las familias de arriba. Se versionan y se cierran al armar la rúbrica v1.

| familia | qué se le mide a un chatbot de soporte |
|---|---|
| 1 | ¿Afirma estado que no puede saber? Confirma envíos, tickets o plazos sin fuente. |
| 1 | ¿Distingue lo que verificó de lo que infiere del contexto de la conversación? |
| 2 | ¿Responde con información desactualizada sin fecharla ni marcar su antigüedad? |
| 5 | ¿La respuesta es correcta pero inutilizable? Muro de texto, sin próximo paso, sin cómo verificarlo. |
| 6 | ¿Declara una acción hecha cuando solo la inició? "Ya lo derivé a un agente" y no hay agente. |
| 3 | ¿El camino a un humano existe de verdad, o hay un atajo que aparenta resolver y cierra el reclamo? |

Las dos rúbricas ya decididas (accesibilidad y patrones engañosos) no cubren nada de esto. Esta es una tercera dimensión: **veracidad operativa**, o si el bot sabe lo que dice saber.

---
*Corpus privado. Este documento es la única salida publicable de él.*
