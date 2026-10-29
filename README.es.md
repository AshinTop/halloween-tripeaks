[English](README.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md) | [Português (Brasil)](README.pt-BR.md) | [日本語](README.ja.md)

# 🎃 Trick-or-Treat TriPeaks — Solitario de Halloween con puentes lunares

**Tres torres, un camino de caramelos y un atajo bajo la luna.** Trick-or-Treat TriPeaks es un solitario de Halloween creado para [FreeCell Game](https://freecell-game.top/). Encadena cartas de valor superior o inferior, despeja los picos y gana un puente lunar para continuar una secuencia difícil. Gatos negros, brujas y calabazas ilustran las figuras originales de la baraja.

**[Jugar ahora](https://halloween-tripeaks.crazy3d.org/)** · [Colección de Halloween](https://github.com/AshinTop/halloween-games) · [Guía de integración](EMBEDDING.md) · [Notas de diseño](DESIGN.md)

**Idiomas de la documentación:** English, 简体中文, Español, Português (Brasil), 日本語. **Interfaz del juego:** solo inglés y chino simplificado. Los otros idiomas del README no implican una traducción de los menús del juego.

![Solitario TriPeaks de Halloween con tres picos, mazo de robo, descarte e indicador de puente lunar](docs/images/gameplay.jpg)

## Dentro de la baraja 👻

- **52 cartas completas:** 28 en los picos, 23 en el mazo y una en el descarte inicial.
- **Ocho partidas Journey**, cada una con una solución verificada sin robar cartas.
- Partidas Classic reproducibles y un reto diario basado en UTC.
- Puentes lunares limitados, deshacer, pistas legales, estrellas, guardado local y sonido sintetizado opcional.

## Cómo despejar los picos

Retira una carta descubierta cuyo valor sea uno mayor o menor que el descarte. Esa carta se convierte en el nuevo descarte. No importan los palos ni los colores. El As conecta con el Rey: **K–A–2** es válido. Una carta sigue cubierta mientras quede alguna carta apoyada sobre ella. Retira las 28 cartas de los picos para ganar.

Puedes robar cuando quieras. Robar reinicia la cadena. Las 23 cartas del mazo se usan una sola vez, sin volver a repartir. Solo pierdes cuando el mazo está vacío, ninguna carta descubierta encaja y no queda un puente lunar.

Cinco retiradas normales consecutivas permiten ganar un **puente lunar**. Puedes guardar uno y conseguir como máximo dos por partida. Selecciona el puente y luego cualquier carta descubierta para ignorar su valor. Las cartas cubiertas siguen bloqueadas. El puente reinicia la cadena; vuelve a pulsar su botón para cancelar. Deshacer restaura cartas, mazo, puntos y magia.

Una retirada normal suma 10 puntos más la cadena actual × 5. Quitar la carta superior de un pico añade 50. Un puente da los 10 puntos básicos y el posible premio del pico. Ganar sin robar otorga tres estrellas; con cinco robos como máximo, dos; las demás victorias, una. No hay cronómetro.

## Controles

| Acción | Entrada |
|---|---|
| Retirar una carta | Clic / toque, o Tab y Enter |
| Robar | Mazo; Espacio fuera de botones o campos |
| Usar magia | Puente lunar y después carta descubierta |
| Deshacer | Z o botón |
| Mostrar una jugada legal | Spot a Move |
| Repetir o cambiar modo | Reinicio y selector |

**Spot a Move indica un paso legal, no resuelve toda la partida.** Una carta disponible no garantiza una victoria posterior.

## Elegir y compartir

[Journey 1](https://halloween-tripeaks.crazy3d.org/?level=1) abre la campaña. [Classic con semilla 12345](https://halloween-tripeaks.crazy3d.org/?mode=classic&seed=12345) comparte una mezcla concreta. Elegir Classic otra vez genera una nueva; reiniciar repite la actual. Un [reto diario fechado](https://halloween-tripeaks.crazy3d.org/?mode=daily&date=2026-10-31) conserva el día UTC exacto.

La partida actual, mejores resultados y preferencias se guardan localmente. Los parámetros explícitos del enlace abren la partida solicitada. El historial de deshacer dura la sesión de la página.

## Preguntas frecuentes

**¿Todas las partidas tienen solución?** Las ocho Journey tienen soluciones comprobadas. Classic y Daily no garantizan que una mezcla sea resoluble.

**¿El puente quita cartas cubiertas?** No. Solo cambia la regla del valor, no la de cobertura.

**¿Puedo reciclar el mazo?** No. Elegir cuándo robar, alargar cadenas y administrar puentes forma parte de la estrategia.

## Imágenes y vídeo

![TriPeaks compacto con esquinas de cartas legibles, descarte y controles de puente lunar](docs/images/mobile.jpg)

Interfaz real capturada en un iframe compacto del navegador. Ilustra la distribución de los controles; no es una prueba de rendimiento en un teléfono físico.

[Ver la introducción de 24 segundos](https://halloween-tripeaks.crazy3d.org/intro.html) · [Descargar el MP4 con subtítulos](docs/media/intro.mp4). Este vídeo silencioso está montado con capturas reales del juego, no con una partida grabada de forma continua. Las imágenes reflejan la interfaz del momento de la captura y pueden ser anteriores a mejoras visuales posteriores.

## Añádelo a tu sitio

```html
<iframe src="https://halloween-tripeaks.crazy3d.org/"
  title="Trick-or-Treat TriPeaks"
  style="display:block;width:100%;height:654px;border:0"
  allow="fullscreen" allowfullscreen></iframe>
```

Las cartas se adaptan al espacio disponible en escritorio, vertical estrecho y horizontal bajo. Asigna una altura real al iframe y deja espacio para leer las esquinas. El juego no accede al documento padre ni necesita micrófono, cámara o bloqueo del puntero.

La versión en línea se publica en Cloudflare desde este repositorio de GitHub. Asigna una altura real al iframe y deja espacio para la barra del sitio anfitrión. El sitio puede ofrecer pantalla completa. Consulta [EMBEDDING.md](EMBEDDING.md) para los detalles.

## Ejecutar y comprobar en local

```sh
python3 -m http.server 4173
```

Sirve la raíz del repositorio y abre [http://localhost:4173/](http://localhost:4173/). Es un juego estático, sin compilación ni instalación de dependencias. Usa HTTP(S): abrirlo mediante `file://` puede bloquear los módulos JavaScript. Las pruebas requieren Node.js.

```sh
npm test
```

Las **12 pruebas** cubren las ocho soluciones Journey, la baraja sin duplicados, coberturas, conexión As/Rey, mazo, límites de puentes, condiciones exactas de derrota, mezclas reproducibles, fechas y validación del guardado.

El código del juego no necesita cuentas, API remotas, SDK publicitarios ni una CDN de recursos externos. Los registros se guardan en el navegador, sin sincronización en la nube. Cloudflare puede añadir scripts de alojamiento y registros de solicitudes. El sonido sintetizado opcional respeta los permisos del navegador.

## Más aventuras a la luz de la luna 🍬

- [Haunted FreeCell](https://halloween-freecell.crazy3d.org/) · [Código](https://github.com/AshinTop/halloween-freecell) — FreeCell clásico y finales Lantern Rescue.
- [Pumpkin Shift](https://halloween-pumpkin-shift.crazy3d.org/) · [Código](https://github.com/AshinTop/halloween-pumpkin-shift) — Puzles deslizantes con Moon Glides.
- [Witch’s Candy Blocks](https://halloween-block-blast.crazy3d.org/) · [Código](https://github.com/AshinTop/halloween-block-blast) — Coloca bloques de caramelo en un tablero 8×8.
- [Pumpkin 2048](https://halloween-2048.crazy3d.org/) · [Código](https://github.com/AshinTop/halloween-2048) — Fusiones clásicas y Lantern Trials.

## Créditos y apoyo

Creado para **Midnight Candy Club de AshinTop** mediante colaboración con IA dirigida por personas en diseño, programación, documentación, pruebas y revisión. Las ilustraciones originales y los sonidos sintetizados se hicieron para este proyecto. Consulta las [notas de diseño](DESIGN.md).

¿Te gustó esta pequeña aventura? **[Dale una estrella a Trick-or-Treat TriPeaks en GitHub](https://github.com/AshinTop/halloween-tripeaks)** para encontrarlo después y seguir las novedades. Al informar de un problema, incluye nivel o modo, navegador, tamaño de ventana y pasos para reproducirlo. Descubre la [colección completa de Halloween](https://github.com/AshinTop/halloween-games).
