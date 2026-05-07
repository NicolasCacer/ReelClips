# 🎬 ReelClips — Plataforma de Videos Cortos e Interacciones

Proyecto desarrollado para la asignatura **Diseño y Arquitectura de Software** de la **Universidad de La Sabana — Facultad de Ingeniería**.

ReelClips es una plataforma enfocada en el consumo, creación y compartición de videos cortos, permitiendo la interacción social mediante likes, comentarios, categorías, feed dinámico y chat entre usuarios.

## 👥 Equipo de trabajo

| Integrante                    | Rol                 |
| ----------------------------- | ------------------- |
| Nicolas Joel Cáceres Parra    | Desarrollo Frontend |
| Jorge Luis Alarcón Isturiz    | Desarrollo Backend  |
| Daniel Felipe Esquinas Suarez | Desarrollo Backend  |
| Eduard Meza Salazar           | Desarrollo Backend  |
| Juan José Campos Covaleda     | Desarrollo Backend  |

**Docente:** Wilmer Fabian Triana Pulgarín
**Curso:** Diseño y Arquitectura de Software
**Semestre:** 2026-1

## 🎯 Objetivo del proyecto

Desarrollar un sistema de información que permita a los usuarios consumir, crear y compartir videos cortos, con el fin de ofrecer una plataforma enfocada en la libre expresión digital, la interacción social y el descubrimiento de contenido dinámico, accesible y centrado en la experiencia del usuario.

## ⚙️ Requerimientos funcionales

### Gestión de usuarios

| ID    | Requerimiento                                                                                            |
| ----- | -------------------------------------------------------------------------------------------------------- |
| RF-01 | El sistema debe permitir a un usuario registrarse proporcionando nombre de usuario, correo y contraseña. |
| RF-02 | El sistema debe permitir iniciar sesión mediante credenciales.                                           |
| RF-03 | El usuario debe poder cerrar sesión en cualquier momento.                                                |
| RF-04 | El usuario debe poder editar su perfil, foto y descripción.                                              |
| RF-05 | El sistema debe permitir visualizar perfiles de usuarios.                                                |
| RF-06 | El usuario debe poder desactivar su cuenta.                                                              |

### Gestión de reels

| ID    | Requerimiento                                                        |
| ----- | -------------------------------------------------------------------- |
| RF-07 | El sistema debe permitir publicar reels con descripción y categoría. |
| RF-08 | El usuario debe poder editar descripción y categorías de sus reels.  |
| RF-09 | El usuario debe poder eliminar sus reels.                            |
| RF-10 | El sistema debe permitir visualizar reels publicados.                |
| RF-11 | El sistema debe permitir compartir reels con otros usuarios. |

### Interacciones sociales

| ID    | Requerimiento                                                      |
| ----- | ------------------------------------------------------------------ |
| RF-12 | El sistema debe permitir reaccionar con likes a un reel.           |
| RF-13 | El usuario debe poder eliminar una reacción previamente realizada. |
| RF-14 | El sistema debe permitir comentar reels.                           |
| RF-15 | El usuario debe poder eliminar sus comentarios.                    |

### Sistema de chat

| ID    | Requerimiento                                                     |
| ----- | ----------------------------------------------------------------- |
| RF-16 | El sistema debe permitir iniciar conversaciones entre usuarios.   |
| RF-17 | El sistema debe permitir enviar mensajes de texto entre usuarios. |

### Gestión de categorías

| ID    | Requerimiento                                                                 |
| ----- | ----------------------------------------------------------------------------- |
| RF-18 | El sistema debe obligar a asignar al menos una categoría al publicar un reel. |
| RF-19 | El sistema debe permitir administrar categorías disponibles.                  |

### Feed de contenido

| ID    | Requerimiento                                                            |
| ----- | ------------------------------------------------------------------------ |
| RF-20 | El sistema debe mostrar un feed de reels públicos.                       |
| RF-21 | El usuario debe poder filtrar contenido por categorías.                  |
| RF-22 | El sistema debe cargar contenido continuamente mediante scroll infinito. |

## 📌 Reglas de negocio

### Cuentas de usuario

| ID    | Regla                                                                                                 |
| ----- | ----------------------------------------------------------------------------------------------------- |
| RN-01 | Cada usuario debe tener un identificador único dentro de la plataforma.                               |
| RN-02 | Solo usuarios autenticados pueden publicar, reaccionar, comentar o iniciar chats.                     |
| RN-03 | Cada cuenta crea automáticamente un canal personal único.                                             |
| RN-04 | El nombre de usuario solo puede modificarse una vez cada 30 días.                                     |
| RN-05 | Una cuenta desactivada conserva reels y mensajes durante 30 días antes de eliminarse permanentemente. |

### Publicación de reels

