# SosFit · Coach Esther

Prototipo navegable, adaptable a móvil, sin herramientas de compilación. Todo el contenido de entrenamiento es de demostración y necesita revisión de Esther.

## Ejecutar

Sirve la carpeta `dist` con un servidor HTTP estático. No requiere instalar paquetes. `dist/index.html`, `styles.css` y `app.js` contienen la aplicación completa. Las fuentes se cargan de Google Fonts y hay alternativas locales.

## Funciones reales de la demo

- Tres sesiones de ejemplo y seis ejercicios con animaciones SVG originales específicas por movimiento.
- Biblioteca con búsqueda y filtros.
- Registro diario por sesión, repeticiones o segundos y carga opcional.
- Progreso e historial en localStorage, exclusivo de este navegador y origen.
- Temporizador de descanso con pausa y reinicio; se detiene al cerrar el ejercicio.
- Diálogos accesibles y opción de pausar la animación, respetando movimiento reducido.

## Lo que falta para producción

El botón Google muestra el estado de configuración: **no autentica ni simula autenticación**. No hay backend, cuentas, pagos, protección de rutinas ni sincronización. El contenido incluido es visible en el cliente y NO sirve para proteger contenido de pago.

1. Definir repositorio y arquitectura de servidor, base de datos y despliegue.
2. Configurar OAuth de Google con dominio, orígenes y política de privacidad; verificar tokens en servidor y emitir sesiones seguras.
3. Crear roles cliente y coach; Esther crea, publica y asigna planes a usuarios autenticados.
4. Servir rutinas desde el backend solo si el usuario tiene acceso vigente; validar pagos mediante webhooks firmados e idempotentes.
5. Sustituir o validar las ilustraciones con Esther. Si se usa wger, conservar autor, licencia y URL de cada recurso y cumplir sus términos. No usar la versión gratuita de ExerciseDB para monetización.
6. Migrar el seguimiento a base de datos por usuario con permisos y exportación/borrado de cuenta.

Las credenciales y los secretos no se incluyen en este repositorio. La configuración Sites en `.openai/hosting.json` identifica únicamente el hosting de la demo; no constituye un inicio de sesión de Google.
