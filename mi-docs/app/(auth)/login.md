# LoginScreen.tsx

Pantalla de inicio de sesión para el usuario.  
Permite ingresar credenciales, validar cuenta, enviar correos de activación y redirigir según el estado del usuario.

---

## Descripción General

LoginScreen se encarga de:

- Validar campos de email y contraseña.
- Autenticar al usuario contra el backend.
- Verificar si es el primer inicio de sesión.
- Enviar un correo de activación si la cuenta aún no ha sido activada.
- Redirigir a /completeInfo si el usuario nunca completó su perfil.
- Redirigir a /home si ya está completo.

---

## Funcionalidad

### useEffect → checkFirstLogin()

- Verifica si hay un token guardado en AsyncStorage.
- Consulta la variable isFirstLogin para decidir redirección.

---

### handleLogin()

- Valida que los campos no estén vacíos.
- Llama a login(email, password).
- Si el login es exitoso:
  - Lee userData y first_login_complete desde AsyncStorage.
  - Redirige a completeInfo o home según el caso.
- Si falla:
  - Si la cuenta no está activada, intenta enviar un correo de activación.
  - Si está bloqueada, muestra un mensaje específico.
  - Si es otro error, muestra alerta genérica.

---

### sendActivationEmail()

- Usa EmailJS para enviar un enlace de activación con el token guardado.
- Incluye URL: `${API_FRONT}/signup/${activationToken}`

---

## Estado

```ts
const [email, setEmail] = useState("");
const [password, setPassword] = useState("");
const [loading, setLoading] = useState(false);
const [emailError, setEmailError] = useState(false);
const [passwordError, setPasswordError] = useState(false);
const [showPassword, setShowPassword] = useState(false);
```

---

## Componentes usados

- Header – Encabezado.
- CustomInput – Campos de email y contraseña.
- Button – Botón de login.
- AsyncStorage – Para manejar estado persistente.
- Eye / EyeOff – Icono para alternar visibilidad de contraseña.
- Alert – Para mostrar errores o confirmaciones.

---

## Validaciones

- Email y contraseña no pueden estar vacíos.
- Se muestra color rojo si hay error en el input.
- Se muestra Alert si las credenciales son inválidas o la cuenta está bloqueada.
- Si la cuenta no está activada, se envía un nuevo correo con el enlace.

---

## Navegación

- useRouter() de expo-router:
  - router.replace("/completeInfo")
  - router.replace("(tabs)/home")
  - router.push("/forgotPassword")
  - router.replace("/validation")

