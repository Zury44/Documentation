# CompleteInfo.tsx

Pantalla para completar la información del perfil del usuario.  
Se muestra después del primer inicio de sesión para recolectar datos adicionales como dirección, ubicación, teléfono e imagen de perfil.

---

## Descripción General

CompleteInfo se encarga de:

- Mostrar un formulario que solicita datos adicionales del usuario después del login.
- Obtener países, departamentos y ciudades dinámicamente desde el backend.
- Validar que todos los campos requeridos estén completos.
- Permitir subir una imagen de perfil (opcional).
- Enviar los datos al backend mediante un formulario FormData.
- Redirigir al usuario a /home cuando el registro es exitoso.

---

## Funcionalidad

### useEffect → fetchCountries()

- Carga la lista de países disponibles en el selector al montar la pantalla.
- Usa getCountries() desde @/services/location.

---

### fetchStates(countryCode)

- Llama a getStates() y getCountryPhoneCode() para el país seleccionado.
- Actualiza los estados disponibles en el segundo selector y el código de teléfono.

---

### fetchCities(countryCode, stateCode)

- Llama a getCities() para obtener la lista de ciudades según el país y departamento seleccionados.

---

### pickImage()

- Abre la galería del dispositivo con ImagePicker para seleccionar una imagen cuadrada.
- Si el usuario selecciona una imagen, se guarda su URI y nombre en el estado.

---

### handleRegister()

- Valida que todos los campos requeridos estén llenos.
- Obtiene el user_id desde getUserData().
- Construye un FormData con los datos ingresados y la imagen (si se seleccionó).
- Envía los datos con axios a la ruta /users/first-login-register del backend.
- Si tiene éxito, muestra un Alert y redirige al usuario a /home.

---

## Estado

```ts
const [direccion, setDireccion] = useState("");
const [telefono, setTelefono] = useState("");
const [imageUri, setImageUri] = useState<string | null>(null);
const [imageName, setImageName] = useState<string | null>(null);

const [selectedCountry, setSelectedCountry] = useState("");
const [selectedState, setSelectedState] = useState("");
const [selectedCity, setSelectedCity] = useState("");

const [countries, setCountries] = useState([]);
const [states, setStates] = useState([]);
const [cities, setCities] = useState([]);
const [phoneCode, setPhoneCode] = useState("");

const [loading, setLoading] = useState(false);
```

---

## Componentes usados

- Header – Encabezado superior de la app.
- CustomInput – Campo de texto reutilizable.
- DropdownPicker – Select personalizado.
- Button – Botón con texto o ActivityIndicator.
- ImagePicker – De expo-image-picker, para cargar imagen desde galería.

---

## Validaciones

- Todos los campos son requeridos excepto la imagen.
- El teléfono se limpia con expresión regular para permitir solo números.
- Si hay errores o campos vacíos, se muestra un Alert.