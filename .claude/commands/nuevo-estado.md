# Nuevo Estado — Agregar un nuevo estado de prospecto al portal

El usuario quiere agregar un nuevo estado de prospecto al sistema. Sigue estos pasos:

## Paso 1: Identificar el nuevo estado
Pregunta al usuario (si no lo especificó en los argumentos):
- ¿Cuál es el nombre del nuevo estado? (e.g., "En tratamiento", "Cancelado", "Pausado")
- ¿Qué color debe tener la badge/etiqueta?
- ¿Desde qué estados puede transicionar a este nuevo estado?
- ¿Debe aparecer en el dashboard de KPIs?

## Paso 2: Leer el archivo actual
Lee `index.html` y ubica:
1. El array o lista donde se definen los estados posibles (busca `Disponible`, `Asignado`, `VIP`, `Garantía`)
2. La función que renderiza las cards/badges de estado
3. El filtro/selector de estados en la UI
4. El sistema de KPIs del dashboard

## Paso 3: Realizar los cambios
Agrega el nuevo estado en todos los lugares necesarios:
1. Lista de estados válidos / select de filtro
2. Lógica de renderizado de badge (color + etiqueta)
3. Estilos CSS si aplica (usando las variables CSS del sistema)
4. KPI dashboard si el estado debe contarse
5. Lógica de transición de estados si aplica

## Paso 4: Verificar consistencia
- Confirma que el nuevo estado no rompe los filtros existentes
- Verifica que los mensajes de WhatsApp manejen correctamente el nuevo estado
- Asegúrate de que la exportación/reporte incluya el nuevo estado si corresponde

## Convenciones del proyecto
- Colores de estado: usar las CSS variables ya definidas (--blue, --teal, --green, --amber, --red, --purple)
- Nombres de estado en español, primera letra mayúscula
- Los estados VIP y Garantía tienen lógica especial — no modificar sin revisar su flujo completo
