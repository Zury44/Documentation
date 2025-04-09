### `DetailsLots`

## Componente que muestra información detallada de un lote seleccionado. Permite cambiar entre una vista de cultivo y una vista de dispositivos, e incluye una barra de búsqueda animada para filtrar los dispositivos disponibles.

#### **Descripción general**

- Proporciona detalles del lote, incluyendo su nombre, extensión, ubicación y número de folio.
- Permite editar información del cultivo asociado.
- Ofrece una lista de dispositivos instalados en el lote.
- Incluye filtrado de dispositivos por modelo, número de serie o estado.
- Utiliza un modal para mostrar los detalles de cada dispositivo, adaptado según su tipo.

---

#### **Estados manejados**

- `viewType`: define la vista activa ("crop" o "devices").
- `selectedDevice`: dispositivo seleccionado para ver en el modal.
- `searchText`: texto para filtrar dispositivos.
- `isSearchVisible`: determina si el campo de búsqueda está visible.
- `searchAnim`: animación asociada a la búsqueda.

---

## Efectos

- `useEffect`: Al cambiar el lote actual (`currentLot`), se realiza una petición a `fetchDevicesByLot` para cargar los dispositivos correspondientes.

---

#### **Funciones clave**

- `fetchDevicesByLot(lotId)`: se ejecuta cuando cambia el lote para obtener los dispositivos relacionados.
- `animateSearchIn() / animateSearchOut()`: animaciones para mostrar u ocultar la barra de búsqueda.

---

## Filtrado de dispositivos

Se genera una lista filtrada (`filteredDevices`) en función del texto ingresado, considerando:

- Modelo (`model`)
- Número de serie (`serial_number`)
- Estado (`status_name`)

---

#### **Renderizado condicional**

- Si `viewType` es "crop", se muestra `LotInfoCard` con opción de editar el cultivo.
- Si `viewType` es "devices", se lista `filteredDevices`:
  - Si el dispositivo es una válvula (`devices_id === 1`), se renderiza `ValveCard`.
  - En caso contrario, se renderiza `DeviceCard`.
  - Si no hay dispositivos, muestra "No hay resultados".

---

#### **Modales de detalles**

- `ValveDetailsModal`: se muestra si el dispositivo seleccionado es una válvula.
- `DeviceDetailsModal`: se muestra si el dispositivo es de otro tipo.

---

## Interfaz

- **Encabezado personalizado (`CustomHeader`)**: Título "Detalles del Lote" con navegación hacia atrás.
- **`LotCard`**: Muestra información general del lote actual.
- **Pestañas**:
  - **"Cultivo"**: Vista de cultivos.
  - **"Dispositivos"**: Vista de dispositivos + botón de búsqueda.
- **`SearchBar`**: Se muestra solo si la vista activa es "devices" y el campo de búsqueda está visible.

---

#### **Dependencias externas utilizadas**

- `useLotContext`: para acceder al lote actual y dispositivos.
- `Ionicons`: para el icono del botón de búsqueda.
- `react-native` y `react-native-reanimated` para vistas, animaciones y estilos.
- `expo-router` para la navegación.

---
