
# Historia de usuario

Como dueño de un negocio, quiero crear mi cuenta, entrar al sistema y registrar mi comercio desde el celular para empezar a utilizar POSNEX sin tener que hacerlo en una computadora.

# Lo que sí se implementará

- Ajustar las pantallas de registro, inicio de sesión y alta de negocio para celular.
- Validar datos obligatorios, correo y mensajes de error antes y después de llamar a la API.
- Conectar los formularios con los endpoints reales de autenticación y negocios.
- Proteger las pantallas que requieren sesión y mostrar una respuesta correcta ante `401` o `403`.
- Consultar el negocio desde el servidor después de recargar la aplicación.
- Probar que una segunda cuenta no pueda consultar el negocio de la primera.
- Guardar evidencia de pruebas, cambios y errores corregidos.

# Lo que queda fuera

No desarrollaremos en este incremento:

- Ventas.
- Caja.
- Tickets.
- Control completo de inventario.
- Pagos.
- Entregas.
- Integración con Uber Direct.
- Personalización avanzada por giro.
- Sincronización sin Internet.
- Publicación en Google Play.

Tampoco se exige un APK.

Estas funciones pueden retomarse cuando el flujo básico sea estable.

# Criterios de aceptación verificables

| ID | Criterio | Cómo se comprueba |
|---|---|---|
| **CA01** | No aparece desplazamiento horizontal en registro, acceso y alta de negocio. | Abrir cada pantalla a 360, 390 y 430 px. |
| **CA02** | Los campos vacíos y correos incorrectos muestran una indicación clara. | Enviar formularios con datos inválidos. |
| **CA03** | El registro y el inicio de sesión se comunican con la API real. | Revisar solicitudes y respuestas de red. |
| **CA04** | Una ruta privada no se abre sin sesión válida. | Entrar directamente a la URL y simular sesión vencida. |
| **CA05** | El alta envía los campos esperados por el backend y confirma el resultado. | Registrar negocio válido y uno con datos incorrectos. |
| **CA06** | El negocio creado se mantiene después de cerrar y volver a abrir la vista. | Recargar y consultar nuevamente con la misma cuenta. |
| **CA07** | Una segunda cuenta no puede consultar o modificar el negocio ajeno. | Repetir la consulta con otro usuario y observar el rechazo. |
| **CA08** | Si la API está caída, la pantalla informa el error y no muestra un guardado falso. | Detener temporalmente la API y enviar el formulario. |
| **CA09** | Las pantallas se pueden usar con el dedo y el texto es legible. | Probar controles y formularios en un teléfono real o emulador. |
| **CA10** | El resultado queda documentado con capturas y cambios versionados. | Revisar las pruebas y el historial Git del incremento. |

### Prueba principal

Un usuario nuevo registra su cuenta y su negocio, recarga la página y ve el mismo comercio.

Después se intenta abrir ese registro con otra cuenta; el servidor debe impedirlo.

# Dependencias y asuntos por resolver

Antes de integrar el frontend necesitamos identificar:

- El contrato real de las solicitudes.
- La forma en que se envía el token.
- El puerto de la API.
- La configuración de PostgreSQL.

Si alguna operación de negocio todavía no está disponible en el backend, se anotará como tarea pendiente y no se presentará como terminada.
