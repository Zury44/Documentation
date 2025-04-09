# MyProperties.tsx

## Descripción general

Pantalla principal que muestra todas las propiedades registradas por el usuario autenticado. Permite realizar búsquedas sobre las propiedades, visualizar sus detalles en un modal, y seleccionar una para trabajar con sus lotes asociados.

---

## Componentes y servicios utilizados

- `CustomHeader`: Encabezado con botón de navegación.
- `SearchBar`: Componente de entrada para filtrar propiedades.
- `PropertyCard`: Tarjeta que muestra los datos básicos de una propiedad.
- `PropertyDetailsModal`: Modal con la información detallada de una propiedad.
- `useLotContext`: Contexto para gestionar la propiedad actual seleccionada.
- `getUserData`: Función para obtener los datos del usuario desde almacenamiento seguro.
- `axios`: Cliente HTTP para obtener propiedades del backend.
- `API_URL`: Ruta base para la API del proyecto.

---

## Estados locales

| Estado         | Tipo             | Descripción                                     |
| -------------- | ---------------- | ----------------------------------------------- |
| `properties`   | `Property[]`     | Lista de propiedades asociadas al usuario.      |
| `searchText`   | `string`         | Texto de búsqueda para filtrar propiedades.     |
| `modalVisible` | `boolean`        | Determina si el modal de detalles está visible. |
| `userId`       | `number \| null` | ID del usuario autenticado.                     |
| `loading`      | `boolean`        | Indica si los datos están en proceso de carga.  |

---

## Lógica principal

### useEffect

- Se ejecuta una única vez al montar el componente.
- Obtiene los datos del usuario con `getUserData()`.
- Luego hace una solicitud GET a `/properties/user/:id` para obtener sus propiedades.

### filteredProperties

- Filtra las propiedades según el texto ingresado (`name`, `id` o `real_estate_registration_number`).

### openModal(property)

- Establece la propiedad seleccionada en el contexto y abre el modal de detalles.

### closeModal()

- Cierra el modal de detalles.

---

## Renderizado

- Encabezado con el título de la sección y navegación de regreso al inicio.
- Mensaje introductorio al usuario.
- Barra de búsqueda para filtrar propiedades.
- Lista de propiedades (o un spinner de carga / mensaje si no hay resultados).
- Modal con los detalles de la propiedad seleccionada (`PropertyDetailsModal`).

---

## Interface: `Property`

| Propiedad                         | Tipo     | Descripción                                |
| --------------------------------- | -------- | ------------------------------------------ |
| `id`                              | `string` | ID único de la propiedad                   |
| `name`                            | `string` | Nombre del predio                          |
| `real_estate_registration_number` | `string` | Número de folio inmobiliario               |
| `latitude`                        | `string` | Coordenada de latitud                      |
| `longitude`                       | `string` | Coordenada de longitud                     |
| `extension`                       | `string` | Extensión total del predio                 |
| `user_id`                         | `number` | ID del usuario propietario de la propiedad |
