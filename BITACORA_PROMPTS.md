# Bitácora de uso de IA — Operación Grúa: Carga Segura

**Curso:** MAT2001 · Cálculo Integral · Actividad evaluada «Diseñen con IA un juego que enseñe centros de masa»
**Fecha:** 19/11/2026 · **Juego:** https://casoham.github.io/operacion-grua/ · **Código:** https://github.com/casoham/operacion-grua

## 1. Herramientas usadas

| Herramienta | Para qué |
|---|---|
| Claude (Claude Code, modelo Sonnet 5.5) | Diseño del juego, código HTML/JS, verificación matemática, análisis de interfaz |
| Navegador integrado + consola JS | Probar el juego, simular partidas, leer estilos de Focus Town |
| Integración numérica (Simpson) y fuerza bruta en JS | Comprobar que cada resultado del juego coincide con el cálculo a mano |
| GitHub + GitHub Pages | Publicación (computadora y celular) |
| Presentación del curso (PPTX) | Fuente del problema, rúbrica y ejemplos (diap. 7 y 12) |

## 2. Prompts clave (en orden) y qué produjeron

| # | Prompt (resumen fiel) | Resultado |
|---|---|---|
| 1 | Concepto «Operación Grúa: carga segura»: poner masas en un barco, estilo de la imagen de referencia; 3 niveles (masas puntuales, figuras compuestas, región bajo una curva); plantilla de prueba y plan de desarrollo con tope a las 11:30. | `index.html` con 3 niveles y 7 etapas, `PLAN.md` con cronograma. |
| 2 | Antes de jugar, una **demostración guiada** («multiplica la masa por la distancia, suma, coloca la carga»). En el nivel 2 la **pista no debe ser la respuesta**, sino un ejemplo con otros datos y otras figuras. | Demo paso a paso por nivel; pistas con ejemplo resuelto distinto (escalón, orificio, cuña, cúpula, y = x² en [0,2]). |
| 3 | Reducir clics y mejorar UX; feedback visible; **escribir los números a mano** (no tocar); barco que zarpa o vuelca y se reinicia solo; pasar al siguiente nivel automáticamente con otro barco; poder recoger un bloque con la grúa antes de la última pieza. | Evaluación automática al colocar la última pieza, barcos distintos por etapa, recoger con la grúa, mensajes sobre la escena. |
| 4 | Situaciones de choque (iceberg, ballena, ola gigante, águila), el barco sale a la **izquierda**, mensajes menos explicativos que se quiten solos, demo que no salga sola y no quede desfasada, más feedback. | 4 peligros animados, sonidos, partículas y confeti; demo solo a pedido y siempre del nivel actual. |
| 5 | Copiar la **identidad visual de Focus Town** (muñecos, mensajes, barras), un **capitán** que «muere» si algo sale mal, y que funcione en teléfono y computadora. | Capitán chibi (5 estados, fantasma al morir), paleta y componentes de Focus Town, diseño adaptable. |
| 6 | Subir a GitHub y compartir un solo enlace para computadora y teléfono. | Repo público con GitHub Pages. |
| 7 | Analizar Focus Town con la sesión abierta (figuras, mensajes, todo lo editable) y aplicar los cambios. | `ANALISIS_FOCUSTOWN.md`; interfaz oscura, HUD en píldoras, dock inferior. |
| 8 | Esta bitácora y aplicar los cambios pendientes sin la estética de la capibara. | Este archivo y las mejoras de la sección 5. |

## 3. Verificación de la matemática (la IA no se da por buena sin comprobar)

| Caso | Cálculo a mano | Comprobado por |
|---|---|---|
| y = 4 − x² | A = 32/3, M_y = 0, M_x = 256/15 → (0, 8/5) | integración numérica; coincide con diap. 7 |
| y = x y y = x² | A = 1/6, M_y = 1/12, M_x = 1/15 → (1/2, 2/5) | integración numérica; coincide con diap. 12 |
| y = √x, [0, 4] | A = 16/3, M_y = 64/5, M_x = 4 → (12/5, 3/4) | integración numérica |
| Placa en L | A = 5 → (1,1; 1,1) | tabla de partes |
| Triángulo b=3, h=2 | A = 3 → (1; 2/3) | fórmula del centroide |
| Semicírculo r=1,5 | ȳ = 4r/(3π) ≈ 0,637 | fórmula |
| Nivel 1.1 | x̄ = (−12 + 4 − 5 + 6)/14 = −0,5 | cálculo directo |

Además se buscaron por fuerza bruta todas las soluciones de cada etapa: 2, 4, 10 y 28 arreglos válidos (ningún nivel es imposible).

## 4. Errores de la IA detectados y corregidos

| Error | Cómo se detectó | Corrección |
|---|---|---|
| Al estimar el centroide de y = √x, un primer cálculo mental dio ȳ = 1,5. | La integración numérica dio M_x/A = 4 / (16/3) = **0,75**. | Se usó 0,75 y se dejó la comprobación numérica en el juego. |
| Los contenedores soltados **no se veían** (animación de caída con signo invertido: caían desde abajo). | Prueba en el navegador: la tabla los contaba pero no se dibujaban. | Se corrigió el desplazamiento de caída. |
| Las pistas del nivel 2 **daban la respuesta**. | Revisión del equipo contra el objetivo pedagógico. | Ahora muestran un ejemplo resuelto con otra figura. |
| Los mensajes al fallar **sobreexplicaban** (tablas de momentos, consejos). | Revisión del equipo. | Mensaje de una línea que se quita solo. |
| La demo del nivel 2 quedaba abierta al volver al nivel 1. | Prueba manual del equipo. | La demo se cierra al cambiar de etapa y siempre es la del nivel actual. |
| El águila aparecía fuera de pantalla. | Captura en el navegador. | Se reubicó sobre la cabina. |
| Se usó la paleta crema de la página de inicio de Focus Town, pero la interfaz del juego es **oscura**. | Al medir los estilos de la sesión abierta. | Se rehízo con los colores reales (#3E2C20, #54402F). |

## 5. Decisiones propias del equipo sobre la IA
- La física y el cálculo los ponemos nosotros: el jugador **escribe** sus resultados.
- Las pistas no dan la respuesta.
- El estilo visual se inspira en Focus Town pero se adapta a nuestro contexto (barco, puerto, capitán).
- Se descartó la estética de la capibara por no corresponder a nuestro tema.

## 6. Limitaciones conocidas
- Los sonidos y las animaciones se probaron en el navegador de escritorio; falta revisión en un teléfono físico.
- El diseño se inspira en una referencia comercial; no se copian sus ilustraciones ni su marca.
