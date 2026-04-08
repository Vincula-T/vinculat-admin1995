# Mensaje WhatsApp — Crear o actualizar plantillas de mensajes

El usuario quiere crear o modificar un mensaje de WhatsApp del portal. El sistema tiene tres tipos de mensajes:
1. **Al alumno** — Notifica al estudiante su nueva asignación con datos del paciente
2. **Al paciente** — Confirma al paciente que fue asignado con datos del alumno
3. **Seguimiento garantía** — Pregunta al paciente si el alumno lo contactó (flujo de garantía)

## Paso 1: Determinar qué mensaje se quiere modificar
Si el usuario no especificó en los argumentos, pregunta:
- ¿Es un mensaje nuevo o modificación de uno existente?
- ¿A quién va dirigido: alumno, paciente, o seguimiento de garantía?
- ¿Qué información nueva se quiere incluir o cambiar?

## Paso 2: Leer el código actual
Lee `index.html` y busca las funciones de generación de mensajes WhatsApp. Identifica:
- Dónde se construyen las URLs `wa.me/`
- Qué variables del prospecto se usan en cada mensaje (nombre, tratamiento, horario, etc.)
- Cómo se codifica el texto para URL (encodeURIComponent)

## Paso 3: Variables disponibles en un prospecto
Las siguientes propiedades están disponibles al construir un mensaje:
- `prospecto.nombre` — Nombre del paciente
- `prospecto.telefono` — Teléfono del paciente
- `prospecto.tratamiento` — Tipo de tratamiento
- `prospecto.horario` — Horario (mañana/tarde)
- `prospecto.alumnoAsignado` — Nombre del alumno
- `prospecto.telAlumno` — Teléfono del alumno
- `prospecto.expediente` — Número de expediente
- `prospecto.id` / folio VIN-### o GAR-###

## Paso 4: Implementar el cambio
- Modifica o agrega la plantilla de mensaje en la función correspondiente
- Asegúrate de que el texto esté codificado con `encodeURIComponent()`
- Mantén el tono profesional y claro para comunicación clínica dental
- Si es un mensaje nuevo, agrega el botón correspondiente en la UI de la card

## Buenas prácticas
- Incluir siempre el folio del caso (VIN-### o GAR-###) para trazabilidad
- El saludo debe ser personalizado con el nombre del destinatario
- Verificar que `telAlumno` y `telefono` tengan formato internacional (52XXXXXXXXXX) antes de armar la URL
- Mensajes de garantía deben ser empáticos y ofrecer alternativas claras al paciente
