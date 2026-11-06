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

## D-06. Estrategia de ramas
**Fecha:** noviembre 2026
**Decisión:** Git Flow simplificado.
- `main`: solo la versión final publicada. No se trabaja directamente en ella.
- `develop`: rama de integración y rama por defecto del repositorio; todo llega aquí mediante pull request.
- `feature/<nº-issue>-<descripcion>`: una rama corta por historia de usuario del tablero Kanban, creada desde develop y fusionada en develop. Igual para `fix/...`, `docs/...` y `chore/...`.
- Al cerrar cada sprint, tag anotado en develop: `v0.1.0-sprint1`, `v0.2.0-sprint2`...
**Motivo:** ramas cortas, fusiones pequeñas y trazabilidad directa con las historias del Kanban.
**Descartada:** una rama por sprint, porque acumula semanas de cambios sin integrar y las fusiones se vuelven grandes y difíciles de depurar.
**A tener en cuenta:** el repositorio es público desde noviembre de 2026, así que el plan gratuito ya permite proteger `main` con una regla de rama. Mientras no se configure, la norma de no tocar `main` es de disciplina.

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