| ID    | Regla                                                        |
| ----- | ------------------------------------------------------------ |
| RN-06 | Los reels deben tener máximo 90 segundos y 500 MB de tamaño. |
| RN-07 | Todo reel debe tener al menos una categoría asignada.        |
| RN-08 | Solo el propietario del reel puede editarlo o eliminarlo.    |
| RN-09 | Todo reel publicado es público por defecto.                  |

### Feed de contenido

| ID    | Regla                                                                               |
| ----- | ----------------------------------------------------------------------------------- |
| RN-10 | El feed principal muestra contenido de toda la comunidad.                           |
| RN-11 | El sistema organiza y filtra contenido según categorías e historial de interacción. |
| RN-12 | Los reels propios no aparecen en el feed de descubrimiento del usuario.             |
| RN-13 | Cada usuario puede dejar únicamente una reacción por reel.                          |
| RN-14 | El feed debe precargar contenido para soportar scroll infinito.                     |

### Chat directo

| ID    | Regla                                                                                           |
| ----- | ----------------------------------------------------------------------------------------------- |
| RN-15 | Solo usuarios registrados pueden participar en chats.                                           |
| RN-16 | Las conversaciones son exclusivamente uno a uno.                                                |
| RN-17 | Cualquier usuario autenticado puede iniciar conversaciones.                                     |
| RN-18 | Los mensajes permanecen almacenados persistentemente.                                           |
| RN-19 | Los mensajes pueden contener texto y referencias a reels, pero no archivos multimedia directos. |

## 🏗️ Arquitectura propuesta

El sistema adopta una arquitectura de **Monolito Modular**, permitiendo mantener una única aplicación desplegable organizada internamente por módulos independientes y desacoplados.

### Módulos principales

| Módulo        | Responsabilidad                                     |
| ------------- | --------------------------------------------------- |
| Usuarios      | Registro, autenticación y gestión de perfiles       |
| Reels         | Publicación, edición y visualización de videos      |
| Feed          | Filtrado, paginación y personalización de contenido |
| Categorías    | Gestión de categorías temáticas                     |
| Interacciones | Likes, comentarios y eventos sociales               |
| Chat          | Conversaciones y mensajes directos                  |
| Streaming     | Gestión de acceso y caché de videos                 |
| Persistencia  | Acceso centralizado a base de datos                 |

## 📂 Estructura prevista del proyecto

