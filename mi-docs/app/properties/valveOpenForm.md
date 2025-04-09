# App.tsx – Pantalla de Solicitud de Apertura

Pantalla que permite al usuario generar una solicitud de apertura de canal de riego, ya sea con límite de agua o sin él. Se pueden ingresar los detalles necesarios como volumen (si aplica), fecha y hora de apertura y cierre.

---

## Descripción General

La pantalla muestra un formulario con opciones de apertura programada. Dependiendo de la selección, se habilitan campos adicionales. Al confirmar, se validan los datos y se muestra una alerta indicando el resultado del proceso.

---

## Hooks y Estados

- `useRouter`: para navegar a otras pantallas dentro de la app.
- `useSafeAreaInsets`: para aplicar correctamente los márgenes del sistema.
- `useState`: para manejar el estado del formulario, fechas y visibilidad de pickers.

### Estados Locales

- `selectedOption`: almacena la opción de apertura seleccionada.
- `volumen`: volumen de agua ingresado (solo si se selecciona con límite).
- `fechaApertura`: fecha y hora programadas de apertura.
- `fechaCierre`: fecha y hora programadas de cierre.
- `showPicker`: controla qué picker de fecha/hora está visible y en qué modo.

---

## Funciones Principales

### `handleConfirm()`

Valida los campos del formulario dependiendo de la opción elegida. Si todo es correcto, muestra una alerta de éxito y registra los datos en consola.

---

## Componentes Utilizados

- `SafeAreaView`: para respetar los márgenes seguros del sistema.
- `ScrollView`: permite el desplazamiento del contenido.
- `CustomHeader`: muestra el encabezado con título y botón de regreso.
- `DropdownPicker`: componente personalizado para desplegable de opciones.
- `TextInput`: entrada de texto para el volumen.
- `DateTimePicker`: selector nativo para fechas y horas.
- `TouchableOpacity`: usado para mostrar los pickers al presionar.
- `Button`: botón personalizado para enviar la solicitud.

---

## Lógica de Renderizado

- Si la opción seleccionada es "con límite de agua", se muestra el campo de volumen.
- Si la opción seleccionada es "con o sin límite", se muestran los pickers para fecha/hora de apertura y cierre.
- La interacción con los `DateTimePicker` se divide entre selección de fecha y luego hora.
- El botón inferior siempre está disponible y lanza la validación del formulario.

---

## Navegación

- El botón de regresar en el encabezado redirige a: `properties/detailsLot`.

---

## Validaciones Incluidas

- Selección de una opción válida.
- Ingreso obligatorio de volumen y fechas según corresponda.
- La fecha de cierre debe ser posterior a la de apertura.
