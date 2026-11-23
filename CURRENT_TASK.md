# CURRENT_TASK.md — Tarea actual

### 1.1. Historia de usuario

Como dueño de un negocio, quiero crear mi cuenta, entrar al sistema y registrar mi comercio desde el celular para empezar a utilizar POSNEX sin tener que hacerlo en una computadora.

### 1.2. Lo que sí se implementará

1. Ajustar e implementar en Flutter las pantallas de registro, inicio de sesión y alta de negocio para celular.
2. Validar datos obligatorios, correo y mensajes de error antes y después de llamar a la API.
3. Conectar los formularios con los endpoints reales de autenticación y negocios.
4. Proteger las pantallas que requieren sesión y mostrar una respuesta correcta ante `401` o `403`.
5. Consultar el negocio desde el servidor al volver a entrar a la pantalla o al reabrir la aplicación.
6. Probar que una segunda cuenta no pueda consultar el negocio de la primera.
7. Guardar evidencia de pruebas, cambios y errores corregidos.

### 1.3. Lo que queda fuera

No desarrollaremos en este incremento ventas, caja, tickets, control completo de inventario, pagos, entregas, integración con Uber Direct, personalización avanzada por giro, sincronización sin Internet ni publicación en Google Play. Estas funciones pueden retomarse cuando el flujo básico sea estable.

### 1.4. Criterios de aceptación verificables

| ID | Criterio | Cómo se comprueba |
|---|---|---|
| CA01 | No aparece desplazamiento horizontal en registro, acceso y alta de negocio. | Probar cada pantalla en tamaños de pantalla equivalentes a 360, 390 y 430 px, usando emulador o dispositivo. |
| CA02 | Los campos vacíos y correos incorrectos muestran una indicación clara. | Enviar formularios con datos inválidos. |
| CA03 | El registro y el inicio de sesión se comunican con la API real. | Revisar solicitudes y respuestas HTTP. |
| CA04 | Una pantalla protegida no se abre sin sesión válida. | Intentar acceder sin sesión y simular una sesión vencida. |
| CA05 | El alta envía los campos esperados por el backend y confirma el resultado. | Registrar un negocio válido y otro con datos incorrectos. |
| CA06 | El negocio creado se mantiene después de salir de la pantalla y volver a entrar, o de cerrar y reabrir la aplicación. | Volver a abrir la pantalla o la aplicación y consultar nuevamente con la misma cuenta. |
| CA07 | Una segunda cuenta no puede consultar o modificar el negocio ajeno. | Repetir la consulta con otro usuario y observar el rechazo. |
| CA08 | Si la API está caída, la aplicación informa el error y no muestra un guardado falso. | Detener temporalmente la API y enviar el formulario. |
| CA09 | Las pantallas se pueden usar con el dedo y el texto es legible. | Probar controles y formularios en un teléfono real o emulador. |
| CA10 | El resultado queda documentado con capturas y cambios versionados. | Revisar las pruebas y el historial Git del incremento. |

**Prueba principal:** un usuario nuevo registra su cuenta y su negocio desde la aplicación Flutter. Al volver a entrar a la pantalla o reabrir la aplicación, consulta el mismo comercio. Después se intenta abrir ese registro con otra cuenta; el servidor debe impedirlo.

### 1.5. Dependencias y asuntos por resolver

Antes de integrar la aplicación Flutter necesitamos identificar el contrato real de las solicitudes, la forma en que se envía el token, la dirección y el puerto de la API y la configuración de PostgreSQL. Si alguna operación de negocio todavía no está disponible en el backend, se anotará como tarea pendiente y no se presentará como terminada.
