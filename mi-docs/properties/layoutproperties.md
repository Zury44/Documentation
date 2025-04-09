# PropertiesLayout.tsx

Layout de **autenticación y contexto para la sección de propiedades**.

---

## Descripción General

Este componente verifica si el usuario está autenticado antes de permitir el acceso a la sección de propiedades. Si no lo está, redirige al login automáticamente. Además, configura un proveedor de contexto global (`LotProvider`) para manejar datos de los lotes.

---

## Funcionalidad principal

- Previene la ocultación automática del SplashScreen con `SplashScreen.preventAutoHideAsync()`.
- Verifica el token de autenticación con `getToken()`.
- Si no hay token válido, redirige al login usando `router.replace("/login")`.
- Usa `LotProvider` como wrapper para compartir estado global entre las pantallas relacionadas.
- Renderiza el stack de navegación sin encabezado (`headerShown: false`).
- Envuelve todo en `KeyboardAvoidingView` para mejorar la experiencia al usar el teclado en dispositivos móviles.

---

## Ciclo de vida

### `useEffect → checkAuth()`

1. Llama a `getToken()` para obtener el token de autenticación.
2. Si hay token válido, actualiza `isAuthenticated` a `true`.
3. Si no hay token, actualiza `isAuthenticated` a `false` y redirige al login.
4. Oculta manualmente el SplashScreen con `SplashScreen.hideAsync()`.

---

## Renderizado condicional

- Mientras `isAuthenticated` es `null`, no se muestra ningún contenido.
- Una vez verificada la autenticación:
  - Si es válida, renderiza las pantallas de propiedades envueltas en el contexto `LotProvider`.
  - Todo el contenido está contenido en un `KeyboardAvoidingView` para evitar problemas de superposición con el teclado.
