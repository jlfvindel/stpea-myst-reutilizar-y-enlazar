---
title: Enlazar con proyectos externos
short_title: Proyectos externos
label: enlazar-proyectos
---

Esta página solo existe en la configuración `myst-enlazado.yml`. Muestra cómo citar contenido que está **fuera del proyecto** con la misma comodidad que el propio: con texto automático y con ventana emergente. La reutilización deja así de limitarse al propio repositorio.

## Qué se puede citar

Otro proyecto MyST publicado
: Todo sitio MyST publica un catálogo de sus etiquetas (el fichero `myst.xref.json`). Con él, se cita cualquier elemento etiquetado de ese proyecto (una página, un apartado, una figura, una ecuación) como si fuera propio.

Documentación hecha con Sphinx
: Muchos proyectos de software (Python, por ejemplo) publican su documentación con Sphinx, que tiene un catálogo equivalente (`objects.inv`). MyST lo reconoce igual.

Wikipedia
: Los enlaces a Wikipedia muestran en la ventana emergente el resumen del artículo.

Publicaciones con DOI
: Un enlace `doi:` se convierte además en una cita bibliográfica.

## Declarar un proyecto externo

Los proyectos MyST y Sphinx se declaran en la configuración, con un nombre corto y su dirección:

```yaml
project:
  references:
    spec: https://mystmd.org/spec
```

`spec` es la especificación del lenguaje MyST, publicada como proyecto MyST. Conviene citar proyectos **estables**: los que se mantienen publicados en la misma dirección y no cambian sus etiquetas con frecuencia, como la documentación oficial de un lenguaje o de una herramienta.

Al construir, MyST descarga el catálogo de cada proyecto declarado. Por eso esta configuración necesita conexión a internet, y por eso la principal, `myst.yml`, no la incluye: así se puede construir sin conexión.

## Citar

Se escribe `xref:`, el nombre corto y, si se quiere un elemento concreto, la ruta de la página y la etiqueta tras `#`:

```markdown
- El proyecto entero: [](xref:spec)
- Un elemento: [](xref:spec#paragraph)
- Un elemento de una página concreta: <xref:spec/tables#example>
- Con texto propio: [la definición de párrafo](xref:spec#paragraph)
```

Resultado:

- El proyecto entero: [](xref:spec)
- Un elemento: [](xref:spec#paragraph)
- Un elemento de una página concreta: <xref:spec/tables#example>
- Con texto propio: [la definición de párrafo](xref:spec#paragraph)

Pasa el ratón por encima: la ventana emergente muestra el elemento citado e indica de qué proyecto procede. Las etiquetas se averiguan en la fuente del otro proyecto, o en su catálogo: basta abrir en el navegador su dirección seguida de `/myst.xref.json`.

## Wikipedia

No hace falta declarar nada. Con el prefijo `wiki:` se enlaza la Wikipedia en inglés, escribiendo el título del artículo con guiones bajos en lugar de espacios. Para otro idioma, se usa la dirección completa del artículo:

```markdown
- <wiki:Projectile_motion>
- [El tiro parabólico](https://es.wikipedia.org/wiki/Tiro_parabólico), en la Wikipedia en español
```

Resultado:

- <wiki:Projectile_motion>
- [El tiro parabólico](https://es.wikipedia.org/wiki/Tiro_parabólico), en la Wikipedia en español

## Los proyectos propios, también

Lo mismo sirve para los materiales propios publicados: los otros ejemplos de esta serie, o los de otra asignatura. Basta declararlos en `references` con su dirección pública. Así, varios proyectos independientes pueden citarse entre sí sin copiar nada.

Hay dos condiciones. Un proyecto solo se puede citar después de publicarlo, porque MyST necesita su catálogo para construir el que lo cita. Y si el proyecto citado cambia de dirección o renombra sus etiquetas, las citas se rompen.

:::{warning} Citar, sí; incrustar, con cuidado
También se puede incrustar un elemento de otro proyecto (`:::{embed} xref:spec#paragraph`). Con MyST 1.13 funciona en la web, pero si el elemento es una imagen, la construcción da un error, porque busca el fichero en el proyecto propio. Para reutilizar contenido entre proyectos, lo más seguro es la cita.
:::

:::{tip} Para explorar más
- Referencias externas en la guía de MyST: <https://mystmd.org/guide/external-references>.
- Añade a `references` la documentación de Python (`python: https://docs.python.org/3.13/`) y cita alguna de sus páginas.
:::
