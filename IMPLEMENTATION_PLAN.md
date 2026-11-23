# POSNEX Mobile — Plan de implementación

### 1.1. Pasos de trabajo

| Paso | Actividad concreta | Entregable y comprobación |
|---|---|---|
| 1 | Revisar carpetas del proyecto Flutter, pantallas, servicios HTTP, endpoints y modelos del backend. | Lista de rutas y campos reales que se utilizarán. |
| 2 | Ajustar diseño, etiquetas y validaciones para uso en celular con Flutter. | Formularios probados en tamaños equivalentes a 360, 390 y 430 px. |
| 3 | Conectar registro e inicio de sesión con la API y manejar errores de autenticación. | Cuenta y sesión creadas con solicitudes reales. |
| 4 | Integrar el alta del negocio y su consulta posterior. | Negocio guardado y recuperado sin duplicados. |
| 5 | Verificar acceso y propiedad con dos usuarios diferentes. | Prueba de autorización exitosa y rechazo a usuario ajeno. |
| 6 | Ejecutar CA01 a CA10, corregir fallos y volver a probar. | Registro de resultados con evidencia por criterio. |
| 7 | Registrar cambios y actualizar el README de ejecución móvil. | Commits identificables e instrucciones reproducibles. |

### 1.2. Orden y seguimiento

El paso 1 va primero porque todavía debemos confirmar las rutas y los campos reales. Los pasos 2 y 3 pueden avanzar juntos una vez conocidos los contratos. La prueba de persistencia depende del alta de negocio; la prueba de permisos se hace después de que existan dos cuentas válidas. Las correcciones se registrarán antes de cerrar el incremento.

Para el seguimiento, cada tarea debe tener estado pendiente, en proceso, en revisión o terminada, nombre de quien la atiende y evidencia del resultado. No se asignan fechas o responsables en este documento; el equipo los registrará en su tablero de trabajo.

### 1.3. Riesgos y respuesta

- **DTO distinto al formulario:** comparar los campos del backend antes de conectar el envío y ajustar los modelos Dart.
- **Fallos al probar desde un teléfono:** comprobar la dirección IP o host de la API, puertos, conectividad y HTTPS. `localhost` en el teléfono apunta al propio teléfono, no a la computadora.
- **Sesión o permisos incorrectos:** revisar los códigos `401` y `403` y validar autorización en el servidor.
- **Datos que solo aparecen en pantalla:** volver a entrar a la pantalla, consultar por API y verificar la persistencia real.

### 1.4. Definición de terminado

El incremento estará terminado cuando se hayan probado los diez criterios de aceptación, un negocio pueda crearse y consultarse desde una vista móvil, no sea visible para usuarios ajenos, los cambios aparezcan en Git y otra persona pueda repetir la prueba siguiendo el README. Cualquier función no verificada deberá permanecer marcada como pendiente.
