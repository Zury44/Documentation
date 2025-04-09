# SeeProfile.tsx

Pantalla de **visualización del perfil de usuario**.  
Permite al usuario consultar sus datos personales, de contacto y de ubicación, incluyendo una imagen de perfil o avatar generado con iniciales.

---

## Descripción General

`SeeProfile` muestra la información del usuario en formato solo lectura.  
Incluye avatar, nombre completo, documento, fecha de nacimiento, género, correo electrónico, dirección y localización.

---

## Funcionalidad principal

- Carga los datos del usuario con `getUserData()`.
- Obtiene los nombres legibles de país, departamento y ciudad con `fetchLocationNames()`.
- Muestra un avatar con imagen o iniciales.
- Organiza la información en tres secciones:
  - Datos personales
  - Datos de contacto
  - Ubicación

---

## Ciclo de vida

### `useEffect → fetchUserData()`

1. Llama a `getUserData()` desde el backend.
2. Usa `getInitials(nombre completo)` para generar avatar con iniciales.
3. Llama a `fetchLocationNames()` para convertir los IDs de país, departamento y ciudad en nombres.
4. Actualiza el estado `userData` y `userInitials`.
5. Controla el indicador de carga con `loading`.

---

## Avatar

```tsx
<View>
  <Svg> {/* Avatar con iniciales */} </Svg>
  {userData.profile_picture && <Image />} {/* Imagen real si existe */}
</View>
```
