# Operación Grúa: Carga Segura — Plan de desarrollo

**Meta: juego entregable a las 11:30.** Inicio del plan 10:25 → quedan ~65 min.
Archivo único `index.html` (canvas + JS, sin dependencias) → se juega abriéndolo o desde GitHub Pages.

## Cronograma

| Hora | Hito | Estado |
|---|---|---|
| 10:25–10:50 | **Plantilla v0.1**: escena (barco, grúa, mar), 3 niveles jugables, 7 etapas, retroalimentación | ✅ hecho |
| 10:50–11:05 | **Iteración 1 – sensación y diseño**: probar con el equipo, ajustar tamaños, colores, tutorial 1.1, sonidos/animación al ganar | |
| 11:05–11:15 | **Iteración 2 – pedagogía**: pedir que el jugador *escriba* su x̄ antes de zarpar (L1), pistas por nivel, mensaje de simetría en L3 | |
| 11:15–11:25 | **Verificación + entregables**: cálculos a mano (tabla abajo), bitácora de IA, capturas, guion de demo 5 min | |
| 11:25–11:30 | **Colchón**: publicar, probar el enlace, ensayar demo | |

> Regla: a las 11:15 se congela la funcionalidad. Después solo se arreglan bugs.

## Qué hay en la plantilla v0.1

| Nivel | Etapas | Mecánica | Fórmula |
|---|---|---|---|
| 1 Masas puntuales | 1.1 (1D), 1.2 (2D con apilado) | Izar contenedores con masa a columnas de la cubierta; el barco escora según x̄ | x̄ = Σmᵢxᵢ / Σm, ȳ = Σmᵢyᵢ / Σm |
| 2 Figuras compuestas | 2.1, 2.2 | Calcular el centroide de cada pieza (L, T, triángulo, semicírculo, placas con agujero = área negativa) → izarla → colocarla (se puede voltear) | x̄ = Σ(±Aᵢx̄ᵢ) / Σ(±Aᵢ) |
| 3 Región bajo curva | 3.1 y=4−x², 3.2 y=x vs y=x², 3.3 y=√x | Elegir la integral de M_y, calcular A, M_y, M_x, x̄, ȳ, y colocar la argolla: la placa **cuelga inclinada** si no está sobre x̄ | M_y=∫x(f−g)dx, M_x=∫½(f²−g²)dx |

Retroalimentación al fallar: tabla de momentos izquierda/derecha respecto al objetivo, qué lado “jala más”, y si el centro queda muy alto/bajo.

## Verificación matemática (rúbrica: ≥3 casos a mano)

El juego ya se comprobó contra integración numérica (Simpson) y fuerza bruta:

| Caso | A | M_y | M_x | (x̄, ȳ) |
|---|---|---|---|---|
| 3.1  y = 4 − x² | 32/3 | 0 | 256/15 | (0, 8/5) — coincide con la diapositiva 7 |
| 3.2  y=x, y=x² | 1/6 | 1/12 | 1/15 | (1/2, 2/5) — coincide con la diapositiva 12 |
| 3.3  y = √x, [0,4] | 16/3 | 64/5 | 4 | (12/5, 3/4) |
| 2.1 L | 5 | — | — | (1,1; 1,1) |
| 2.1 Triángulo b=3, h=2 | 3 | — | — | (1; 2/3) |
| 2.2 Semicírculo r=1,5 | 9π/8 ≈ 3,534 | — | — | (1,5; 4r/3π ≈ 0,637) |
| 1.1 | masas 4 en −3, 2 en 2, 5 en −1, 3 en 2 | | | x̄ = −7/14 = −0,5 |

Soluciones existentes (para que ningún nivel sea imposible): 1.1 → 2, 1.2 → 4, 2.1 → 10, 2.2 → 28 arreglos válidos.

## Backlog para iterar (priorizado)

1. **Tutorial 1.1**: flecha animada y texto de la fórmula en la primera carga.
2. **Predicción**: en L1, casilla “mi x̄ = ___” antes de *Zarpar* (evita ganar solo por prueba y error).
3. **Efectos**: confeti/olas al ganar, sonido de cadena y golpe de contenedor, pantalla final.
4. **Más variedad en L1**: etapa “añade una masa” (cualquier masa libre que el jugador elija).
5. **L3**: opción de visualizar las franjas dx sobre la placa; mostrar el eje de simetría cuando exista.
6. **Móvil**: arrastrar el gancho con el dedo (hoy el toque suelta de inmediato).
7. **Informe** (2–3 págs.) + **bitácora de IA**: guardar prompts clave y errores de la IA corregidos (p. ej. ȳ de √x: la IA dio 1,5, la integral da 0,75).

## Reparto sugerido (3 integrantes)

- **A – Diseño/arte**: estilo del barco y contenedores, colores, pantalla de inicio y final.
- **B – Matemática/pedagogía**: validar cálculos a mano, redactar pistas y mensajes de error, informe.
- **C – Código/QA**: iterar `index.html`, probar en celular, publicar enlace, bitácora de IA.
