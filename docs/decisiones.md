# Registro de decisiones técnicas

Cada decisión importante se apunta aquí con su fecha, qué se decidió, por qué y qué alternativas se descartaron. Sirve para que ninguna conversación con la IA la contradiga y como material directo para la memoria.

## D-01. Flutter como framework
**Fecha:** septiembre 2026
**Decisión:** desarrollar con Flutter y Dart.
**Motivo:** un único código para Windows, Android e iOS, encaja con el ciclo de DAM, rendimiento nativo y curva de aprendizaje asumible.
**Descartadas:** aplicación web con Electron (peor latencia de audio) y C++ con JUCE (curva de aprendizaje excesiva para un curso).

## D-02. Plataformas
**Fecha:** septiembre 2026
**Decisión:** Windows y Android como plataformas garantizadas; iOS como objetivo opcional.
**Motivo:** compilar para iOS requiere macOS (se usaría GitHub Actions) y sin cuenta de pago la app caduca a los 7 días en el iPhone.

## D-03. Backend (revisada)
**Fecha original:** septiembre 2026 · **Revisión:** octubre 2026
**Decisión original:** Supabase (PostgreSQL, Auth y Storage).
**Estado actual:** pendiente. Tras el kick-off, el profesor pidió no usar Supabase y construir un backend propio, así que la elección se hará en el Sprint 2 (diseño técnico), priorizando una opción gratuita, segura y mantenible.
**Sigue en pie:** Firebase descartado por exigir el plan de pago por uso para el almacenamiento en proyectos nuevos.

## D-04. Audio
**Fecha:** septiembre 2026
**Decisión:** flutter_soloud para reproducción y efectos, record para la grabación.
**Motivo:** baja latencia, control de la velocidad de reproducción (base del modo teclado) y filtros incluidos.
**Pendiente de validar:** latencia real en Android. La prueba de concepto del Sprint 1 solo ejecutó la app base de Flutter en Windows; la integración de estos paquetes se valida al empezar el desarrollo del audio.
**Dato comprobado (pub.dev, octubre 2026):** record exige Android API 23 como mínimo; flutter_soloud, API 21. Por eso el mínimo del proyecto es Android 6.0 (API 23).

## D-05. Presupuesto cero
**Fecha:** septiembre 2026
**Decisión:** todas las herramientas gratuitas o en plan gratuito. Distribución por GitHub Releases, sin Google Play ni App Store.

## D-06. Estrategia de ramas (revisada)
**Fecha:** noviembre 2026 · **Revisión:** noviembre 2026, tras la explicación del profesor
**Decisión:** Git Flow.
- `main`: rama principal del repositorio. Solo recibe lo entregado al final de cada sprint y las correcciones urgentes.
- `develop`: rama de integración. De ella salen las ramas de cada tarea del sprint y a ella vuelven mediante pull request.
- `feature/<nº-issue>-<descripcion>`: una rama corta por historia de usuario del tablero Kanban. Igual para `docs/...` y `chore/...`.
- Cierre de sprint: pull request de `develop` a `main` y etiqueta de versión en `main` (`v0.1.0` Sprint 1, `v0.2.0` Sprint 2, `v0.3.0` Sprint 3, `v1.0.0` versión final).
- `hotfix/<descripcion>`: si aparece un fallo en `main`, se crea desde `main`, se fusiona en `main` con versión de parche (`v0.1.1`...) y después en `develop`, para que las tareas en curso tengan la corrección.
**Versionado:** semántico, mayor.menor.parche.
**Motivo:** ramas cortas, fusiones pequeñas, trazabilidad con el Kanban y una rama `main` que siempre muestra la última versión entregada y estable.
**Descartadas:** una rama por sprint (acumula semanas de cambios sin integrar) y `develop` como rama principal (dejaba `main` sin uso hasta el final del curso).
**A tener en cuenta:** el repositorio es público, así que el plan gratuito permite proteger `main` con una regla de rama.

## D-07. Identidad visual
**Fecha:** noviembre 2026
**Decisión:** logo propio en blanco y negro: una S (Playfair Display Black) que proyecta hacia atrás y a la izquierda una sombra con forma de clave de sol (glifo de FreeSerif). Versión clara para documentos y versión oscura con esquinas redondeadas como icono de la app.
**Ficheros:** `assets/branding/simplesample_logo.svg|png` y `simplesample_icono.svg|png`.

## D-08. Arquitectura (pendiente)
**Fecha:** noviembre 2026
**Estado:** se decide en el Sprint 2. Candidata principal: la arquitectura recomendada por la documentación oficial de Flutter (MVVM con capa de interfaz —vistas y view models— y capa de datos —repositorios y servicios—, más capa de dominio solo si hace falta), comparada con la arquitectura por capas clásica del anteproyecto. El audio encajaría como un servicio de la capa de datos.

## D-09. Repositorio limpio
**Fecha:** noviembre 2026
**Decisión:** fuera del repositorio todo lo que es configuración local de cada equipo (`.idea/`, `*.iml`) y el servidor MCP de Supabase, que ya no se usa. El `.gitignore` pasa a ser el de una app Flutter en lugar del genérico de Dart.
**Motivo:** el repositorio es público y lo revisa el profesor; solo debe contener lo que hace falta para compilar, documentar y trabajar en el proyecto.
