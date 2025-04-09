# Documentación del Componente `DetailsProperties`

## Descripción General

`DetailsProperties` es una pantalla que muestra la información detallada de un predio y sus lotes asociados. Permite la visualización de la información general del predio, el uso de una barra de búsqueda para filtrar lotes y la visualización de detalles de un lote mediante un modal.

---

## Estados

- `selectedLot`: Lote actualmente seleccionado para mostrar en el modal.
- `searchText`: Texto usado para filtrar los lotes por nombre, ID o número de registro inmobiliario.

---

## Contexto

Se obtiene del `LotContext`:

- `currentProperty`: Predio actualmente seleccionado.
- `lots`: Lotes asociados al predio.
- `refreshLotsByProperty`: Función que actualiza los lotes al cambiar el predio actual.

---

## Hooks Utilizados

- `useRouter`: Para navegar entre pantallas.
- `useFocusEffect`: Para refrescar los lotes cada vez que la pantalla es enfocada.

---

## Comportamiento

- Al montar el componente y cuando cambia el `currentProperty`, se actualizan los lotes mediante `refreshLotsByProperty`.
- Si no hay `currentProperty`, el componente retorna `null`.
- Filtra los lotes según el texto ingresado en la barra de búsqueda.

---

## Renderizado

- `CustomHeader`: Cabecera con título y botón para volver a "myProperties".
- `PropertyCard`: Muestra los datos generales del predio.
- `SearchBar`: Barra de búsqueda de lotes.
- `LotCard`: Tarjetas de los lotes filtrados, cada una con opción de abrir su modal.
- `LotDetailsModal`: Modal que se muestra si hay un lote seleccionado, con información detallada.

---

## Estilos

Incluye estilos específicos para:

- Área segura (`safeArea`)
- Contenedor principal y de scroll
- Contenedores interiores y secciones
- Títulos de secciones

---

## Dependencias

- `@react-navigation/native`: Para el hook `useFocusEffect`.
- `expo-router`: Para la navegación con `useRouter`.
- Componentes personalizados: `CustomHeader`, `PropertyCard`, `LotCard`, `LotDetailsModal`, `SearchBar`.
- Temas: `colors` y `typography` desde configuraciones compartidas.

---

## Navegación

- Regresa a la pantalla de propiedades al presionar el botón de retroceso (`/properties/myProperties`).

---

## Consideraciones

- Este componente depende del contexto `LotContext`, por lo tanto, debe estar envuelto en un `LotProvider` en un nivel superior.
- No renderiza nada si no hay un predio actual seleccionado.
