# POSNEX

Sistema de gestión de negocios desarrollado con una arquitectura cliente-servidor, compuesto por un frontend y una API backend, utilizando PostgreSQL como sistema de gestión de base de datos.

## 1. Repositorios del proyecto

El proyecto se encuentra dividido en dos repositorios independientes:

| Componente | Repositorio |
|---|---|
| Frontend | [FRONT-END-POSNEX](https://github.com/carlosmelendrez31/FRONT-END-POSNEX) |
| Backend | [BACK-END-POSNEX](https://github.com/carlosmelendrez31/BACK-END-POSNEX) |

## 2. Requisitos previos

Antes de ejecutar el proyecto, es necesario contar con las siguientes herramientas:

- **Git:** para clonar y administrar los repositorios.
- **Node.js y npm:** versiones compatibles con el frontend.
- **SDK de .NET:** versión requerida por el proyecto backend.
- **PostgreSQL:** sistema de gestión de base de datos.
- **Navegador web:** para ejecutar y probar la aplicación.
- **Editor de código:** Visual Studio Code, Visual Studio u otro compatible.

También es necesario contar con los archivos de configuración y credenciales locales correspondientes. No se deben publicar contraseñas, cadenas de conexión ni otros datos sensibles en GitHub.

## 3. Descargar el proyecto

Clonar ambos repositorios desde una terminal:

```bash
git clone https://github.com/carlosmelendrez31/FRONT-END-POSNEX.git
git clone https://github.com/carlosmelendrez31/BACK-END-POSNEX.git
```

Comprobar que los repositorios se hayan descargado correctamente:

```bash
git -C FRONT-END-POSNEX remote -v
git -C BACK-END-POSNEX remote -v
```

## 4. Instrucciones de ejecución

### 4.1. Preparar y ejecutar el Backend

1. Acceder a la carpeta del backend.
2. Identificar la solución `.sln` o el proyecto `.csproj` correspondiente a la API.
3. Verificar que se encuentre instalado el SDK de .NET requerido.
4. Configurar la conexión a PostgreSQL utilizando el mecanismo de configuración definido por el proyecto.

Acceder al repositorio:

```bash
cd BACK-END-POSNEX
```

Restaurar las dependencias:

```bash
dotnet restore
```

Ejecutar la API:

```bash
dotnet run
```

Al iniciar correctamente, la consola mostrará las direcciones en las que se encuentra disponible la API.

**Importante:** La cadena de conexión de PostgreSQL debe configurarse de acuerdo con los archivos reales del proyecto. No se deben utilizar credenciales inventadas ni publicar información sensible.

Si el proyecto utiliza migraciones, deberán ejecutarse únicamente después de verificar su configuración.

### 4.2. Preparar y ejecutar el Frontend

1. Acceder a la carpeta del frontend.
2. Verificar que exista el archivo `package.json`.
3. Comprobar los scripts disponibles y la configuración de la URL de la API.
4. Instalar las dependencias necesarias.

Acceder al repositorio:

```bash
cd FRONT-END-POSNEX
```

Instalar las dependencias:

```bash
npm ci
```

Consultar los scripts disponibles:

```bash
npm run
```

Iniciar la aplicación utilizando el script de desarrollo correspondiente.

```bash
npm start
```

**Nota:** El comando `npm ci` requiere un archivo `package-lock.json` válido. Si no existe, deberá revisarse el uso de `npm install`.

Asimismo, `npm start` solamente funcionará si el script `start` está definido en `package.json`. En caso contrario, deberá utilizarse el comando correspondiente a los scripts disponibles.

### 4.3. Pruebas desde dispositivos móviles

Para comprobar el funcionamiento de la aplicación en dispositivos móviles:

1. Iniciar el backend y verificar que la API responda correctamente.
2. Iniciar el frontend.
3. Abrir la aplicación desde un navegador.
4. Activar las herramientas de desarrollador y seleccionar la vista de dispositivo móvil.
5. Realizar pruebas con resoluciones de 360, 390 y 430 píxeles.
6. Comprobar que los formularios, botones y elementos de navegación se visualicen correctamente.

Para realizar pruebas desde un teléfono físico:

- Conectar el teléfono y la computadora a la misma red local.
- Identificar la dirección IP local de la computadora.
- Configurar el frontend para consumir la API mediante una dirección accesible desde el teléfono.
- Verificar que el firewall permita las conexiones necesarias.

En caso de utilizar Angular, puede habilitarse el acceso desde la red local mediante:

```bash
npx ng serve --host 0.0.0.0
```

Este comando debe utilizarse únicamente en una red de pruebas confiable y verificando el puerto configurado.

**Importante:** La dirección `localhost` desde un teléfono apunta al propio teléfono, no a la computadora donde se ejecuta la API.

## 5. Pruebas funcionales

Una vez iniciados ambos componentes, se recomienda realizar las siguientes pruebas para verificar el funcionamiento del sistema.

| Prueba | Resultado esperado |
|---|---|
| Registro de usuario | El sistema permite registrar una cuenta correctamente. |
| Inicio de sesión | El usuario puede autenticarse con sus credenciales. |
| Registro de negocio | El usuario autenticado puede crear un negocio. |
| Persistencia de datos | La información permanece disponible después de recargar la aplicación. |
| Control de acceso | Una segunda cuenta no puede consultar información privada de otro usuario. |
| Comunicación frontend-backend | Las solicitudes llegan correctamente a la API. |
| Manejo de errores | La interfaz informa cuando la API no está disponible. |
| Diseño responsivo | La aplicación se adapta correctamente a diferentes resoluciones móviles. |

Es importante comprobar que las operaciones se realicen realmente en el servidor y que los datos se almacenen en PostgreSQL. Una respuesta visual de éxito no demuestra por sí sola que la información se haya guardado.

## 6. Errores comunes

| Problema | Posible solución |
|---|---|
| El celular no puede acceder a la aplicación. | Verificar la IP local, el firewall, el puerto y la conexión de red. |
| El frontend inicia, pero no guarda información. | Revisar la URL de la API, CORS, autenticación y respuestas HTTP. |
| La API no inicia. | Comprobar el SDK de .NET, la configuración y los mensajes de error. |
| Error de conexión con PostgreSQL. | Verificar que el servicio esté activo y que las credenciales sean correctas. |
| `npm ci` presenta errores. | Comprobar la existencia y compatibilidad de `package-lock.json`. |
| `npm start` no funciona. | Consultar los scripts disponibles mediante `npm run`. |
| Los datos desaparecen al recargar. | Revisar que el backend y la base de datos estén realizando correctamente las operaciones de persistencia. |

## 7. Evidencias de ejecución y validación

Para comprobar el funcionamiento del proyecto, se recomienda recopilar las siguientes evidencias:

| Evidencia | Resultado esperado |
|---|---|
| Herramientas y versiones | Capturas o salida de los comandos que muestran las versiones instaladas. |
| Configuración | Archivos reales de configuración del frontend y backend, sin credenciales visibles. |
| Repositorios | Enlaces de GitHub, código fuente, ramas y commits. |
| Ejecución del backend | Terminal mostrando la API iniciada correctamente. |
| Ejecución del frontend | Terminal mostrando la aplicación disponible. |
| Pruebas móviles | Capturas de la aplicación funcionando en diferentes resoluciones. |
| Pruebas funcionales | Evidencias de registro, autenticación y gestión de negocios. |
| Persistencia | Comprobación de que los registros permanecen después de recargar la aplicación. |
| Control de acceso | Evidencia de que un usuario no puede acceder a información privada de otra cuenta. |

## 8. Consideraciones de seguridad

- No publicar contraseñas ni cadenas de conexión en los repositorios.
- Utilizar archivos de configuración locales para almacenar credenciales.
- Configurar correctamente las políticas CORS.
- Validar las solicitudes tanto en el frontend como en el backend.
- Implementar controles de autenticación y autorización en el servidor.
- Evitar confiar únicamente en las validaciones visuales del frontend.
- Verificar que cada usuario solamente pueda acceder a los recursos que tiene autorizados.

## 9. Estado de verificación

Las instrucciones anteriores describen el procedimiento general para preparar, ejecutar y probar POSNEX.

Los comandos, versiones de herramientas, rutas internas, variables de entorno y direcciones de conexión deberán contrastarse con la configuración real de cada repositorio antes de considerar validado el procedimiento de instalación.

---

**POSNEX**  
Proyecto de desarrollo de software.
