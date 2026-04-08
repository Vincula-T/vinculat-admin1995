# Garantía — Gestionar el flujo de garantías del portal

Este skill ayuda a trabajar con el flujo especial de garantías (casos donde un tratamiento falló y debe reasignarse a otro alumno).

## Contexto del flujo de garantías
- Un prospecto de garantía tiene en `alumnoAsignado` el valor: `[GARANTÍA:folio_malo] Nombre Alumno`
- El folio de garantías usa el prefijo `GAR-###` en lugar de `VIN-###`
- La card se renderiza con badge ámbar "SOLICITUD DE GARANTÍA"
- El botón muestra "Aprobar Garantía" en lugar de "Validar pago"
- Existe un mensaje de seguimiento al paciente preguntando si fue contactado

## Usos posibles de este skill

### A) Revisar el flujo completo de garantías
Lee `index.html` y audita:
1. Detección del tag `[GARANTÍA:folio]` en `alumnoAsignado`
2. Renderizado especial de la card (badge, color ámbar, evidencia)
3. Función "Aprobar Garantía" — qué hace exactamente al aprobar
4. Mensaje de seguimiento WhatsApp al paciente
5. Vinculación entre el caso malo (folio original) y el caso garantía (GAR-###)
6. Actualización del estado del prospecto original tras aprobar la garantía

### B) Modificar la lógica de aprobación de garantía
Si el usuario quiere cambiar cómo funciona "Aprobar Garantía":
- Lee la función actual de aprobación
- Identifica qué datos se envían al Google Apps Script
- Verifica que el prospecto original quede en estado correcto tras la aprobación
- Confirma que se notifica tanto al alumno nuevo como al paciente

### C) Agregar validaciones al flujo de garantía
Verifica que:
- No se puede aprobar una garantía sin evidencia (comprobante/foto)
- El folio referenciado en `[GARANTÍA:folio]` existe en el sistema
- No se puede crear una garantía de una garantía (GAR de GAR)
- El alumno asignado en la garantía es diferente al alumno original fallido

### D) Depurar un caso específico de garantía
Si el usuario proporciona un folio (e.g., GAR-042), ayuda a:
- Rastrear el flujo completo del caso
- Identificar en qué paso está atascado
- Sugerir la corrección en el código o en los datos

## Formato del tag de garantía
```
alumnoAsignado: "[GARANTÍA:VIN-015] María González López"
```
- `VIN-015` es el folio del caso original que falló
- `María González López` es el nuevo alumno asignado para cubrir la garantía

## Entregable
Describe el estado actual del flujo, los problemas encontrados (si los hay), y las correcciones recomendadas con líneas de referencia en `index.html`.
