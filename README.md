# POSNEX Mobile

POSNEX Mobile es una aplicación móvil desarrollada con Flutter y Dart, diseñada para ofrecer acceso a las funcionalidades de POSNEX desde dispositivos móviles Android y iOS.

La aplicación se comunica con POSNEX API, desarrollada en ASP.NET Core, mediante servicios REST. La lógica de negocio y la persistencia de información se gestionan desde el backend utilizando PostgreSQL.

## Tecnologías utilizadas

| Tecnología | Descripción |
|---|---|
| Flutter | Framework para desarrollo de aplicaciones móviles multiplataforma. |
| Dart | Lenguaje de programación utilizado por Flutter. |
| ASP.NET Core | Tecnología utilizada para los servicios del backend. |
| PostgreSQL | Sistema de gestión de base de datos utilizado por el backend. |
| REST API | Mecanismo de comunicación entre la aplicación móvil y el backend. |

Las versiones exactas de Flutter, Dart y los paquetes utilizados se deben consultar en el entorno de desarrollo y en los archivos `pubspec.yaml` y `pubspec.lock`.

## Requisitos de desarrollo

Para ejecutar el proyecto se requiere:

- Flutter SDK.
- Dart SDK (incluido con Flutter).
- Android Studio.
- Android SDK.
- Emulador Android o dispositivo físico.
- Visual Studio Code o Android Studio como entorno de desarrollo.
- Acceso a POSNEX API.

Para comprobar la instalación:

```bash
flutter --version
dart --version
flutter doctor -v
```

## Configuración del backend

La aplicación móvil consume los servicios de POSNEX API.

**Dirección del backend en desarrollo:**

```text
http://localhost:5071
```

La dirección debe adaptarse dependiendo del dispositivo utilizado:

| Entorno | Dirección |
|---|---|
| Emulador Android | `http://10.0.2.2:5071` |
| Dispositivo físico | Dirección IP local de la computadora donde se ejecuta la API. |
| Producción | Dominio HTTPS del backend. |

**Importante:** en un emulador o dispositivo físico, `localhost` hace referencia al propio dispositivo y no necesariamente a la computadora donde se ejecuta el backend.

La dirección base de la API debe configurarse mediante el mecanismo de configuración implementado en el proyecto, evitando utilizar direcciones locales en producción.

## Instalación y ejecución

Clonar el repositorio:

```bash
git clone https://github.com/JuandaMonkey/MOBILE-POSNEX.git
```

Ingresar al directorio del proyecto:

```bash
cd POSNEX-MOBILE
```

Instalar las dependencias:

```bash
flutter pub get
```

Verificar los dispositivos disponibles:

```bash
flutter devices
```

Ejecutar la aplicación:

```bash
flutter run
```

Para ejecutar en un dispositivo específico:

```bash
flutter run -d DEVICE_ID
```

## Integración con POSNEX API

La aplicación móvil consume los endpoints disponibles en el backend.

### Autenticación

Base: `/api/v1/auth`

| Método | Endpoint | Descripción |
|---|---|---|
| POST | `/register` | Registro de usuarios. |
| POST | `/login` | Inicio de sesión. |
| POST | `/refresh` | Renovación de sesión. |

### Administración de negocios

Base: `/api/v1/businesses`

| Método | Endpoint | Descripción |
|---|---|---|
| GET | `/api/v1/businesses` | Lista los negocios del usuario autenticado. |
| POST | `/api/v1/businesses` | Registra un negocio. |
| GET | `/api/v1/businesses/{id}` | Consulta un negocio específico. |
| PUT | `/api/v1/businesses/{id}` | Actualiza la información del negocio. |
| DELETE | `/api/v1/businesses/{id}` | Realiza la eliminación lógica del negocio. |

Los endpoints de negocios requieren autenticación mediante un token Bearer.

El backend administra las membresías de los usuarios y verifica que cada operación corresponda a un negocio al que el usuario tenga acceso.

### Documentación de la API

Durante el desarrollo, Swagger se encuentra disponible en:

```text
http://localhost:5071/swagger
```

## Seguridad

La aplicación debe considerar las siguientes medidas de seguridad:

- No almacenar contraseñas directamente en el dispositivo.
- No incluir tokens, contraseñas o credenciales en el código fuente.
- Utilizar almacenamiento seguro para los tokens cuando sea necesario conservarlos en el dispositivo.
- Utilizar HTTPS en ambientes de producción.
- No exponer información sensible en los registros de depuración.
- Validar las respuestas y errores recibidos desde el backend.
- Respetar los permisos y restricciones definidos por la API.

La autenticación y autorización de las operaciones son responsabilidad del backend.

## Compilación

### Android

Generar APK de producción:

```bash
flutter build apk --release
```

Generar Android App Bundle:

```bash
flutter build appbundle --release
```

### iOS

La compilación para iOS requiere macOS y Xcode:

```bash
flutter build ios --release
```

## Pruebas y análisis

Ejecutar el análisis estático del proyecto:

```bash
flutter analyze
```

Ejecutar las pruebas automatizadas:

```bash
flutter test
```

Se recomienda validar:

- Funcionamiento del inicio de sesión.
- Comunicación con POSNEX API.
- Manejo de errores y respuestas del servidor.
- Funcionamiento en emuladores y dispositivos físicos.
- Comportamiento ante pérdida de conexión.
- Validación de formularios.
- Acceso a los negocios autorizados.

## Repositorios relacionados

- **Backend:** [BACK-END-POSNEX](https://github.com/carlosmelendrez31/BACK-END-POSNEX)
- **Frontend móvil:** [MOBILE-POSNEX](https://github.com/JuandaMonkey/MOVIL-POSNEX)

## Estado del proyecto

La aplicación móvil forma parte del ecosistema POSNEX y utiliza el backend independiente para la autenticación, administración de usuarios y gestión de negocios.

El estado de implementación de los módulos móviles debe documentarse de acuerdo con el código disponible en este repositorio.

Los módulos y funcionalidades pendientes deben identificarse antes de considerarlos implementados o conectados a la API.
