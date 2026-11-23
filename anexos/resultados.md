---
title: 'Anexo: resultados'
short_title: Resultados
label: anexo-resultados
---

Esta página es también parte del repositorio, pero **visible**: aparece en el menú y, por eso, sus elementos **sí se numeran**. Las presentaciones citan e incrustan estos resultados, y conservan el número que tienen aquí.

## Ecuaciones del movimiento

Con el origen en el punto de lanzamiento, la posición en cada instante es

$$
x(t) = v_0\cos\theta\, t, \qquad y(t) = v_0\sin\theta\, t - \tfrac{1}{2} g t^2 .
$$ (eq-posicion)

El proyectil vuelve al suelo ($y = 0$) en el instante

$$
t_v = \frac{2 v_0 \sin\theta}{g}.
$$ (eq-tiempo)

Sustituyendo $t_v$ en $x(t)$ se obtiene el alcance, y evaluando $y$ en $t_v/2$, la altura máxima:

$$
R = \frac{v_0^2 \sin 2\theta}{g}, \qquad h_{\max} = \frac{v_0^2 \sin^2\theta}{2g}.
$$ (eq-alcance)

## Proposiciones

:::{prf:proposition} Ángulo de alcance máximo
:label: prop-45

Para una velocidad inicial fija, el alcance es máximo cuando $\theta = 45^\circ$.
:::

:::{prf:proof}
:label: dem-45

Por [](#eq-alcance), $R$ es proporcional a $\sin 2\theta$, que vale como máximo 1. Ese máximo se alcanza cuando $2\theta = 90^\circ$, es decir, $\theta = 45^\circ$.
:::

:::{prf:corollary} Ángulos complementarios
:label: cor-complementarios

Dos lanzamientos con la misma velocidad y {term}`ángulos complementarios` tienen el mismo alcance.
:::

:::{prf:proof}
Si $\theta_2 = 90^\circ - \theta_1$, entonces $\sin 2\theta_2 = \sin(180^\circ - 2\theta_1) = \sin 2\theta_1$, y por [](#eq-alcance) los dos alcances coinciden.
:::

:::{prf:example} Lanzamiento a 20 m/s
:label: ejemplo-20

Con $v_0 = 20$ m/s, a $45^\circ$ el alcance es $400/9{,}81 \approx 40{,}8$ m. A $30^\circ$ y a $60^\circ$, por [](#cor-complementarios), es el mismo: $\approx 35{,}3$ m.
:::

:::{prf:remark}
En un lanzamiento real, el rozamiento con el aire reduce el alcance respecto al calculado aquí {cite:p}`halliday2014`.
:::
