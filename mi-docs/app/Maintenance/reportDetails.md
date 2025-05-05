# ReportDetailsScreen.tsx

Pantalla que muestra los detalles completos de un reporte de mantenimiento. Incluye fechas, estado, ubicación y observaciones del fallo reportado.

---

## Descripción General

`ReportDetailsScreen`:

- Usa `useLocalSearchParams` para obtener el `reportId`.
- Llama al backend para traer detalles del reporte con `fetchReportDetail`.
- Muestra dos secciones principales: información general del reporte y detalles del usuario.
- Formatea fechas en formato colombiano.
- Usa componentes personalizados como `CustomHeader`.

---

## Funcionalidad

### fetchReportDetail()

- Realiza una petición `GET` a `/maintenance/reports/:id/detail`.
- Guarda el resultado en `report`.

### formatDate()

- Convierte una fecha ISO a formato `dd/mm/yyyy` para mostrar al usuario.

---

## Estado

```ts
const [report, setReport] = useState<ReportDetail | null>(null);
const [loading, setLoading] = useState(true);
```
---

## Layout Visual

La pantalla está dividida en:

1. **Card de información general del reporte:**
   - Estado con badge visual.
   - Fecha de revisión.
   - Fecha de finalización (si aplica).

2. **Card de datos del usuario reportante:**
   - Fecha del reporte.
   - Documento del propietario.
   - Predio y lote asociados.
   - Tipo de fallo y observaciones.

---

## Estilos

- Fondo blanco para cada card con padding y bordes redondeados.
- Badges visuales de estado con colores e íconos circulares.
- Tipografía basada en `typography` global.
- ScrollView para desplazamiento en pantallas largas.

---

## Navegación

```ts
router.push("/maintenance/assignedReports")
```

Usado como `backRoute` en el `CustomHeader`.

---

