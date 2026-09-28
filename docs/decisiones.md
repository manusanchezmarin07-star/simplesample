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

## D-03. Supabase como backend
**Fecha:** septiembre 2026
**Decisión:** Supabase (PostgreSQL, Auth y Storage).
**Motivo:** base de datos relacional, autenticación con correo y Google, almacenamiento para los samples, SDK oficial para Flutter y plan gratuito suficiente.
**Descartada:** Firebase, que exige el plan de pago por uso para usar su almacenamiento en proyectos nuevos.
**A tener en cuenta:** el plan gratuito pausa el proyecto tras una semana sin actividad; revisarlo antes de cada demo.

## D-04. Audio
**Fecha:** septiembre 2026
**Decisión:** flutter_soloud para reproducción y efectos, record para la grabación.
**Motivo:** baja latencia, control de la velocidad de reproducción (base del modo teclado) y filtros incluidos.
**Pendiente de validar:** latencia real en Android en la prueba de concepto del Sprint 1.

## D-05. Presupuesto cero
**Fecha:** septiembre 2026
**Decisión:** todas las herramientas gratuitas o en plan gratuito. Distribución por GitHub Releases, sin Google Play ni App Store.
