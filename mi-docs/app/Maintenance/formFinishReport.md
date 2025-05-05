# formFinishReport.tsx

## Descripción general

Este componente muestra un formulario de dos pasos para completar un reporte de mantenimiento, dividiendo la información en "Detalles del fallo" y "Detalles de la solución". Permite adjuntar archivos como evidencia, seleccionar opciones desde listas desplegables y enviar los datos al backend.

## Hooks y estados principales

* `useLocalSearchParams()`: recibe datos del mantenimiento (finca, lote, fallo, observaciones, etc.) desde la navegación.
* `useState(...)`: se usa para manejar el paso actual (`step`), datos seleccionados del formulario, archivos cargados y estado de carga.

## Estructura del formulario

* **Paso 1**: Muestra información del fallo e incluye un campo para subir evidencia (foto) del mismo.
* **Paso 2**: Permite seleccionar tipo de mantenimiento, solución, observaciones de la solución y subir evidencia (foto) de la solución.

## Componentes utilizados

* `DropdownPicker`: para seleccionar opciones (tipo de mantenimiento, solución).
* `CustomHeader`: encabezado con título y botón de regreso.
* `Button`: botón de siguiente, confirmar o volver.
* `TouchableOpacity` + `Image`: para mostrar archivos cargados y eliminar alguno si se desea.

## Validaciones

Antes de enviar:

* Se verifica que todos los campos requeridos estén completos.
* Se valida que las evidencias se hayan subido.
* Se limita el tamaño de archivo a 1MB.

## Lógica de envío (`handleSubmit`)

1. Se construye un `FormData` con los valores seleccionados y los archivos adjuntos.
2. Se hace un `POST` a `/maintenance/finalize`.
3. Si es exitoso, se redirige al listado de reportes asignados.

## Estilos

Los estilos están definidos en un objeto `StyleSheet`, utilizando constantes del `theme` y `typography`. Se aplican bordes redondeados, colores consistentes y espaciados adecuados.
