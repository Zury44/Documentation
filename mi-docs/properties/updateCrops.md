# UpdateCrops.tsx

Pantalla para actualizar los datos del cultivo asociado a un lote dentro del proyecto de gestión de distritos de riego.

---

## Descripción General

Esta pantalla permite al usuario editar los detalles del cultivo de un lote previamente registrado. Se puede seleccionar el tipo de cultivo, visualizar su intervalo de pago, definir la fecha de siembra y calcular automáticamente la fecha estimada de cosecha. Todos los cambios se guardan tanto en el contexto local como en el backend.

---

## Hooks y Estados

- `useRouter`: para la navegación entre pantallas.
- `useLotContext`: para acceder y manipular la información del lote.
- `useEffect`: para cargar datos iniciales y sincronizar valores de cultivo.
- `useMemo`: para transformar los tipos de cultivo y sus metadatos en opciones seleccionables.

### Estados Locales

- `selectedCrop`: cultivo actualmente seleccionado.
- `plantingDate`: fecha de siembra seleccionada.
- `showDatePicker`: controla la visibilidad del selector de fecha.
- `estimatedHarvestDate`: fecha calculada estimada de cosecha.
- `isLoadingOptions`: indica si las opciones están siendo cargadas.

---

## Funciones Principales

### `onChangeCrop(value: string)`

Actualiza el cultivo seleccionado y recalcula la fecha estimada de cosecha.

### `onChangeDate(event, selectedDate)`

Maneja los cambios en la fecha de siembra y actualiza la fecha estimada de cosecha en consecuencia.

### `handleSave()`

Guarda los cambios localmente (en el contexto) y los sincroniza con el backend. Si la operación es exitosa, redirige a la pantalla de detalles del lote.

---

## Componentes Utilizados

- `CustomHeader`: cabecera personalizada con navegación.
- `DropdownPicker`: selector desplegable para tipos de cultivo.
- `CustomInput`: campo de entrada personalizado (varios en modo solo lectura).
- `DateTimePicker`: componente nativo para seleccionar fechas.
- `Button`: botón personalizado para guardar los cambios.
- `ActivityIndicator`: indicador de carga mientras se obtienen los datos.

---

## Navegación

- Ruta de regreso: `"/properties/detailsLot"` (cuando se presiona el botón de atrás o se guarda la información correctamente).
