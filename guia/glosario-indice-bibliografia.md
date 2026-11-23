---
title: Glosario, índice y bibliografía
short_title: Glosario, índice, citas
label: glosario-indice-bibliografia
---

Tres herramientas clásicas de un libro, que en MyST se construyen solas a partir de marcas en el texto.

## Glosario

El glosario es una lista de definiciones dentro de la directiva `glossary`. En este proyecto vive en una página oculta, `repositorio/glosario.md`:

```markdown
:::{glossary}
Proyectil
: Objeto que se mueve solo bajo la acción de la gravedad tras un impulso inicial.

Ángulos complementarios
: Dos ángulos que suman $90^\circ$, como $30^\circ$ y $60^\circ$.
:::
```

Desde cualquier página, el rol `term` enlaza un término con su definición, que aparece en una ventana emergente:

```markdown
Un {term}`proyectil` lanzado con {term}`ángulos complementarios`…
```

Resultado:

Un {term}`proyectil` lanzado con {term}`ángulos complementarios`…

Si el texto visible no coincide con el término (un plural, otra forma), se escriben los dos: `` {term}`proyectiles <proyectil>` `` muestra «{term}`proyectiles <proyectil>`» y enlaza con «Proyectil». Las mayúsculas no importan.

## Índice alfabético

El índice reúne las entradas marcadas en todas las páginas con el rol `index`. La palabra marcada se sigue viendo normalmente en el texto:

```markdown
{index}`Galileo` fue el primero en describir este movimiento…

El {index}`alcance <single: Alcance; fórmula>` y la altura máxima…
```

- En la primera línea, «Galileo» es a la vez el texto y la entrada del índice.
- En la segunda, el texto visible es «alcance», y lo que va entre `< >` dice qué entrada crear: `single: Alcance; fórmula` crea la subentrada «fórmula» dentro de «Alcance».

Los dos ejemplos están en el [tema](#tema). Los términos del glosario entran en el índice automáticamente. El índice se muestra con la directiva `show-index`, en una página propia: el [índice alfabético](#indice) de este proyecto.

:::{warning} Una entrada, una forma de escribirla
«Alcance» y «alcance» son para MyST dos entradas distintas, y avisa de ello. Como los términos del glosario empiezan por mayúscula, conviene escribir igual las entradas del índice.
:::

## Bibliografía

Las referencias bibliográficas se guardan en un fichero BibTeX, `referencias.bib`, que se declara en la configuración (`bibliography`). Cada referencia tiene una clave:

```text
@book{halliday2014,
  author    = {Halliday, David and Resnick, Robert and Walker, Jearl},
  title     = {Fundamentals of Physics},
  edition   = {10},
  publisher = {Wiley},
  year      = {2014}
}
```

y se cita con ella de dos formas:

```markdown
Según {cite:t}`halliday2014`, … reduce la carga cognitiva {cite:p}`sweller1988`.
```

Resultado:

Según {cite:t}`halliday2014`, … reduce la carga cognitiva {cite:p}`sweller1988`.

`cite:t` cita en el texto, con el autor fuera del paréntesis; `cite:p` cita entre paréntesis. La forma breve `[@sweller1988]` equivale a `cite:p`. Al final de cada página, MyST añade la lista de las referencias citadas en ella, como la de esta página. El encabezado de esa lista («References») sale en inglés.

:::{tip} Para explorar más
- Los gestores bibliográficos (Zotero, Mendeley, JabRef…) exportan la biblioteca a BibTeX, de modo que el `.bib` no hace falta escribirlo a mano.
- Glosarios: <https://mystmd.org/guide/glossaries-and-terms>. Citas: <https://mystmd.org/guide/citations>.
:::
