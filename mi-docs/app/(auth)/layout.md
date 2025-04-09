# AuthLayout.tsx

Componente de layout para las pantallas de autenticación de la aplicación.  
Se encarga de preparar el entorno antes de mostrar las vistas de login, registro, validación, etc.

---

## Descripción General

AuthLayout se encarga de:

- Prevenir que la pantalla de splash se oculte automáticamente.
- Cargar las fuentes personalizadas de la aplicación.
- Ocultar la splash screen solo cuando las fuentes estén listas.
- Renderizar el stack de navegación sin encabezado para las pantallas de autenticación.

---

## Funcionalidad

### useEffect → SplashScreen.hideAsync()

- Espera a que las fuentes estén completamente cargadas (`useFonts()`).
- Si las fuentes están listas, oculta el SplashScreen manualmente.

---

## Estado

```ts
const [loaded] = useFonts({
  RobotoBold: require("../../assets/fonts/Roboto-Bold.ttf"),
  RobotoSemiBold: require("../../assets/fonts/Roboto-SemiBold.ttf"),
  RobotoMedium: require("../../assets/fonts/Roboto-Medium.ttf"),
  RobotoRegular: require("../../assets/fonts/Roboto-Regular.ttf"),
  RobotoLight: require("../../assets/fonts/Roboto-Light.ttf"),
});
