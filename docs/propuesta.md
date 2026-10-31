# SosFit · Coach Esther

Propuesta inicial e investigación — 31 de octubre de 2026.

## La primera versión

Una web adaptada al teléfono donde cada cliente accede a sus rutinas, toca un ejercicio para ver su demostración y registra su entrenamiento. La marca inicial utiliza únicamente «SosFit» y «Coach Esther», sin inventar un logo.

La demo entregada incluye tres sesiones de ejemplo, seis ilustraciones animadas originales, biblioteca con búsqueda y filtros, registro de repeticiones/carga, temporizador y progreso guardado en el navegador. El contenido de entrenamiento es de ejemplo; Esther debe revisar los movimientos y las prescripciones antes de publicarlos para sus clientes.

La pantalla de acceso es una propuesta visual. Google no está conectado. La demo no tiene cuentas reales, base de datos ni cobros, y sus archivos estáticos no protegen contenido de pago. Los registros locales no se sincronizan ni identifican a una persona.

## Demostraciones: alternativas investigadas

| Alternativa | Qué ofrece | Decisión para SosFit |
| --- | --- | --- |
| wger | Proyecto abierto y API REST. Sus endpoints públicos de ejercicios se consultan sin autenticación. | Candidato para evaluar contenido sin pagar una API. Hay que comprobar disponibilidad de animación o vídeo para cada ejercicio y conservar su autor/licencia; no asumir cobertura completa. |
| ExerciseDB V1 de AscendAPI, versión gratuita | Catálogo con GIF y datos de ejercicios. Sus condiciones excluyen productos comerciales y cualquier uso monetizado sin plan de pago. | No utilizar la versión gratuita para vender rutinas. |
| Contenido propio | Vídeos de Esther o animaciones producidas para SosFit. | Mi recomendación para los ejercicios principales: controlar calidad, instrucciones en español y disponibilidad. Requiere trabajo de producción, alojamiento y validación. |

La documentación de wger distingue el software AGPL de los datos iniciales CC-BY-SA; algunas imágenes tienen fuentes adicionales. Antes de incorporar medios a SosFit se debe revisar la ficha concreta de cada uno. No se ha incorporado contenido de wger ni ExerciseDB a la demo. [Documentación y licencias de wger](https://wger.readthedocs.io/en/latest/), [API de wger](https://wger.readthedocs.io/en/latest/api/api.html), [condiciones de ExerciseDB gratuito](https://oss.exercisedb.dev/docs).

La página pública de wger presentó una protección automatizada durante la investigación; se consultó su documentación oficial y no se verificó el rendimiento de la API desde la aplicación. Por eso aún no se recomienda como dependencia definitiva.

Si se adopta una biblioteca externa, cada ejercicio debe guardar el proveedor, identificador externo, URL del medio, créditos y licencia. La app debe ofrecer instrucciones en texto y un estado claro cuando no se pueda cargar el vídeo. La posibilidad de alojar copias depende de los términos del proveedor.

## Acceso con Google

Es viable con Google Identity Services. Hace falta un proyecto de Google Cloud, un cliente OAuth web y registrar los orígenes de la aplicación. También se configura la marca de la aplicación y la política de privacidad. [Configuración oficial de Google](https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid).

El servidor debe validar la firma, el destinatario, el emisor y la caducidad del token, y asociar la cuenta al identificador `sub`. Después establece la sesión de SosFit. Iniciar sesión identifica al usuario; el servidor de SosFit determina qué rutinas compró o tiene asignadas. [Verificación oficial del token](https://developers.google.com/identity/gsi/web/guides/verify-google-id-token).

No hace falta compartir tu contraseña de Google ni de GitHub en el chat. Las credenciales privadas se configuran como secretos del alojamiento elegido.

## Qué añadir para que tenga valor pagar

Estas son prioridades propuestas para SosFit. Como referencia de mercado, Trainerize agrupa programación de entrenamientos, seguimiento, gestión de clientes y pagos; no es necesario copiar toda esa plataforma. [Funciones de Trainerize](https://www.trainerize.com/features/).

| Prioridad | Función | Valor concreto |
| --- | --- | --- |
| Lanzamiento | Panel de Esther para crear, duplicar y asignar rutinas | Gestionar clientes sin editar código ni enviar archivos por separado. |
| Lanzamiento | Rutina con series, repeticiones, descanso, carga e instrucciones | Guiar la sesión completa en un mismo lugar. |
| Lanzamiento | Demostraciones revisadas por Esther | Entender el movimiento sin salir a buscarlo. |
| Lanzamiento | Registro de cargas y repeticiones por fecha | Consultar la sesión anterior y revisar la evolución. |
| Lanzamiento | Compra y acceso según producto o vigencia | Entregar automáticamente lo comprado y gestionar renovaciones. |
| Lanzamiento | Perfil inicial con objetivo, experiencia y equipo disponible | Ayudar a Esther a escoger una rutina apropiada. |
| Siguiente fase | Revisión semanal y comentarios de Esther | Dar acompañamiento y ajustar los planes según el seguimiento. |
| Siguiente fase | Alternativas de ejercicios revisadas por la coach | Continuar cuando falta equipo o se necesita otra variante. |
| Siguiente fase | Calendario y recordatorios voluntarios | Facilitar la constancia sin saturar de notificaciones. |
| Siguiente fase | Web instalable en el teléfono | Acceder a SosFit con un icono y una experiencia cómoda en móvil. |

Conviene dejar chat en tiempo real, integraciones con relojes y recomendaciones automáticas para después de validar el uso de las rutinas. Un canal de consultas y revisión semanal puede cubrir el acompañamiento inicial con menos complejidad.

## Arquitectura propuesta para la versión de pago

Separar la interfaz, la autenticación, los permisos y los datos duraderos. La demo estática sirve para revisar la experiencia; la versión comercial necesita servidor.

- Usuarios con roles de cliente y coach.
- Biblioteca de ejercicios y medios con créditos/licencia.
- Rutinas, versiones y asignaciones por cliente.
- Sesiones de entrenamiento y registros por serie.
- Productos, compras y derechos de acceso con fecha de vigencia cuando corresponda.
- Confirmación de pagos en servidor mediante notificaciones firmadas del proveedor; no confiar en la pantalla de «pago exitoso» del navegador.

La elección de pasarela depende del país del negocio, moneda, cuenta bancaria y modalidad de venta. No se ha elegido ni conectado un proveedor de cobros. Tampoco se han contratado servicios ni planes de API.

## Decisiones pendientes

1. Vender rutinas individuales, una membresía o ambos modelos.
2. Determinar si Esther asigna planes personalizados o el cliente compra programas comunes.
3. Definir el país y la moneda del negocio para investigar cobros compatibles.
4. Revisar colores, textos, ejercicios y estilo de las demostraciones con Esther.
5. Configurar el proyecto de Google y decidir la visibilidad del repositorio de GitHub (actualmente público).

## Estado de la entrega

La sintaxis de JavaScript y la coherencia de los archivos pueden verificarse localmente. La revisión visual e interacción en navegador quedó pendiente: el control del navegador en Windows se detuvo al no poder determinar con seguridad la URL actual. El usuario creó el repositorio `NigelCastilloR/sosfit`, configurado como público, y se incorporó el código de la demo mediante la conexión de GitHub.
