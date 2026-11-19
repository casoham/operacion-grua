# Análisis de Focus Town → qué aplicamos en «Operación Grúa»

Fuentes: variables de diseño y estilos calculados de la página pública y de la sesión abierta (solo interfaz, sin datos de cuenta).

## Identidad visual
| Elemento | Focus Town | En nuestro juego |
|---|---|---|
| Tipografía | Fredoka 500/600/700 (redondeada) | Fredoka |
| Paneles | `#3E2C20` café oscuro, borde `#6E5544`, radio 20 px | `.panel`, modales |
| HUD / dock | `#54402F`, borde `#140C07` 1,6 px, **labio sólido 0 4px 0** | píldoras superiores y dock inferior |
| Texto | crema `#FBEFD9`; secundario `#CBBBA5`; títulos dorados `#F9D79D` | igual |
| Botón principal | azul `#78ADFD`, borde `#2F67C9`, brillo interior y labio | `.btn` |
| Botón secundario | café `#54402F` con labio negro | `.btn.ghost`, chips |
| Éxito / peligro | `#4A7C59` / `#C6410D` | mensajes |
| Insignias | círculo rojo `#FF3B30` | pendiente |

## Navegación y mensajes
- **HUD superior en píldoras** («Estás en · Mi casa», monedas, racha) → «Estás en · Nivel 1 · 1.1» y ⭐ etapas completadas.
- **Dock inferior** con icono grande + etiqueta corta, el icono rebota al pasar (`cubic-bezier(.34,1.56,.64,1)`) → Demo · Sonido · Reiniciar.
- **Hojas laterales** que se deslizan con filas redondeadas → modales de demo y pistas.
- **Mensajes**: píldora con labio, entran con rebote y se van solos → `setFB`.
- Poco texto: iconos y etiquetas de 1–2 palabras.

## Animaciones disponibles en su CSS (para próximas iteraciones)
`ft-confetti`, `ft-breathe`, `ft-shine`, `ft-sheet-reveal`, `ft-pin-drift`, `ft-live-dot-breathe`, `ft-skel-shimmer`, `ft-snow`. Curvas: `(.34,1.56,.64,1)` rebote, `(.22,1,.36,1)` suave.

## Personajes
Muñecos 3D chibi: cabeza grande, anteojos redondos, gorra, ojos grandes. Su mascota es una capibara. → Capitán chibi (gorra, anteojos, chaqueta) con 5 estados: normal, preocupado, pánico, festejo, muerto (fantasma con aureola).

## Ideas pendientes
1. Capibara como segundo tripulante que reacciona al capitán.
2. Insignias rojas en las etapas nuevas.
3. Iconos ilustrados en vez de emojis.
4. Confeti `ft-confetti` con tonos cálidos al ganar.
5. Barra de progreso por nivel con relleno `ft-fill`.
