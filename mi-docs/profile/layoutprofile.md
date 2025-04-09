# ProfileLayout.tsx

Componente de layout para las vistas del perfil de usuario.  
Es responsable de verificar la autenticación antes de permitir el acceso a las pantallas hijas.

---

## Descripción General

`ProfileLayout` se encarga de:

- Verificar si el usuario tiene un token de sesión válido.
- Redirigir al login en caso de no estar autenticado.
- Mostrar las pantallas del perfil en un `Stack` de navegación.
- Usar `KeyboardAvoidingView` para evitar que el teclado cubra los inputs en iOS.

---

## Funcionalidad

### `useEffect → checkAuth()`

- Obtiene el token con `getToken()`.
- Si **hay token**: establece `isAuthenticated` en `true`.
- Si **no hay token**: establece `isAuthenticated` en `false` y redirige a `/login`.
- Oculta manualmente el splash screen con `SplashScreen.hideAsync()`.

---

## Estado

```ts
const [isAuthenticated, setIsAuthenticated] = useState<boolean | null>(null);
```
