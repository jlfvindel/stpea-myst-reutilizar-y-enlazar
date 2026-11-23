---
title: 'Proyecto 3: reutilizar y enlazar'
short_title: Inicio
label: inicio
---

Este proyecto propone una forma de trabajar para quien prepara materiales: mantener un **repositorio** de piezas (definiciones, fórmulas, figuras, ejercicios, avisos) y montar con ellas distintas **presentaciones** para el alumnado, sin copiar ni repetir nada. Las piezas tratan del tiro parabólico, el mismo tema del proyecto 2.

:::{note} Sobre la elaboración de este material
:class: dropdown
Este proyecto lo ha preparado José Luis Fernández Vindel en colaboración con un asistente de inteligencia artificial (Claude, de Anthropic). La estructura, los textos y los ejemplos se han elaborado en diálogo con el asistente; el autor ha decidido el enfoque, ha revisado el resultado y responde de su contenido. Los ejemplos se han comprobado con MyST 1.13.0.
:::

Puedes {download}`descargar la fuente completa del proyecto <descargas/reutilizar-y-enlazar.zip>` para ejecutarlo y modificarlo en tu ordenador. También está en el botón de descarga, arriba a la derecha de cada página.

## Cómo está organizado

Guía
: Explica, para el autor, cómo está hecho todo: [el repositorio](#repositorio), [las formas de reutilizar](#reutilizar) y cómo queda la numeración, [los enunciados matemáticos](#demostraciones), [el glosario, el índice y la bibliografía](#glosario-indice-bibliografia), y [las configuraciones](#configuraciones).

Presentaciones
: Lo que leería el alumnado: un [tema](#tema) completo y una [ficha de repaso](#repaso), hechos con las mismas piezas.

Anexos
: Los [resultados](#anexo-resultados), que forman parte del repositorio pero se muestran (y se numeran), y el [índice alfabético](#indice).

El resto del repositorio está en páginas **ocultas**: no aparecen en el menú, pero sus piezas se ven en las ventanas emergentes de las citas y dentro de las presentaciones.

## Tres configuraciones

| Fichero | Se usa con | Qué produce |
|---|---|---|
| `myst.yml` | `myst start` | La guía completa: guía, presentaciones y anexos |
| `myst-alumnado.yml` | `myst --config myst-alumnado.yml start` | Solo las presentaciones y los anexos. Su índice web y el de su PDF son ficheros externos, y distintos entre sí |
| `myst-enlazado.yml` | `myst --config myst-enlazado.yml start` | La guía, con una página más que cita proyectos MyST externos y Wikipedia |

Las tres heredan lo común de `config/comun.yml`. La página [](#configuraciones) las explica.

:::{note} Los cuatro proyectos
1. Usar MyST y maquetar.
2. Recursos multimedia.
3. **Reutilizar y enlazar** (este).
4. Documentos ejecutables con cuadernos Jupyter.
:::
