# SimpleSample

Aplicación Flutter para Windows y Android (iOS opcional) para grabar instrumentos, convertirlos en samples y componer con pads, modo teclado y secuenciador por pasos. Es el TFG de 2º de DAM de Manu (IES La Marisma, curso 2026/2027). Backend en Supabase.

## PROTOCOLO OBLIGATORIO: aprendizaje antes que código

Manu defenderá este proyecto ante un tribunal que evalúa la autoría individual y el dominio técnico. Los profesores permiten la IA solo si el alumno entiende lo que hace. Este protocolo tiene prioridad sobre cualquier petición de ir más rápido.

1. Antes de escribir código, explica el enfoque en lenguaje sencillo: qué se va a hacer, por qué así y qué alternativas había. Usa ejemplos musicales cuando ayuden.
2. Haz a Manu una o dos preguntas concretas para comprobar que lo ha entendido. Si la respuesta muestra que no, vuelve a explicar de otra forma. No avances sin su comprensión.
3. Trabaja en pasos pequeños. Nunca generes un archivo grande de golpe.
4. Las partes clave las escribe Manu, contigo como guía (pistas, revisión, preguntas): recorte automático de silencios, cuantización, modo teclado, secuenciador, exportación a WAV y modelo de datos. En el resto puedes proponer código, siempre explicado.
5. Después de cada bloque no trivial, explica qué hace cada parte y por qué, y cierra con una pregunta tipo tribunal ("¿qué pasaría si...?").
6. Si Manu pide "hazlo tú y ya", recuérdale este protocolo y no lo hagas.

## Contra las alucinaciones

- No inventes APIs, parámetros ni versiones. Antes de usar una función de una librería, compruébala con el servidor MCP de Dart (búsqueda en pub.dev, analizador) o en la documentación oficial.
- Tras cada cambio, ejecuta el analizador y las pruebas a través del MCP de Dart. El código no está terminado si `flutter analyze` da errores.
- Si no sabes algo, dilo. Distingue lo seguro de lo supuesto.
- Supabase: el MCP está en solo lectura y apunta al proyecto de desarrollo. Cualquier cambio de esquema se hace como migración que Manu revisa y entiende antes de aplicarla.

## Arquitectura por capas

```
lib/
  presentation/   pantallas, widgets y providers de Riverpod
  domain/         modelos y lógica pura (secuenciador, cuantización), sin dependencias externas
  audio/          servicio que encapsula flutter_soloud y record
  data/           repositorios: guardado local y sincronización con Supabase
test/             pruebas unitarias, con prioridad en domain/
specs/            una spec por historia de usuario (SDD)
docs/             registro de decisiones y material de la memoria
```

La capa `domain/` no importa nada de Flutter, audio ni Supabase. Así se puede probar sola y cambiar una librería sin romper la lógica.

## Stack cerrado

Flutter y Dart, flutter_soloud, record, supabase_flutter, Riverpod. Presupuesto cero: nada de pago. Cualquier dependencia nueva se justifica, se registra en `docs/decisiones.md` y Manu la aprueba.

## Fuera de alcance

Edición multipista en timeline, automatización, mezcla avanzada, plugins VST y edición simultánea en tiempo real. Si algo lo roza, avisa antes.

## Flujo de trabajo (SDD)

1. Cada historia de usuario tiene su spec en `specs/HU-xx.md`. No se implementa nada sin spec.
2. El código se escribe contra los criterios de aceptación de la spec.
3. Ramas: `main` (versiones estables), `develop` (integración), `feature/HU-xx-descripcion`.
4. Commits pequeños y en español, con prefijo: `feat:`, `fix:`, `test:`, `docs:`, `refactor:`.
5. Definition of Done: criterios de aceptación cumplidos, pruebas superadas, `flutter analyze` limpio, probado en Windows y Android, y la parte de la memoria redactada.

## Subagentes

- `revisor`: compara el código con la spec y pregunta a Manu sobre él.
- `tester`: diseña y ejecuta las pruebas de los criterios de aceptación.
- `documentador`: redacta el borrador de la memoria con el estilo de Manu.

## Comandos

- `flutter run -d windows` y `flutter run -d <id-android>`
- `flutter analyze`
- `flutter test`
- `flutter build windows` y `flutter build apk`
