
# Qué es POSNEX y qué problema resuelve

POSNEX es un sistema pensado para micro y pequeños negocios, como tiendas, perfumerías y restaurantes. Buscamos que un dueño pueda administrar su comercio desde un celular sin depender de una computadora todo el tiempo.

Más adelante se podrían agregar ventas, inventario y herramientas diferentes para cada giro, pero primero necesitamos una cuenta y un negocio bien registrados.

La base de trabajo descrita para el proyecto utiliza:

- **Angular 20** para la interfaz.
- **ASP.NET Core** para la API.
- **PostgreSQL** para almacenar datos.

En este incremento nos enfocaremos en que la interfaz sea cómoda en un teléfono y que guarde la información mediante la API.

> No se requiere generar una aplicación Android instalable para terminar esta tarea.

# Objetivo y usuarios

**Objetivo:** completar y comprobar el flujo de registro de usuario, inicio de sesión, alta de negocio y consulta posterior del negocio desde una pantalla móvil.

**Usuario principal:** propietario de un negocio que entra desde su teléfono. Debe poder llenar los formularios, identificar errores y regresar a su información sin volver a registrar el comercio.

# Reglas del incremento

1. Para crear o consultar un negocio, el propietario debe iniciar sesión.
2. Cada negocio debe quedar asociado a su propietario y la API debe validar esa relación.
3. Los datos se guardan en PostgreSQL a través de la API; el celular no se conecta directamente a la base de datos.
4. Un formulario no debe mostrar que guardó correctamente hasta recibir confirmación del servidor.
5. Los campos obligatorios deben validarse y los errores deben explicarse en la pantalla.
6. Las credenciales y cadenas de conexión no se suben al repositorio ni aparecen en capturas.
7. Los datos simulados pueden usarse para diseñar pantallas, pero no cuentan como evidencia de persistencia real.

# Decisiones aprobadas y pendientes

| Estado | Decisión | Justificación o siguiente revisión |
|---|---|---|
| **Aprobada para el incremento** | Priorizar registro, inicio de sesión y creación de negocio desde el celular. | Es la base necesaria antes de agregar módulos de ventas. |
| **Aprobada para el incremento** | Continuar con la interfaz Angular responsiva y reutilizar la API existente. | Permite probar el flujo sin mantener dos aplicaciones distintas. |
| **Aprobada para el incremento** | Comprobar persistencia y permisos con datos reales. | La pantalla por sí sola no demuestra que el negocio quedó guardado. |
| **Pendiente de confirmar en código** | Contratos, nombres de rutas y campos exactos de registro, sesión y negocio. | Se tomarán del backend antes de conectar los formularios. |
| **Pendiente de confirmar en código** | Versión precisa de SDK, variables de entorno y configuración de la API. | Se documentarán al revisar el repositorio. |
| **Pendiente de decisión futura** | App instalable, funcionamiento sin Internet y módulos por giro. | No forman parte de la entrega de este incremento. |

# Restricciones

- El incremento debe funcionar primero en el navegador de un teléfono o en las herramientas de vista móvil.
- No se deben inventar respuestas de API ni dar por terminada una pantalla que aún use datos locales simulados.
- Las pruebas deben incluir al menos dos usuarios para comprobar que un negocio no aparece en cuentas ajenas.
- La configuración para desarrollo no debe exponer secretos ni depender de una URL fija de `localhost` cuando se prueba con un celular físico.
- Los cambios y pruebas se registrarán en el repositorio del proyecto; la URL y los commits exactos deben verificarse.