```text
src/main/java/com/reelclips/
│
├── ReelClipsApplication.java ← Main (paquete raíz)
│
├── usuarios/
│ ├── api/
│ │ ├── UsuarioModuloApi.java ← Interfaz pública del módulo
│ │ └── dto/
│ │ ├── UsuarioInfo.java ← DTO público (record)
│ │ └── PerfilInfo.java ← DTO público (record)
│ ├── internal/
│ │ ├── model/
│ │ │ ├── Usuario.java ← Entidad JPA
│ │ │ └── Canal.java ← Entidad JPA
│ │ ├── repository/
│ │ │ ├── UsuarioRepository.java
│ │ │ └── CanalRepository.java
│ │ └── service/
│ │ └── UsuarioService.java ← RF-01 al RF-06
│ └── UsuariosModulo.java ← Fachada (implementa UsuarioModuloApi)
│
├── reels/
│ ├── api/
│ │ ├── ReelModuloApi.java ← Interfaz pública del módulo
│ │ └── dto/
│ │ └── ReelInfo.java ← DTO público (record)
│ ├── internal/
│ │ ├── model/
│ │ │ └── Reel.java ← Entidad JPA
│ │ ├── repository/
│ │ │ └── ReelRepository.java
│ │ ├── proxy/
│ │ │ ├── ProxyReel.java ← Patrón Proxy
│ │ │ ├── CacheVideo.java
│ │ │ ├── ServicioAutorizacion.java
│ │ │ ├── ServicioAlmacenamientoVideo.java
│ │ │ └── VideoStream.java
│ │ └── service/
│ │ └── ReelService.java ← RF-07 al RF-11 · usa UsuarioModuloApi
│ └── ReelsModulo.java ← Fachada (implementa ReelModuloApi)
│
├── categorias/
│ ├── api/
│ │ ├── CategoriaModuloApi.java ← Interfaz pública del módulo
│ │ └── dto/
│ │ └── CategoriaInfo.java ← DTO público (record)
│ ├── internal/
│ │ ├── model/
│ │ │ └── Categoria.java ← Entidad JPA
│ │ ├── repository/
│ │ │ └── CategoriaRepository.java
│ │ └── service/
│ │ ├── ServicioFiltroCategorias.java ← RF-21
│ │ └── ServicioAdminCategorias.java ← RF-19 (admin)
│ └── CategoriasModulo.java ← Fachada (implementa CategoriaModuloApi)
│
├── feed/
│ ├── api/
│ │ └── dto/
│ │ └── FeedResponse.java ← DTO de respuesta paginada
│ ├── internal/
│ │ └── service/
│ │ ├── ServicioFiltroVisibilidad.java ← RF-20, RN-10, RN-12
│ │ └── ServicioPaginacion.java ← RF-22, RN-14
│ └── FacadeFeed.java ← Patrón Facade · usa Reels, Categorias, Usuarios
│
├── interacciones/
│ ├── api/
│ │ └── dto/
│ │ └── InteraccionInfo.java
│ ├── internal/
│ │ ├── model/
│ │ │ ├── Reaccion.java ← Entidad JPA · RF-12, RF-13
│ │ │ ├── Comentario.java ← Entidad JPA · RF-14, RF-15
│ │ │ └── EventoInteraccion.java ← Entidad de evento
│ │ ├── repository/
│ │ │ ├── ReaccionRepository.java
│ │ │ └── ComentarioRepository.java
│ │ ├── observer/
│ │ │ ├── IObservador.java ← Interfaz Observer
│ │ │ ├── PublicadorEventosInteraccion.java ← Subject
│ │ │ ├── NotificadorAutor.java ← Observer
│ │ │ ├── ActualizadorMetricas.java ← Observer
│ │ │ └── AnalizadorActividad.java ← Observer
│ │ └── service/
│ │ └── InteraccionService.java ← RF-12 al RF-15 · usa ReelModuloApi
│ └── InteraccionesModulo.java
│
├── chat/
│ ├── api/
│ │ └── dto/
│ │ ├── ConversacionInfo.java
│ │ └── MensajeInfo.java
│ ├── internal/
│ │ ├── model/
│ │ │ ├── Conversacion.java ← Entidad JPA
│ │ │ ├── ParticipanteConversacion.java ← Entidad JPA
│ │ │ └── Mensaje.java ← Entidad JPA
│ │ ├── repository/
│ │ │ ├── ConversacionRepository.java
│ │ │ └── MensajeRepository.java
│ │ └── service/
│ │ └── ChatService.java ← RF-16, RF-17 · usa UsuarioModuloApi
│ └── ChatModulo.java
│
└── shared/
 ├── db/
 │ └── ConexionBD.java ← Patrón Singleton
 ├── enums/
 │ ├── EstadoReel.java
 │ ├── EstadoCuenta.java
 │ └── TipoMensaje.java
 └── exception/
 ├── ReglaNegocioException.java
 ├── RecursoNoEncontradoException.java
 ├── AccesoDenegadoException.java
 └── GlobalExceptionHandler.java
```

## 🧩 Patrones de diseño aplicados

| Patrón    | Categoría      | Aplicación                           |
| --------- | -------------- | ------------------------------------ |
| Singleton | Creacional     | Gestión centralizada de persistencia |
| Facade    | Estructural    | Construcción simplificada del feed   |
| Proxy     | Estructural    | Control de acceso y caché de videos  |
| Observer  | Comportamiento | Manejo de eventos e interacciones    |

## 🚀 Atributos de calidad

### Rendimiento (Atributo dominante)

* Tiempo de carga inicial de videos menor o igual a 2 segundos.
* Cambio de reels en máximo 1 segundo.
* Carga de comentarios menor o igual a 1.5 segundos.

### Otros atributos relevantes

* Escalabilidad
* Usabilidad
* Disponibilidad
* Mantenibilidad

## 🔄 Evolución arquitectónica

### Estado inicial

El sistema inicia como un monolito modular debido al tamaño del equipo, la complejidad manejable del dominio y el alcance académico del proyecto.

### Evolución futura

Los módulos de streaming y feed podrían extraerse posteriormente como servicios independientes si aumentan significativamente las necesidades de rendimiento y escalabilidad.

## 💻 Stack tecnológico

| Capa                 | Tecnología                       |
| -------------------- | -------------------------------- |
| Frontend             | Next.js + TypeScript             |
| Backend              | Spring Boot + Java               |
| Base de datos        | PostgreSQL                       |
| Caché                | Redis                            |
| Mensajería           | REST API + Polling               |
| DevOps               | Docker + GitHub Actions + Vercel |
| Control de versiones | Git + GitHub                     |

## ▶️ Ejecución del proyecto

### Backend

```bash
./mvnw spring-boot:run
```

### Frontend

```bash
npm install
npm run dev
```

### Docker

```bash
docker compose up
```

## 📚 Estado del proyecto

Actualmente ReelClips se encuentra en fase de análisis y diseño arquitectónico.

El proyecto ya cuenta con:

* Objetivo del sistema
* Requerimientos funcionales
* Reglas de negocio
* Diagrama UML
* Evaluación de patrones GoF
* Atributos de calidad
* Estilo arquitectónico
* Stack tecnológico
* Estructura modular propuesta