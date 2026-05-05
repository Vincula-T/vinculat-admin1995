// ═══════════════════════════════════════════════════════════
// GOOGLE APPS SCRIPT - ADMIN1995 BACKEND
// ═══════════════════════════════════════════════════════════

function doGet(e) {
  const params = e.parameter;
  const accion = params.accion || '';

  try {
    switch(accion) {
      case 'admin':
        return ContentService.createTextOutput(
          JSON.stringify(cargarDatos())
        ).setMimeType(ContentService.MimeType.JSON);

      case 'cambiarEstado':
        cambiarEstado(params.id, params.estado);
        return ContentService.createTextOutput(
          JSON.stringify({ ok: true })
        ).setMimeType(ContentService.MimeType.JSON);

      // 🔴 NUEVO: Acción para actualizar monto
      case 'actualizarMonto':
        actualizarMonto(params.id, params.monto);
        return ContentService.createTextOutput(
          JSON.stringify({ ok: true })
        ).setMimeType(ContentService.MimeType.JSON);

      case 'crearVIP':
        // ... tu código existente ...
        break;

      case 'setPrecios':
        // ... tu código existente ...
        break;

      default:
        return ContentService.createTextOutput(
          JSON.stringify({ ok: false, error: 'Acción no válida' })
        ).setMimeType(ContentService.MimeType.JSON);
    }
  } catch(error) {
    return ContentService.createTextOutput(
      JSON.stringify({ ok: false, error: error.toString() })
    ).setMimeType(ContentService.MimeType.JSON);
  }
}

// ═══════════════════════════════════════════════════════════
// FUNCIÓN PARA ACTUALIZAR MONTO
// ═══════════════════════════════════════════════════════════

function actualizarMonto(id, monto) {
  const sheet = SpreadsheetApp.getActiveSheet();
  const data = sheet.getDataRange().getValues();
  const headers = data[0];

  // Encontrar el índice de la columna 'monto'
  const montoColIndex = headers.findIndex(h =>
    h.toString().toLowerCase().includes('monto')
  );

  if (montoColIndex === -1) {
    throw new Error('Columna "monto" no encontrada en la hoja');
  }

  // Buscar la fila con el ID coincidente
  for (let i = 1; i < data.length; i++) {
    if (String(data[i][0]).trim() === String(id).trim()) {
      // Actualizar el monto en la columna encontrada
      sheet.getRange(i + 1, montoColIndex + 1).setValue(monto);
      break;
    }
  }
}

// ═══════════════════════════════════════════════════════════
// FUNCIONES EXISTENTES (mantén las tuyas)
// ═══════════════════════════════════════════════════════════

function cargarDatos() {
  // Tu código existente...
}

function cambiarEstado(id, nuevoEstado) {
  // Tu código existente...
}

// ... agregar todas tus otras funciones ...
