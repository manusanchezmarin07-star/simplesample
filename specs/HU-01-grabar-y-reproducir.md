# HU-01: grabar y reproducir un sonido (prueba de concepto)

**Sprint:** 1
**Story points:** 5
**Estado:** borrador

## Historia de usuario
Como músico aficionado, quiero grabar unos segundos con el micrófono y escucharlos al momento para comprobar que la app captura bien el sonido de mi instrumento.

## Contexto
Es la prueba de concepto del Sprint 1 y la base de toda la app. Va la primera porque el audio es la parte con más riesgo técnico: si la grabación o la latencia fallan en alguna plataforma, hay que saberlo cuanto antes.

## Criterios de aceptación
1. Dado que la app está abierta, cuando pulso grabar, entonces la app pide permiso de micrófono si no lo tiene.
2. Dado que tengo permiso, cuando pulso grabar y luego parar, entonces se guarda un archivo de audio en el dispositivo.
3. Dado que hay una grabación, cuando pulso reproducir, entonces la oigo completa.
4. Todo lo anterior funciona igual en Windows y en Android.

## Casos límite
(Por completar por Manu)

## Diseño técnico
(Por completar por Manu tras investigar record y flutter_soloud)

## Pruebas
Manuales: medir a oído la latencia al reproducir en Windows y en Android y anotarla.

## Lo que tengo que saber explicar
Qué es una frecuencia de muestreo, en qué formato se guarda la grabación y por qué, y cómo pide permisos una app en Android frente a Windows.
