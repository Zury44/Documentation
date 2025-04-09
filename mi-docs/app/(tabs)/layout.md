# TabsLayout.tsx

Componente de layout principal para navegación inferior por pestañas.  
Gestiona el acceso a rutas protegidas y muestra las pestañas: Notificaciones, Inicio y Perfil.

---

## Descripción General

TabsLayout se encarga de:

- Verificar si el usuario está autenticado antes de mostrar las pestañas.
- Redirigir al login si no hay token válido.
- Renderizar una barra inferior de navegación con iconos personalizados.

---

## Funcionalidad

### useEffect → checkAuth()

- Llama a getToken() para verificar si hay token de sesión.
- Si no hay token, redirige a "/login".
- Previene renderizado hasta completar validación de sesión.

---

## Estado

```ts
const [isAuthenticated, setIsAuthenticated] = useState<boolean | null>(null);
```

---

## Navegación

- router.replace("/login") → si el usuario no está autenticado

---

## Tabs configuradas

- Notificaciones → icono notifications-outline
- Inicio → icono home-outline
- Perfil → icono person-outline

---

