# ForgotPasswordScreen.tsx

Pantalla de recuperación de contraseña.  
Permite al usuario solicitar un enlace para restablecer su contraseña a través de su correo electrónico.

---

## Descripción General

ForgotPasswordScreen se encarga de:

- Validar el correo electrónico ingresado por el usuario.
- Enviar una solicitud al backend para generar un token de recuperación.
- Usar EmailJS para enviar un enlace de restablecimiento al correo del usuario.
- Notificar al usuario sobre el éxito o fallo del proceso.

---

## Funcionalidad

### handleSendEmail()

- Valida que el campo de correo no esté vacío y tenga formato válido.
- Realiza una petición POST a /auth/request-reset-password.
- Recibe el token de recuperación desde el backend.
- Construye un payload con EmailJS para enviar un correo con el enlace de recuperación.
- Maneja errores de validación y errores del servidor.

---

## Estado

```ts
const [email, setEmail] = useState("");
```

---

## Componentes usados

- Header – Encabezado superior.
- CustomInput – Campo de entrada de texto.
- Button – Botón de acción.
- ScrollView – Contenedor con scroll vertical.
- Alert – Muestra mensajes de éxito o error.

---

## Validaciones

- El campo de correo no puede estar vacío.
- El correo debe tener un formato válido (regex).
- Si el correo no está registrado, muestra un mensaje de error personalizado.

---

## Extras

- El enlace de recuperación incluye el token recibido, concatenado a la URL del frontend:

```ts
${API_FRONT}/login/resetpassword/${resetToken}
```

- Si el correo se envía correctamente, se muestra un mensaje de éxito con Alert.
- En caso de error 500, se indica que el correo no está registrado.

---

## Navegación

- Usa useRouter de expo-router para redirigir al login con:

```ts
router.push("/login")
```

