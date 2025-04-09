# UpdateProfile.tsx

Pantalla de **actualización del perfil de usuario**.  
Permite visualizar y modificar datos personales, dirección, teléfono e imagen de perfil. Además, permite seleccionar país, estado y ciudad mediante dropdowns dependientes.

---

## Descripción General

`UpdateProfile` es un componente que muestra un formulario editable con los datos del usuario.  
El usuario puede cargar una imagen, editar su dirección y teléfono, y seleccionar su localización desde listas dinámicas.

---

## Funcionalidad principal

- Carga inicial de datos del usuario y países (`useEffect`).
- Lógica para selección dinámica de país, estado y ciudad.
- Carga y previsualización de imagen de perfil.
- Subida de imagen al servidor.
- Guardado de datos editados.

---

## Ciclo de vida

### `useEffect → fetchData()`

1. Llama a `getUserData()` y `getCountries()`.
2. Si hay datos del usuario:
   - Carga dirección, teléfono y selección actual de país/departamento/ciudad.
   - Carga estados y ciudades correspondientes.
   - Muestra imagen actual si existe.

---

## Lógica de Avatar

- `getInitials(nombre)` genera iniciales en mayúsculas.
- `getColorFromName(nombre)` asigna color determinista al avatar.

---

## Estados principales

- `user`: datos del usuario.
- `direccion`, `telefono`: valores editables.
- `imageUri`: imagen cargada.
- `countries`, `states`, `cities`: listas para los dropdowns.
- `selectedCountry`, `selectedState`, `selectedCity`: selección actual.

---

## Memorizar opciones para dropdowns

- Se usan `useMemo` para evitar recálculo:
  - `countryOptions`
  - `stateOptions`
  - `cityOptions`

---

## Manejo de cambios en la ubicación

- `handleCountryChange`: actualiza país y carga estados.
- `handleStateChange`: actualiza estado y carga ciudades.

---

## Guardar cambios

- `handleSaveChanges()` envía los nuevos datos al servidor (dirección, teléfono, ubicación).
- Usa `axios.put` con token de autenticación.

---

## Imagen de perfil

### Selección

- `handleImagePicker()` permite elegir una imagen desde la galería.
- Solicita permisos y lanza `ImagePicker.launchImageLibraryAsync`.
- Guarda `imageUri` localmente y llama a `uploadImage()`.

### Subida al servidor

- `uploadImage(uri)`:
  - Usa `FormData` para enviar la imagen como archivo.
  - Llama a `axios.put` con el endpoint correspondiente.
  - Muestra alerta en caso de éxito o error.

---

## Navegación

- Usa `useRouter` de `expo-router` para redireccionar si es necesario.

---

## Indicadores de estado

- `loading`: muestra `ActivityIndicator` mientras se cargan los datos.
- `savingChanges`, `uploadingImage`: controlan estados de carga durante guardado o subida de imagen.

---

## Componentes personalizados utilizados

- `CustomInput`, `DropdownPicker`, `CustomHeader`, `Button`

---

## Servicios utilizados

- `getUserData`, `getCountries`, `getStates`, `getCities` (API interna)
- `AsyncStorage` para obtener token de autenticación
- `axios` para comunicación con el backend

---

## Consideraciones finales

- La carga de ubicaciones es dependiente: estados dependen del país, ciudades del estado.
- Manejo de errores con `try/catch` para llamadas a la API.
- Imágenes deben ser cuadradas y de buena calidad para mejor presentación.
- El token debe estar disponible en `AsyncStorage` para poder hacer las peticiones protegidas.
