# Notification.tsx

Pantalla de notificaciones del sistema, muestra una lista de notificaciones con título, mensaje, fecha y estado (leída / no leída). Permite alternar su estado al tocarlas.

---

## Descripción General

Notification.tsx se encarga de:

- Mostrar una lista de notificaciones locales (mock).
- Alternar entre estado "leída" y "no leída" al presionar una notificación.
- Mostrar visualmente las notificaciones con estilos distintos según estado.

---

## Funcionalidad

### obtenerNotificaciones()

- Simula la carga de datos de notificaciones (mock estático).
- Cada notificación tiene `id`, `titulo`, `mensaje`, `fecha`, y `estado`.

```ts
const respuesta: Notificacion[] = [
  {
    id: 1,
    titulo: "DisRiego",
    mensaje: "El dispositivo ... ha sido asignado ...",
    fecha: "Jul 16, 2025",
    estado: "no_leida"
  },
  {
    id: 2,
    titulo: "DisRiego",
    mensaje: "Mantenimiento programado ...",
    fecha: "Jul 29, 2025",
    estado: "leida"
  }
]
```

### alternarEstadoNotificacion(id)

- Cambia el estado de una notificación de `leida` a `no_leida` y viceversa.
- Se ejecuta al presionar una notificación.

---

## Estado

```ts
const [notificaciones, setNotificaciones] = useState<Notificacion[]>([]);
```

---

## Componentes usados

- `FlatList` – Para renderizar la lista de notificaciones.
- `TouchableOpacity` – Para hacer clic sobre las tarjetas.
- `Image` – Ícono de cada notificación.
- `AntDesign` (importado pero no utilizado actualmente).
- `SafeAreaView` – Contenedor seguro con margen superior.

---

## Navegación

- Este componente no redirige a otras vistas por ahora.
- Utiliza `useRouter` de expo-router, pero no lo llama aún.
