# CompletedReportsScreen.tsx

Pantalla que muestra los reportes de mantenimiento que ya han sido finalizados por el técnico.
Permite buscarlos, ver su información resumida y acceder a detalles completos.

---

## Descripción General

Este componente realiza las siguientes tareas:

* Obtiene los reportes desde el contexto global.
* Filtra los reportes para mostrar únicamente los finalizados.
* Permite buscar reportes por ID, lote, propiedad o tipo de falla.
* Muestra cada reporte como una tarjeta interactiva.
* Permite abrir la vista de detalles completos del reporte finalizado.

---

## Hooks y Estado

* `useReports()` → contexto para obtener reportes y función de carga.
* `useRouter()` → navegación con `expo-router`.
* `useState()` para:

  * `searchText`: texto de búsqueda ingresado por el usuario.

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
  .filter((r) => r.status === "Finalizado")
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

## Navegación a Detalles

Cada tarjeta permite ir a los detalles del reporte finalizado:

```ts
router.push({
  pathname: "/maintenance/completedReportDetails",
  params: {
    reportId,
    technicianAssignmentId,
    propertyName,
    lotName,
    fallo,
    observacion,
  },
});
```

---

## Componentes Utilizados

* `CustomHeader`: encabezado personalizado con botón para volver al Home.
* `SearchBar`: barra de búsqueda para filtrar reportes.
* `ReportCard`: tarjeta con resumen del reporte.
* `ActivityIndicator`: indicador de carga mientras se cargan reportes.

---

Esta pantalla facilita al técnico la consulta y revisión del historial de reportes de mantenimiento que ya han sido finalizados.
