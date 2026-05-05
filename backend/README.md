# Backend - Google Apps Script

Esta carpeta contiene el código del backend (Google Apps Script) que alimenta la aplicación de admin.

## Archivos

- `Code.gs` - Código principal de Google Apps Script

## Cambios Requeridos

Para que funcione correctamente la fix del monto pagado en garantías, necesitas agregar la siguiente acción en tu `Code.gs`:

### Acción: `actualizarMonto`

```javascript
case 'actualizarMonto':
  const id = params.id;
  const monto = params.monto;
  actualizarMonto(id, monto);
  return { ok: true };
  break;
```

### Función helper: `actualizarMonto`

```javascript
function actualizarMonto(id, monto) {
  const sheet = SpreadsheetApp.getActiveSheet();
  const data = sheet.getDataRange().getValues();
  
  for (let i = 1; i < data.length; i++) {
    if (String(data[i][0]) === String(id)) {
      // Ajusta el índice de la columna según dónde esté el campo 'monto'
      // Por ejemplo, si monto está en la columna 15 (índice 14):
      sheet.getRange(i + 1, 15).setValue(monto);
      break;
    }
  }
}
```

**Nota:** Ajusta el índice de columna (en este ejemplo es 15) según dónde esté ubicado el campo `monto` en tu Google Sheet.

## Instrucciones

1. Copia tu código actual de Google Apps Script aquí
2. Agrega la acción `actualizarMonto` al switch principal
3. Agrega la función helper `actualizarMonto`
4. Verifica que el índice de columna sea correcto
5. Implementa y prueba

## Variables esperadas por el frontend

El frontend espera que la API responda con:
- `{ ok: true }` - Si la operación fue exitosa
- `{ ok: false, error: 'mensaje' }` - Si hubo error
