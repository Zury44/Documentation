

# ValidationScreen.tsx

Pantalla para validar la identidad del usuario antes del registro.  
Solicita tipo de documento, número y fecha de expedición para iniciar el pre-registro.

---

## Descripción General

ValidationScreen se encarga de:

- Cargar los tipos de documento desde el backend o caché local.
- Validar los datos ingresados: tipo, número y fecha de expedición.
- Enviar la información al backend para generar un token de pre-registro.
- Redirigir a la pantalla de registro si la validación es exitosa.

---

## Funcionalidad

### fetchDocumentTypes()

- Obtiene los tipos de documentos desde el endpoint /users/type-documents.
- Si están cacheados en AsyncStorage, los usa.
- Si no, los solicita al backend y los guarda en caché.

### handleValidation()

- Valida que todos los campos estén completos.
- Verifica que el número de documento sea numérico.
- Valida que la fecha de expedición no sea futura.
- Envía los datos al backend y guarda el token recibido.
- Redirige a /register si la validación fue exitosa.
- Muestra errores personalizados en caso de fallos usando handleErrorMessages.

### handleErrorMessages()

- Parsea errores devueltos por el backend y devuelve títulos/mensajes legibles.
- Identifica mensajes conocidos como:
  - Fecha incorrecta
  - Ya registrado
  - Correo ya vinculado
  - Usuario no encontrado
  - Errores 400/404/500 genéricos

---

## Estado

```ts
const [documentType, setDocumentType] = useState("");
const [documentNumber, setDocumentNumber] = useState("");
const [dateIssuanceDocument, setDateIssuanceDocument] = useState<Date | null>(null);
const [showDatePicker, setShowDatePicker] = useState(false);
const [loading, setLoading] = useState(false);
const [documentTypes, setDocumentTypes] = useState([]);
const [loadingDropdown, setLoadingDropdown] = useState(true);
```

---

## Componentes usados

- Header – Encabezado principal.
- CustomInput – Entradas para número de documento y fecha.
- DropdownPicker – Selector de tipo de documento.
- Button – Botón para validar.
- DateTimePicker – Selector de fecha nativo.
- Alert – Para mostrar validaciones y errores.

---

## Validaciones

- El número de documento debe ser numérico.
- El tipo de documento no puede ser el valor placeholder.
- La fecha de expedición no puede ser posterior a la actual.
- Si algún dato es inválido, se muestra un mensaje de error.

---

## Navegación

- router.replace("/register") → luego de validación exitosa
- router.replace("/login") → si el usuario ya tiene cuenta

