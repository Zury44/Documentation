# AssignedReportsScreen.tsx

Pantalla que muestra los reportes asignados al técnico.
Permite filtrar, visualizar detalles y redirigir para finalizar o ver un reporte específico.

---

## Descripción General

Este componente realiza las siguientes tareas:

* Obtiene la lista de reportes asignados al técnico desde el contexto global.
* Filtra los reportes para excluir los que están finalizados y para aplicar búsquedas.
* Muestra cada reporte como una tarjeta interactiva.
* Permite abrir un modal con opciones para ver detalles o finalizar el reporte.

---

## Hooks y Estado

* `useReports()` → contexto para obtener reportes asignados.
* `useRouter()` → navegación con `expo-router`.
* `useState()` para:

  * `searchText`: texto de búsqueda ingresado.
  * `modalVisible`: visibilidad del modal de detalles.
  * `selectedReport`: reporte actualmente seleccionado.

---

## Efectos

### useEffect()

```ts
useEffect(() => {
  fetchAssignedReports();
}, []);
```

Carga los reportes asignados al montar la pantalla.

---

## Filtrado de Reportes

```ts
const filteredReports = reports
  .filter((r) => r.status !== "Finalizado")
  .filter((report) => {
    const query = searchText.toLowerCase();
    return (
      String(report.id).toLowerCase().includes(query) ||
      report.property_name.toLowerCase().includes(query) ||
      report.lot_name.toLowerCase().includes(query) ||
      report.failure_type.toLowerCase().includes(query)
    );
  });
```

---

## Modal de Detalles

Se muestra al hacer clic en una tarjeta de reporte. Permite:

* Ver detalles del reporte (redirección a `/maintenance/reportDetails`).
* Finalizar el reporte (redirección a `/maintenance/formFinishReport`).

Se pasa el reporte seleccionado mediante el estado `selectedReport` y sus propiedades como parámetros.

---

## Componentes Utilizados

* `CustomHeader`: encabezado personalizado con botón para volver a Home.
* `SearchBar`: componente de entrada de texto para búsqueda.
* `ReportCard`: tarjeta con resumen del reporte.
* `ReportDetailsModal`: modal que presenta acciones sobre el reporte seleccionado.

---

Esta pantalla facilita al técnico la gestión diaria de sus reportes activos de mantenimiento de manera centralizada, eficiente y con acceso rápido a acciones clave.
