# HomeScreen.tsx

Pantalla de bienvenida del usuario tras iniciar sesión.  
Muestra un saludo personalizado, avatar e ítems de navegación rápida a funciones clave.

---

## Descripción General

HomeScreen se encarga de:

- Mostrar el nombre e imagen del usuario (o sus iniciales si no hay imagen).
- Renderizar una grilla con tarjetas de acceso rápido: Predios, Facturas, Consumo, Reportes.
- Permitir al usuario navegar fácilmente por la aplicación.

---

## Funcionalidad

### useEffect → fetchUserData()

- Obtiene datos del usuario usando getUserData().
- Muestra nombre y carga imagen si existe.
- Si no hay datos, muestra "Usuario" por defecto.

### renderUserAvatar()

- Muestra una imagen circular con las iniciales si no hay foto.
- Si existe imagen, la superpone sobre el círculo base SVG.

---

## Estado

```ts
const [username, setUsername] = useState<string | null>(null);
const [profileImage, setProfileImage] = useState<string | null>(null);
const [imageLoaded, setImageLoaded] = useState(false);
const [loading, setLoading] = useState(true);
```

---

## Navegación

Cada tarjeta ejecuta:

```ts
router.push(item.route);
```

- Mis predios y lotes → /properties/myProperties
- Mis facturas y pagos → /home/payments
- Mi consumo → /home/consumption
- Reportar fallos → /home/report

---

## Componentes usados

- SafeAreaView – Margen superior seguro
- ActivityIndicator – Carga mientras llega la data
- Svg, Circle, SvgText – Para mostrar iniciales si no hay foto
- Image – Imagen de perfil y de tarjetas
- TouchableOpacity – Para navegación
- Feather – Icono flecha derecha en tarjetas
