---
title: Organizar un repositorio de fragmentos
short_title: El repositorio
label: repositorio
---

La idea de este proyecto es sencilla: **cada pieza de contenido se escribe una sola vez**, en un repositorio, y las páginas que lee el alumnado (las *presentaciones*) se montan citando e incrustando esas piezas. Una definición, una fórmula o una figura corregida en el repositorio queda corregida en todas las presentaciones que la usan.

Este proyecto tiene dos presentaciones hechas con las mismas piezas: un [tema](#tema) completo y una [ficha de repaso](#repaso).

## Tres lugares para guardar piezas

MyST ofrece tres maneras de guardar contenido reutilizable, y se comportan de forma distinta:

| | Página oculta | Página visible (anexo) | Fichero para `include` |
|---|---|---|---|
| En este proyecto | `repositorio/` | `anexos/resultados.md` | `fragmentos/` |
| ¿Está en el índice? | Sí, con `hidden: true` | Sí | No |
| ¿Sale en el menú? | No | Sí | No |
| ¿Se puede citar e incrustar? | Sí | Sí | Solo si está incluido en alguna página |
| ¿Se numeran sus elementos? | **No** | Sí, en la página | Sí, en la página que lo incluye |

Página oculta
: Es una página normal que el índice marca con `hidden: true`. MyST la procesa entera: sus elementos etiquetados se pueden citar e incrustar desde cualquier página, y sus ventanas emergentes funcionan. Lo que no hace es numerarlos. Sirve para definiciones, figuras, fichas y el glosario.

Página visible
: Como el [anexo de resultados](#anexo-resultados). Sus elementos llevan número, y al citarlos o incrustarlos en otra página conservan ese número. Sirve para lo que se quiere referenciar con número: proposiciones, ecuaciones.

Fichero para `include`
: No es una página: no está en el índice y MyST no lo procesa por sí solo. Cuando una página lo incluye, su contenido pasa a formar parte de ella, como si estuviera escrito allí. Sirve para bloques que se repiten tal cual: un aviso de unidades, unas instrucciones de entrega, un ejercicio.

:::{warning} Un fichero con etiquetas se incluye una sola vez
Si un fichero con etiquetas se incluye en dos páginas, la misma etiqueta queda definida dos veces. MyST avisa (`Duplicate identifier`), y las citas a esa etiqueta llevan a una sola de las dos. Por eso, en este proyecto, `fragmentos/unidades.md` no tiene etiquetas y se incluye en las dos presentaciones, mientras que `fragmentos/ejercicio-alcance.md` sí las tiene y solo se incluye en el tema.
:::

## La estructura de este proyecto

```text
reutilizar-y-enlazar/
├── myst.yml, myst-alumnado.yml, myst-enlazado.yml
├── config/comun.yml          ← configuración compartida
├── tocs/                     ← índices externos
├── referencias.bib           ← bibliografía
├── repositorio/              ← páginas ocultas
│   ├── conceptos.md          (definiciones y fichas)
│   ├── figuras.md
│   └── glosario.md
├── anexos/
│   ├── resultados.md         ← repositorio visible y numerado
│   └── indice.md
├── fragmentos/               ← solo para include
│   ├── unidades.md
│   └── ejercicio-alcance.md
├── presentaciones/
│   ├── tema.md
│   └── repaso.md
└── guia/                     ← estas páginas
```

## Etiquetas con prefijo

En un repositorio, las etiquetas son el catálogo: con ellas se encuentra cada pieza. Conviene que digan qué tipo de pieza es y de qué trata:

| Prefijo | Pieza | Ejemplo |
|---|---|---|
| `def-` | Definición | `def-alcance` |
| `prop-`, `cor-`, `dem-` | Proposición, corolario, demostración | `prop-45` |
| `ejemplo-` | Ejemplo | `ejemplo-20` |
| `eq-` | Ecuación | `eq-alcance` |
| `fig-` | Figura | `fig-trayectorias` |
| `ficha-` | Apartado reutilizable | `ficha-componentes` |
| `ej-` | Ejercicio | `ej-alcance` |

:::{tip} Para explorar más
- Abre `presentaciones/tema.md` en un editor: verás que apenas tiene texto propio. Casi todo son directivas `embed` e `include`.
- Prueba a cambiar una palabra de `def-alcance` en `repositorio/conceptos.md` y mira cómo cambia a la vez en el tema y en las ventanas emergentes de todas las citas.
:::
