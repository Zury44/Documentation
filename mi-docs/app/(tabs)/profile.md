# Profile.tsx

Pantalla de perfil del usuario. Muestra datos básicos del usuario, permite navegar a vistas relacionadas como ver perfil, editar datos, cambiar contraseña, accesibilidad y cerrar sesión.

---

## Descripción General

Profile.tsx se encarga de:

- Mostrar nombre, correo e imagen (o iniciales) del usuario.
- Permitir navegación a opciones de configuración personal.
- Cerrar sesión y redirigir al login.

---

## Funcionalidad

### useEffect → fetchUserData()

- Llama a getUserData() y guarda el nombre, apellido, correo e imagen.
- Muestra un avatar SVG con iniciales o imagen.

### handleLogout()

- Ejecuta logout() y redirige al login con router.replace("/login").

### renderUserAvatar()

- Muestra un círculo con iniciales como base.
- Si hay imagen, la renderiza encima con onLoad para mostrar.

---

## Estado

```ts
const [user, setUser] = useState<UserData | null>(null);
const [loading, setLoading] = useState(true);
const [imageLoaded, setImageLoaded] = useState(false);
```

---

## Navegación

- router.push("/profile/seeProfile")
- router.push("/profile/updateProfile")
- router.push("/profile/updatePassword")
- router.push("/profile/accesibility")
- router.replace("/login") (al cerrar sesión)

---

## Opciones disponibles

- Ver perfil
- Editar datos personales
- Actualizar contraseña
- Preferencias de accesibilidad
- Cerrar sesión

---

## Componentes usados

- `SafeAreaView` – contenedor general
- `Svg`, `Circle`, `SvgText` – avatar con iniciales
- `Image` – imagen de perfil
- `Ionicons` – iconos de acciones
- `TouchableOpacity` – navegación y acciones
- `ActivityIndicator` – cargando info del usuario
- `getUserData`, `logout` – servicios de auth
