# Reutilizar y enlazar

Ejemplo guiado de producción de materiales docentes con [MyST](https://mystmd.org): un repositorio de fragmentos para montar distintas presentaciones: incrustación, numeración, enunciados, glosario, índice, bibliografía, varias configuraciones y referencias a proyectos externos.

Forma parte de una serie de cuatro proyectos independientes, pensados para recorrerse en orden:

1. Usar MyST y maquetar
2. Recursos multimedia
3. **Reutilizar y enlazar** (este)
4. Libros ejecutables

Cada proyecto está construido con el propio MyST: lo que explica está escrito con los recursos que explica.

## Ponerlo en marcha

1. Instala [Node.js](https://nodejs.org) (versión 22 o superior) y MyST: `npm install -g mystmd` (o `pip install mystmd`).
2. En una terminal, desde esta carpeta: `myst start`.
3. Abre <http://localhost:3000>.

El PDF de la edición para el alumnado se compone con LaTeX.

## Configuraciones

| Fichero | Se usa con | Qué produce |
|---|---|---|
| `myst.yml` | `myst start` | Guía completa para el autor |
| `myst-alumnado.yml` | `myst --config myst-alumnado.yml start` | Edición para el alumnado, con PDF de índice propio |
| `myst-enlazado.yml` | `myst --config myst-enlazado.yml start` | Guía con referencias a proyectos externos (necesita internet) |

## Publicarlo

```bash
./preparar-descarga.sh                     # zip de la fuente, para el botón de descarga
BASE_URL=/ruta/del/sitio myst build --html
```

y se copia el contenido de `_build/html` al servidor. Si no se ejecuta `preparar-descarga.sh`, MyST avisa de que falta el fichero de descarga; el resto del sitio funciona igual.

## Licencia y elaboración

José Luis Fernández Vindel. Contenido bajo licencia [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es).

Preparado en colaboración con un asistente de inteligencia artificial (Claude, de Anthropic); el autor ha decidido el enfoque, ha revisado el resultado y responde de su contenido. Comprobado con MyST 1.13.0.
