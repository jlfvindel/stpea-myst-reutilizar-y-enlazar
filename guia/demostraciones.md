---
title: Definiciones, proposiciones y demostraciones
short_title: Enunciados
label: demostraciones
---

Para el contenido con estructura matemática, MyST tiene una familia de directivas que empiezan por `prf:` (de *proof*). Cada una produce un recuadro con su tipo, su número y, opcionalmente, un título. Las de este proyecto están en el [repositorio de conceptos](#def-alcance) y en el [anexo de resultados](#anexo-resultados).

## Los tipos disponibles

| Directiva | Para… |
|---|---|
| `prf:definition` | una definición |
| `prf:axiom`, `prf:assumption` | un punto de partida que no se demuestra |
| `prf:theorem`, `prf:proposition`, `prf:lemma` | un resultado, de más a menos importante |
| `prf:corollary` | una consecuencia inmediata de otro resultado |
| `prf:proof` | la demostración del enunciado anterior |
| `prf:example`, `prf:remark`, `prf:observation` | un ejemplo, una observación |
| `prf:conjecture`, `prf:criterion`, `prf:property`, `prf:algorithm` | otros enunciados |

Aunque proceden de las matemáticas, sirven para cualquier materia: una norma, un criterio de evaluación o un procedimiento técnico pueden escribirse igual.

## Un enunciado y su demostración

```markdown
:::{prf:proposition} Tiempo hasta la altura máxima
:label: prop-subida

El proyectil alcanza su altura máxima en la mitad del tiempo de vuelo.
:::

:::{prf:proof}
:class: dropdown

En el punto más alto, la velocidad vertical se anula:
$v_0\sin\theta - g t = 0$, de donde $t = v_0\sin\theta / g$,
que es la mitad del tiempo de vuelo [](#eq-tiempo).
:::
```

Resultado:

:::{prf:proposition} Tiempo hasta la altura máxima
:label: prop-subida

El proyectil alcanza su altura máxima en la mitad del tiempo de vuelo.
:::

:::{prf:proof}
:class: dropdown

En el punto más alto, la velocidad vertical se anula: $v_0\sin\theta - g t = 0$, de donde $t = v_0\sin\theta / g$, que es la mitad del tiempo de vuelo [](#eq-tiempo).
:::

- El texto tras el nombre de la directiva es el **título**, que aparece entre paréntesis junto al tipo y el número.
- `:class: dropdown` pliega el recuadro, algo útil para que el alumnado intente la demostración antes de leerla.
- La demostración también se numera («Proof 1»), con su propia cuenta. Si no se quiere, se añade la opción `:nonumber:`.

## La numeración

Cada tipo se numera por separado y por página: en esta página, la proposición anterior es la proposición 1, igual que la del anexo es la proposición 1 del anexo. Al citarlas, [](#prop-subida) y [](#prop-45) muestran el mismo texto, aunque el enlace y la ventana emergente llevan a cada una.

:::{warning} Números repetidos entre páginas
Como cada página empieza a contar desde 1, dos citas iguales pueden llevar a elementos distintos. Si un material cita resultados de varias páginas, conviene reunirlos en una sola página visible, como el anexo de este proyecto, o citarlos con texto propio: «la [proposición del ángulo de $45^\circ$](#prop-45)».
:::

Para que un enunciado o una demostración no lleven número, se añade la opción `:nonumber:`. Los enunciados de una [página oculta](#repositorio) tampoco se numeran: así son las definiciones de este proyecto.

:::{tip} Para explorar más
- Directivas `prf` en la guía de MyST: <https://mystmd.org/guide/proofs-and-theorems>.
- Abre `anexos/resultados.md` para ver una proposición, su demostración y un corolario que cita a ambas.
:::
