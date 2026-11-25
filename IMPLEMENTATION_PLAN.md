
# Pasos de trabajo

| Paso | Actividad concreta | Entregable y comprobación |
|---|---|---|
| **1** | Revisar carpetas, formularios, servicios Angular, endpoints y modelos del backend. | Lista de rutas y campos reales que se utilizarán. |
| **2** | Ajustar diseño, etiquetas y validaciones para uso en celular. | Formularios probados a 360, 390 y 430 px. |
| **3** | Conectar registro e inicio de sesión con la API y manejar errores de autenticación. | Cuenta y sesión creadas con solicitudes reales. |
| **4** | Integrar el alta del negocio y su consulta posterior. | Negocio guardado y recuperado sin duplicados. |
| **5** | Verificar acceso y propiedad con dos usuarios diferentes. | Prueba de autorización exitosa y rechazo a usuario ajeno. |
| **6** | Ejecutar CA01 a CA10, corregir fallos y volver a probar. | Registro de resultados con evidencia por criterio. |
| **7** | Registrar cambios y actualizar el README de ejecución móvil. | Commits identificables e instrucciones reproducibles. |

# Orden y seguimiento

El paso 1 va primero porque todavía debemos confirmar las rutas y los campos reales.

Los pasos 2 y 3 pueden avanzar juntos una vez conocidos los contratos. La prueba de persistencia depende del alta de negocio; la prueba de permisos se hace después de que existan dos cuentas válidas.

Las correcciones se registrarán antes de cerrar el incremento.

Para el seguimiento, cada tarea debe tener:

- Estado: pendiente, en proceso, en revisión o terminada.
- Nombre de quien la atiende.
- Evidencia del resultado.

No se asignan fechas o responsables ficticios en este documento; el equipo los registrará en su tablero de trabajo.

# Riesgos y respuesta

| Riesgo | Respuesta |
|---|---|
| **DTO distinto al formulario** | Comparar los campos del backend antes de conectar el envío y ajustar los modelos de TypeScript. |
| **Fallos al probar desde un teléfono** | Comprobar IP local, puertos, CORS y certificados; `localhost` en el teléfono no apunta a la computadora. |
| **Sesión o permisos incorrectos** | Revisar los códigos `401` y `403` y validar autorización en el servidor. |
| **Datos que solo aparecen en pantalla** | Recargar, consultar por API y verificar la persistencia real. |

# Definición de terminado

El incremento estará terminado cuando se cumplan las siguientes condiciones:

- Se hayan probado los diez criterios de aceptación.
- Un negocio pueda crearse y consultarse desde una vista móvil.
- El negocio no sea visible para usuarios ajenos.
- Los cambios aparezcan en Git.
- Otra persona pueda repetir la prueba siguiendo el README.

Cualquier función no verificada deberá permanecer marcada como pendiente.
