# UpdatePassword.tsx

Pantalla de **actualización de contraseña del usuario**.  
Permite ingresar la contraseña actual y establecer una nueva, siempre que cumpla con los requisitos de seguridad definidos.

---

## Descripción General

`UpdatePassword` proporciona un formulario seguro para el cambio de contraseña.  
Valida en tiempo real los criterios de seguridad y verifica que la confirmación coincida con la nueva contraseña.

Incluye:

- Campos para contraseña actual, nueva y su confirmación.
- Indicadores visuales de requisitos de seguridad.
- Alternancia de visibilidad para cada campo de contraseña.
- Comunicación segura con el backend.

---

## Funcionalidad principal

- Valida que todos los campos estén completos.
- Verifica el cumplimiento de reglas de seguridad con `usePasswordValidation()`.
- Confirma coincidencia entre nueva contraseña y su confirmación.
- Obtiene los datos del usuario con `getUserData()` y el token de autenticación desde `AsyncStorage`.
- Envía la solicitud de cambio al backend mediante `axios.post`.
- Muestra mensajes informativos o de error con `Alert`.

---

## Ciclo de vida

### `handleSaveChanges()`

1. Verifica campos vacíos y requisitos de seguridad.
2. Llama a `getUserData()` para obtener el ID del usuario autenticado.
3. Recupera el token desde `AsyncStorage`.
4. Envía la nueva contraseña al backend (`/users/:id/change-password`).
5. Muestra confirmación de éxito o error.
6. Redirige a la pantalla de perfil con `router.replace("/(tabs)/profile")`.

---

## Validación de contraseñas

Validación en tiempo real mediante el hook `usePasswordValidation`.

Requisitos:

- Al menos 12 caracteres.
- Al menos 1 número.
- Letras mayúsculas y minúsculas.
- Al menos 1 carácter especial.

Errores mostrados en pantalla si no se cumplen.

---

## Iconos de visibilidad

```tsx
<TouchableOpacity onPress={() => setShowNewPassword(!showNewPassword)}>
  {showNewPassword ? <EyeOff /> : <Eye />}
</TouchableOpacity>
```

Disponible para los tres campos: actual, nueva y confirmación.

---

## Estructura relacionada

- `services/auth.ts`: contiene `getUserData()`
- `services/config.ts`: contiene la constante `API_URL`
- `hooks/passwordValidation.ts`: lógica para validación de contraseñas
- `components/CustomInput.tsx`, `components/Button.tsx`, `components/CustomHeader.tsx`: componentes visuales reutilizables

## Formulario

```tsx
<View>
  <CustomInput placeholder="Contraseña actual" secureTextEntry />
  <CustomInput placeholder="Contraseña nueva" secureTextEntry />
  <CustomInput placeholder="Confirmar contraseña" secureTextEntry />
</View>
```

---

## Requisitos visuales

```tsx
<Text>• Al menos 12 caracteres</Text>
<Text>• Al menos 1 número</Text>
<Text>• Mayúsculas y minúsculas</Text>
<Text>• Mínimo un carácter especial</Text>
```

Se muestran al pie del formulario como recordatorio.
