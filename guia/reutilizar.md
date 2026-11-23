---
title: 'Reutilizar: embed, include y literalinclude'
short_title: Reutilizar
label: reutilizar
---

Hay tres directivas para traer a una página contenido escrito en otro sitio. Se diferencian en **qué** traen y en **cómo** queda numerado.

## `embed`: una pieza con etiqueta

`embed` copia en la página un elemento etiquetado de cualquier otra página del proyecto: una definición, una ecuación, una figura, un apartado entero…

```markdown
:::{embed} #prop-45
:::
```

Resultado:

:::{embed} #prop-45
:::

La pieza sigue viviendo en su página de origen. Lo que se ve aquí es una copia que se actualiza sola, y **conserva el número que tiene en el origen**: es la proposición 1 del anexo, aunque aquí sea la primera que aparece.

Si la etiqueta es de un apartado (un título precedido de `(etiqueta)=`), `embed` trae el apartado completo, con su título:

```markdown
:::{embed} #ficha-componentes
:::
```

Resultado:

:::{embed} #ficha-componentes
:::

## `include`: un fichero entero

`include` inserta el contenido de un fichero como si estuviera escrito en la página. La ruta es relativa a la página que incluye:

```markdown
:::{include} ../fragmentos/unidades.md
:::
```

Resultado:

:::{include} ../fragmentos/unidades.md
:::

A diferencia de `embed`, lo incluido **pasa a ser de la página**: si contiene ecuaciones o ejercicios, se numeran en la secuencia de la página que incluye, como cualquier otro elemento suyo. Así, el ejercicio de `fragmentos/ejercicio-alcance.md` es el ejercicio 1 del [tema](#tema), que es donde se incluye.

## `literalinclude`: un fichero como código

`literalinclude` muestra el fichero tal cual, sin interpretarlo. Sirve para enseñar cómo está escrito un fragmento:

````markdown
```{literalinclude} ../fragmentos/unidades.md
:language: markdown
```
````

Resultado:

```{literalinclude} ../fragmentos/unidades.md
:language: markdown
```

(numeracion)=
## Dónde nace el número

La numeración es la parte menos intuitiva de la reutilización. MyST numera **por página**, y cada elemento recibe el número de la página donde está escrito:

| El elemento está… | Su número | Ejemplo en este proyecto |
|---|---|---|
| en una página visible | el de esa página, también cuando se incrusta en otra | [](#prop-45), [](#eq-alcance) |
| en una página oculta | ninguno | la [definición de alcance](#def-alcance) |
| en un fichero incluido | el de la página que lo incluye, en su secuencia | [](#ej-alcance) |
| en un fichero incluido en dos páginas | etiqueta duplicada: MyST avisa | — |

Mira el efecto en la [ficha de repaso](#repaso): incrusta las ecuaciones del anexo, y por eso empiezan en la (2), no en la (1).

Todo esto vale para la web. En un PDF compuesto con LaTeX, la numeración la decide LaTeX, por capítulos, y es distinta: lo explica la página de [configuraciones](#configuraciones).

:::{note} Citar lo que no tiene número
Una cita sin texto a un elemento numerado muestra su número: [](#prop-45). Si el elemento no tiene número, muestra su título, si lo tiene: [](#def-alcance). Una figura de una página oculta no tiene ni número ni título, así que a las piezas ocultas conviene citarlas siempre con un texto propio: [la gráfica de las trayectorias](#fig-trayectorias).
:::

## El texto de las citas, en español

Por defecto, el texto automático de las citas sale en inglés: *Figure 1*, *Definition 1*… Se cambia en la configuración, bajo `numbering`, con una plantilla para cada tipo de elemento, donde `%s` es el número. En este proyecto está en `config/comun.yml`:

```yaml
numbering:
  figure:
    template: figura %s
  proof:proposition:
    template: proposición %s
  exercise:
    template: ejercicio %s
```

Por eso las citas dicen «proposición 1» o «ejercicio 1». La plantilla afecta solo a las citas: el rótulo del propio recuadro («Proposition 1», «Exercise 1») lo pone el tema web y sigue en inglés.

:::{tip} Para explorar más
- Prueba a quitar `hidden: true` de `repositorio/conceptos.md` en `myst.yml`: las definiciones pasarán a tener número, y también las citas a ellas.
- Todas las opciones de `embed` e `include`: <https://mystmd.org/guide/embed>. Entre ellas hay dos para cambiar o quitar el número de lo incrustado, `:enumerator:` y `:enumerated:`.
:::
