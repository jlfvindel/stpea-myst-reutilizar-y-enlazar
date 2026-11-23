---
title: Tres configuraciones, un mismo repositorio
short_title: Configuraciones
label: configuraciones
---

El repositorio permite montar presentaciones distintas; las configuraciones permiten publicarlas de formas distintas. Este proyecto tiene tres, y también ellas reutilizan piezas entre sí.

| Fichero | Se usa con | Qué produce |
|---|---|---|
| `myst.yml` | `myst start` | Esta guía completa: guía, presentaciones y anexos |
| `myst-alumnado.yml` | `myst --config myst-alumnado.yml start` | Solo lo que lee el alumnado, y un PDF con otro índice |
| `myst-enlazado.yml` | `myst --config myst-enlazado.yml start` | La guía, con citas a proyectos externos (necesita internet al construir) |

## Lo común, en un fichero aparte

Autoría, licencia, bibliografía y plantillas de numeración son iguales en las tres. En lugar de repetirlas, están en `config/comun.yml`, y cada configuración lo **hereda** con `extends`:

:::{literalinclude} ../config/comun.yml
:language: yaml
:::

La configuración principal solo añade el título y el índice:

:::{literalinclude} ../myst.yml
:language: yaml
:::

Al heredar, MyST combina los dos ficheros. Un valor simple, como el título, se sustituye si el fichero que hereda lo vuelve a definir. Las listas, como las exportaciones, se combinan: se suman las de los dos ficheros. El índice (`toc`) es la excepción, como se ve más abajo.

(toc-externos)=
## Índices externos: uno para la web y otro para el PDF

`myst-alumnado.yml` no escribe ningún índice: los toma de dos ficheros externos.

:::{literalinclude} ../myst-alumnado.yml
:language: yaml
:::

El índice **del sitio web** viene de `tocs/alumnado.yml`, que se hereda con `extends` igual que `comun.yml`. Es un fichero de configuración que solo contiene el índice:

:::{literalinclude} ../tocs/alumnado.yml
:language: yaml
:::

El índice **del PDF** se indica en la exportación, con `toc: tocs/libro/_toc.yml`:

:::{literalinclude} ../tocs/libro/_toc.yml
:language: yaml
:::

Los dos índices son distintos a propósito. En la web, el repositorio está oculto: el alumnado lo consulta en las ventanas emergentes. En papel no hay ventanas emergentes, y además **todo lo que se cita tiene que estar dentro del documento**. Por eso el índice del libro añade el repositorio como capítulos finales, y deja fuera el índice alfabético, que no tiene sentido sin enlaces.

:::{note} Dos formatos de índice
Para la exportación, un índice externo tiene que estar en el formato de Jupyter Book 1 (`format: jb-book`, con `root` y `chapters`), que es distinto del de `myst.yml`. Sus rutas son relativas a la carpeta del propio índice y se escriben sin extensión. La página `root` no se convierte en capítulo del PDF. Si no hace falta que el índice sea un fichero aparte, también se puede escribir dentro de la exportación, con el mismo formato que el `toc` del proyecto.
:::

Para obtener el PDF:

```bash
myst --config myst-alumnado.yml build --pdf
```

### Qué cambia en el PDF

Este PDF se compone con LaTeX, y no con Typst como en los proyectos anteriores. Con MyST 1.13, Typst se detiene con un error en cuanto el documento contiene citas al glosario (`{term}`) o entradas de índice (`{index}`), y las presentaciones de este proyecto tienen las dos cosas. LaTeX las tolera, aunque con pérdidas. Al comparar el PDF con la web:

- **La numeración es otra.** LaTeX numera por capítulos (definición 1.1.1, ecuación 3.2…) y numera **todo**: también lo que en la web estaba en páginas ocultas, y también cada copia incrustada, que recibe su propio número en el capítulo donde aparece.
- **Los términos del glosario** quedan como texto normal, sin enlace (MyST avisa con `Unknown glossary entry`).
- **Los ejercicios** no se exportan: el apartado «Para practicar» del tema queda vacío.
- **Las imágenes SVG** necesitan Inkscape para convertirse.
- **Los grados** se escriben en este proyecto como `$45^\circ$` y no con el carácter `°`, que la plantilla LaTeX no compone bien.
- **La bibliografía** se reúne en un capítulo final, en lugar de aparecer al pie de cada página.

## Heredar una configuración entera

`myst-enlazado.yml` hereda directamente `myst.yml` (y, a través de él, `comun.yml`). Añade la dirección de un proyecto MyST externo y un índice con una página más:

:::{literalinclude} ../myst-enlazado.yml
:language: yaml
:::

Fíjate en que el índice se repite entero. A diferencia de las demás listas, el índice no se combina al heredar: el nuevo **sustituye** al heredado. Por eso, cuando dos configuraciones comparten casi todo el índice, puede convenir sacarlo a un fichero externo, como se ha hecho con el del alumnado.

:::{tip} Para explorar más
- Crea `myst-repaso.yml` que herede `config/comun.yml` y tenga como índice solo la ficha de repaso y el repositorio oculto. ¿Qué citas se rompen, y por qué?
- La herencia de configuraciones, en la guía de MyST: <https://mystmd.org/guide/configuration>.
:::
