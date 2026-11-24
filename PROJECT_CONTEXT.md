# PROJECT_CONTEXT.md — Contexto del proyecto

Este documento organiza el trabajo del siguiente incremento de POSNEX. La meta es que una persona pueda usar el sistema desde su celular para registrarse, iniciar sesión y dar de alta su negocio. Se separa lo que ya se decidió, lo que debemos revisar en el código y lo que todavía no vamos a desarrollar.

### 1.1. Qué es POSNEX y qué problema resuelve

POSNEX es un sistema pensado para micro y pequeños negocios, como tiendas, perfumerías y restaurantes. Buscamos que un dueño pueda administrar su comercio desde un celular sin depender de una computadora todo el tiempo. Más adelante se podrían agregar ventas, inventario y herramientas diferentes para cada giro, pero primero necesitamos una cuenta y un negocio bien registrados.

La aplicación móvil de POSNEX se desarrolla completamente con **Flutter (Dart)**. Flutter constituye el cliente móvil y se comunica mediante solicitudes HTTP/HTTPS con una API de **ASP.NET Core**. **PostgreSQL** almacena los datos. La aplicación no se conecta directamente a la base de datos: las operaciones se realizan a través de la API.

### 1.2. Objetivo y usuarios

**Objetivo:** completar y comprobar el flujo de registro de usuario, inicio de sesión, alta de negocio y consulta posterior del negocio desde la aplicación Flutter.

**Usuario principal:** propietario de un negocio que entra desde su teléfono. Debe poder llenar los formularios, identificar errores y regresar a su información sin volver a registrar el comercio.

### 1.3. Reglas del incremento

1. Para crear o consultar un negocio, el propietario debe iniciar sesión.
2. Cada negocio debe quedar asociado a su propietario y la API debe validar esa relación.
3. Los datos se guardan en PostgreSQL a través de la API; el celular no se conecta directamente a la base de datos.
4. Un formulario no debe mostrar que guardó correctamente hasta recibir confirmación del servidor.
5. Los campos obligatorios deben validarse y los errores deben explicarse en la pantalla.
6. Las credenciales y cadenas de conexión no se suben al repositorio ni aparecen en capturas.
7. Los datos simulados pueden usarse para diseñar pantallas, pero no cuentan como evidencia de persistencia real.

### 1.4. Decisiones aprobadas y pendientes

| Estado | Decisión | Justificación o siguiente revisión |
|---|---|---|
| Aprobada para el incremento | Priorizar registro, inicio de sesión y creación de negocio desde el celular. | Es la base necesaria antes de agregar módulos de ventas. |
| Aprobada para el incremento | Desarrollar la aplicación móvil completamente con Flutter y reutilizar la API existente. | Flutter será el cliente móvil; se evita duplicar la lógica del backend. |
| Aprobada para el incremento | Comprobar persistencia y permisos con datos reales. | La pantalla por sí sola no demuestra que el negocio quedó guardado. |
| Pendiente de confirmar en código | Contratos, nombres de rutas y campos exactos de registro, sesión y negocio. | Se tomarán del backend antes de conectar los formularios. |
| Pendiente de confirmar en código | Versión precisa de Flutter SDK/Dart, variables de entorno y configuración de la API. | Se documentarán al revisar el repositorio. |
| Pendiente de decisión futura | Funcionamiento sin Internet y módulos por giro. | No forman parte de la entrega de este incremento. |

### 1.5. Restricciones

- El incremento debe ejecutarse como aplicación Flutter en un emulador o teléfono físico; no depende de un navegador web.
- No se deben inventar respuestas de API ni dar por terminada una pantalla que aún use datos locales simulados.
- Las pruebas deben incluir al menos dos usuarios para comprobar que un negocio no aparece en cuentas ajenas.
- La configuración para desarrollo no debe exponer secretos ni depender de una URL fija de `localhost` cuando se prueba con un celular físico. La dirección de la API debe ser alcanzable desde el dispositivo.
- Los cambios y pruebas se registrarán en el repositorio del proyecto; la URL y los commits exactos deben verificarse.
