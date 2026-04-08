# Review Portal — Revisión del flujo de asignación de prospectos

Lee el archivo `index.html` completo y realiza una revisión enfocada en:

## 1. Flujo de asignación de prospectos
- Verifica que las transiciones de estado sean correctas: Disponible → Asignado → Pago enviado → validado
- Detecta condiciones donde un prospecto podría quedar en un estado inconsistente
- Revisa si hay casos borde no manejados (e.g., prospecto ya asignado siendo reasignado)

## 2. Flujo de garantías
- Verifica la detección del tag `[GARANTÍA:folio]` en el campo `alumnoAsignado`
- Confirma que el renderizado de tarjetas de garantía (`GAR-###`) es correcto
- Revisa que el botón "Aprobar Garantía" dispara la lógica adecuada

## 3. Mensajes de WhatsApp
- Revisa los tres tipos de mensajes (alumno, paciente, seguimiento garantía)
- Verifica que los números de teléfono se formateen correctamente para `wa.me/`
- Detecta casos donde el mensaje podría enviarse con datos vacíos o faltantes

## 4. Lógica de precios
- Verifica que el cálculo de precio considere todos los factores: tratamiento, horario, extracciones, aparato, edad
- Detecta posibles divisiones por cero o valores undefined

## 5. Bugs visuales / UX
- Revisa que los overlays se cierren correctamente
- Verifica que las cards de estado VIP, Garantía, Disponible, etc. muestren el badge correcto

## Entregable
Reporta los hallazgos organizados por sección. Para cada problema encontrado, indica:
- Descripción del bug o riesgo
- Línea aproximada en el archivo
- Sugerencia de corrección
