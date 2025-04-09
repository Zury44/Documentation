# RegisterScreen.tsx

Pantalla de registro final para completar el proceso de validación del usuario.  
Permite crear una contraseña, validar los campos y enviar un correo de activación.

---

## Descripción General

RegisterScreen se encarga de:

- Recibir el correo validado previamente.
- Validar que las contraseñas cumplan con los requisitos.
- Completar el registro en el backend usando un token prevalidado.
- Enviar un correo de activación con EmailJS.
- Redirigir al usuario a /home tras un registro exitoso.

---

## Funcionalidad

### handleRegister()

- Verifica que todos los campos estén completos.
- Valida el formato del correo electrónico.
- Usa un hook personalizado (usePasswordValidation) para validar contraseñas.
- Recupera el token de validación desde AsyncStorage.
- Llama a /users/pre-register/complete para registrar al usuario.
- Guarda el token de activación en AsyncStorage y envía un correo de activación.

---

### sendActivationEmail()

- Usa EmailJS para enviar un enlace con el token de activación.
- Enlace: `${API_FRONT}/signup/${activationToken}`

---

## Estado

```ts
const [email, setEmail] = useState("");
const [emailError, setEmailError] = useState(false);
const [newPassword, setNewPassword] = useState("");
const [confirmPassword, setConfirmPassword] = useState("");
const [loading, setLoading] = useState(false);
```

---

## Componentes usados

- Header – Encabezado de navegación.
- CustomInput – Campos de texto reutilizables.
- Button – Botón de confirmación.
- AsyncStorage – Para leer el token de validación y guardar el de activación.
- usePasswordValidation – Hook personalizado de validación de contraseñas.
- Alert – Para mostrar errores o mensajes de éxito.
- AntDesign – Iconos para mostrar requisitos de contraseña.

---

## Validaciones

- Email debe tener formato válido.
- Las contraseñas deben cumplir con:
  - Mínimo 12 caracteres
  - Al menos 1 número
  - Mayúsculas y minúsculas
  - Al menos un carácter especial
- Las contraseñas deben coincidir.

---

## Navegación

- router.replace("/home") → luego de finalizar el registro exitoso
- router.replace("/login") → si el usuario ya tiene cuenta

