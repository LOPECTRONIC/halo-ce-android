# Android: sensibilidad de mando, pantalla y ratón (2026-10-11)

**Cómo entrar:** Halo Android > Porting options > Aim sensitivity.

| Ajuste | Nuevo máximo | Qué modifica |
| --- | --- | --- |
| Gamepad | nivel 30 | Velocidad del joystick derecho al apuntar. Los antiguos niveles 1-10 conservan la misma velocidad; 11-30 prolongan la curva del juego. |
| Touch screen | 20x | Movimiento de la cámara al arrastrar el dedo. Antes el límite era 4x. |
| Mouse | 30x | Sensibilidad real de movimiento relativo del ratón, en horizontal y vertical. |

El mando y el ratón empiezan en **game setting** (extremo izquierdo de sus barras). En esa posición siguen respetando la configuración del juego que el usuario ya tenía. Si mueves cualquiera de sus barras a la derecha, la nueva configuración de Porting options pasa a prevalecer para ese dispositivo. Si vuelves al extremo izquierdo, se desactiva la modificación adicional y se recupera el ajuste guardado en el juego.

El **nivel 30 del mando no significa multiplicar por treinta** la velocidad original: se prolongan las velocidades del Halo original, que pasaban de 80 a 260 grados/segundo en horizontal entre los niveles 1 y 10. El nivel 30 usa 660 grados/segundo de velocidad horizontal base. El ratón, en cambio, sí usa un multiplicador directo de su desplazamiento relativo; la pantalla también aplica su factor directamente a los movimientos táctiles.

La pantalla táctil mantiene su valor anterior guardado, incluidos los diseños exportados en `.halolayout`; ahora acepta 0.25x a 20x. Las opciones **Gyroscope sensitivity** (0.25x-4x), tamaños de controles y FOV no cambian. Los ajustes de mando y ratón se guardan independientemente en las preferencias Android de la aplicación; los diseños `.halolayout` siguen exportando exclusivamente los ajustes de pantalla y demás opciones de su formato existente.

Además, en el menú habitual de ajustes de jugador se amplía **Controller > Look sensitivity** de 1-10 a 1-30. El menú habitual **Mouse settings** también incluye valores hasta 30x en horizontal y vertical. Son accesibles con teclado y ratón o con el mando. Si se activa el valor de ratón desde Porting options, su valor único se aplica por igual a ambos ejes y reemplaza temporalmente la configuración horizontal/vertical habitual. Para recuperar ajustes independientes de los ejes vuelve a situar **Mouse** en **game setting** dentro de Porting options.

## Comprobación en el teléfono

1. Empieza con Gamepad y Mouse en **game setting**, para comprobar que funcionan exactamente como antes.
2. En **Aim sensitivity**, mueve Touch screen hacia 20x. Apunta arrastrando el dedo y comprueba que el giro es más rápido; cierra y abre la app para verificar que se guarda.
3. Selecciona, por ejemplo, Gamepad nivel 15. Prueba el joystick derecho y luego nivel 30. Prueba con el perfil de mando que ya utilizabas.
4. Conecta tu ratón USB o Bluetooth; selecciona Mouse 5x, después 30x. Prueba ambos ejes sin tocar la pantalla. Comprueba que la captura de ratón sigue funcionando.
5. Devuelve Gamepad y Mouse al extremo izquierdo y comprueba que reaparecen los ajustes originales del juego.
6. Exporta e importa un diseño táctil con sensibilidad 20x, y verifica que el valor se recupera.

**Compilación:** el proyecto incluye `.github/workflows/build.yml`. En GitHub, después de subir estos cambios al código de la rama principal, accede a Actions > Android build > Run workflow o espera a que termine la compilación automática. Descarga los artefactos de depuración o release del run completado. No se ha generado un APK en este entorno; hay que comprobar el APK compilado en hardware Android real.
