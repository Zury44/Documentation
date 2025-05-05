# CompletedReportDetails.tsx

Pantalla de detalle para un reporte finalizado. Presenta toda la información relacionada al reporte, tanto del lado del usuario como del mantenimiento.

---

## Descripción General

Este componente realiza las siguientes tareas:

* Obtiene el `reportId` desde los parámetros de navegación.
* Llama a la API para obtener el detalle del reporte.
* Muestra la información dividida en secciones:

  * Estado y fechas del reporte.
  * Datos del usuario que reportó.
  * Información del fallo y evidencia.
  * Datos del mantenimiento realizado y su evidencia.
* Controla los errores de carga de imágenes.

---

## Hooks y Estado

* `useLocalSearchParams()` → obtiene `reportId` desde la ruta.
* `useState()` para:

  * `report`: datos del reporte.
  * `loading`: estado de carga inicial.
  * `failureImageError`: error al cargar imagen de fallo.
  * `solutionImageError`: error al cargar imagen de solución.
* `useEffect()` → carga el detalle al montar el componente.

---

## Función Auxiliar

### formatDate(dateString: string): string

Formatea una fecha ISO a formato colombiano (`dd/mm/yyyy`). Devuelve "No disponible" si no hay fecha.

---

## Secciones Visuales

### 1. Estado del Reporte

Incluye:

* Estado actual con badge.
* Fecha de revisión (`assignment_date`).
* Fecha de finalización (`finalization_date`).

### 2. Datos del Usuario

Incluye:

* Fecha del reporte original.
* Documento del propietario.
* Identificación del predio y lote.
* Posible fallo y observaciones.
* Evidencia fotográfica del fallo.

### 3. Datos de Mantenimiento

Incluye:

* Nombre del técnico.
* Tipo de mantenimiento.
* Observaciones del fallo y solución aplicada.
* Evidencia fotográfica de la solución.

---

## Comportamiento ante Errores

* Si falla la carga de imágenes, se muestra un mensaje alternativo.
* Si los datos del reporte no están disponibles, se muestra "No disponible".

---

Este componente proporciona una vista completa y clara del reporte finalizado, útil para ver el historial del trabajo realizado tanto por el usuario como por el equipo de mantenimiento.
