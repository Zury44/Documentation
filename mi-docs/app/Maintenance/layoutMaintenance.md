# ReportsLayout.tsx

Componente de layout para la sección de reportes.
Se encarga de verificar el acceso del usuario y envolver las vistas en un contexto global.

---

## Descripción General

ReportsLayout realiza las siguientes tareas:

* Verifica si el usuario está autenticado mediante la función `getToken`.
* Redirige al login (`/login`) si no se encuentra un token válido.
* Oculta manualmente el splash screen (`SplashScreen.hideAsync`) al completar la verificación.
* Proporciona acceso al contexto de reportes (`ReportsProvider`) a todas las pantallas hijas.
* Renderiza las pantallas del stack sin encabezado (`headerShown: false`).

---

## Funcionalidad

### useEffect → checkAccess()

* Ejecuta una verificación de autenticación al montar el componente.
* Si no hay token, redirige a la pantalla de login.
* Si hay token válido, oculta el splash screen y permite mostrar las pantallas hijas.

---

## Estado

```ts
const [isAuthenticated, setIsAuthenticated] = useState<boolean | null>(null);
```

* null → estado inicial mientras se realiza la verificación.
* false → el usuario no está autenticado.
* true → el usuario está autenticado correctamente.

---

## Contexto

Este layout envuelve todo el stack dentro del componente:

```tsx
<ReportsProvider>
  <Stack screenOptions={{ headerShown: false }} />
</ReportsProvider>
```

Esto permite que cualquier pantalla dentro del stack acceda al contexto de reportes globalmente.
