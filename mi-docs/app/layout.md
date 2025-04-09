# Layout.tsx

Componente de layout que gestiona la visualización inicial de las pantallas públicas (login, registro, etc.)  
Carga fuentes personalizadas, verifica la autenticación y oculta el SplashScreen cuando todo está listo.

---

## Descripción General

Layout se encarga de:

- Evitar que el SplashScreen desaparezca automáticamente.
- Cargar fuentes personalizadas con useFonts().
- Verificar si el usuario está autenticado usando getToken().
- Redirigir según el segmento actual y si el usuario está logueado.
- Renderizar un Stack para las pantallas públicas sin encabezado.

---

## Funcionalidad

### useEffect → checkAuth()

- Ejecuta getToken() para verificar si el usuario tiene sesión activa.
- Guarda true o false en isAuthenticated.

### useEffect → SplashScreen + navegación

- Espera a que estén listas las fuentes y autenticación.
- Oculta el SplashScreen con SplashScreen.hideAsync().
- Redirige:
  - Si está autenticado → a "/(tabs)/home"
  - Si no → a "/login"

---

## Estado

```ts
const [isAuthenticated, setIsAuthenticated] = useState<boolean | null>(null);
const [loaded] = useFonts({ Roboto... });

```

## Dependencias / Hooks
- useRouter – Para redirigir entre pantallas.
- useSegments – Para saber si estás en "/login" o "/register".
- useFonts – De Expo para cargar tipografías.
- SplashScreen – Para mostrar el splash hasta que todo esté listo.

## Navegación
- Renderiza un Stack con header oculto.
- Solo se muestra la pantalla "index".
- Utiliza router.replace() para cambiar entre rutas si es necesario.


## Detalles
- No renderiza nada mientras no cargan fuentes o no se sabe si hay sesión.
- Usa StatusBar de Expo con estilo automático.