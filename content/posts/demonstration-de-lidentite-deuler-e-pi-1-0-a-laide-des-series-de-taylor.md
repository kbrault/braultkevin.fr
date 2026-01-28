+++
date = '2024-10-03'
title = "Démonstration de l'identité d'Euler e^i*pi + 1 = 0 à l'aide des séries de Taylor."
categories = ['Maths']
description = "Exploration analytique de la plus belle formule des mathématiques, démontrant comment les séries de Taylor fusionnent les fonctions exponentielles et trigonométriques pour lier e, i, π, 1 et 0."
+++

L'identité d'Euler est une équation célèbre en mathématiques :

$$e^{i\pi} + 1 = 0$$

Elle relie cinq des nombres les plus fondamentaux des mathématiques :
$e$, $i$, $\pi$, $1$, et $0$. En plus cela, trois types de nombres sont
représentés : les entiers, les nombres irrationnels et les nombres
imaginaires. Cette équation est obtenu depuis la formule d'Euler qui
établit la relation fondamentale entre les fonctions trigonométriques et
la fonction exponentielle complexe :

$$e^{i} = \cos x + i \sin x$$

En fixant $x = \pi$ la forme intermédiaire devient donc :
$e^{i\pi} = -1$. Cette égalité correspond au point du cercle unitaire
(cercle de rayon 1 centré à l'origine (0,0)) dont l'angle par rapport à
l'axe des réels positifs est $\pi$.

En d'autres termes, $e^{i\pi}$ se rapporte à un point spécifique sur le
cercle unitaire, qui se trouve directement sur l'axe des réels négatifs
à un angle de $\pi$ radians.

Il y a plusieurs méthodes pour démontrer l'identité d'Euler. La méthode
basée sur les séries de Taylor est l'une des approches analytiques pour
démontrer l'identité d'Euler. Elle repose sur le développement en série
de Taylor de fonctions transcendantes telles que la fonction
exponentielle, le cosinus et le sinus.

Les séries de Taylor permettent de représenter une fonction
différentiable de manière infinie comme une somme infinie de termes
dérivés de cette fonction en un point. Ainsi, la série de Taylor d'une
fonction $f(x)$ autour de $x = 0$ est donnée par :

$$f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(0)}{n!} x^n,$$ 

où
$f^{(n)}(0)$ est la $n$-ème dérivée de $f(x)$ évaluée en $x = 0$, et
$n!$ représente la factorielle de $n$.

La fonction exponentielle complexe $e^z$, où $z$ est un nombre complexe,
admet un développement en série de Taylor autour de 0, valable pour tout
$z \in \mathbb{C}$. 

Cette série est donnée par :

$$e^z = \sum_{n=0}^{\infty} \frac{z^n}{n!} = 1 + z + \frac{z^2}{2!} + \frac{z^3}{3!} + \frac{z^4}{4!} + \cdots.$$

Cette série converge absolument pour tout $z \in \mathbb{C}$.

Pour la fonction exponentielle complexe, nous voulons étudier le cas où
l'argument est purement imaginaire, c'est-à-dire $z = ix$ où $x$ est un
réel. Nous avons donc :

$$e^{ix} = \sum_{n=0}^{\infty} \frac{(ix)^n}{n!}$$ 

Développons les premiers termes de cette série en séparant les puissances paires et
impaires de $ix$. En utilisant le fait que $i^2 = -1$, $i^3 = -i$,
$i^4 = 1$ \... etc, on obtient :

$$e^{ix} = 1 + ix - \frac{x^2}{2!} - i\frac{x^3}{3!} + \frac{x^4}{4!} + i\frac{x^5}{5!} - \cdots.$$

Cette série peut être réorganisée en séparant les termes réels et
imaginaires :

$$e^{ix} = \left( 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \dots \right) + i\left( x - \frac{x^3}{3!} + \frac{x^5}{5!} - \dots \right).$$

Les séries de Taylor des fonctions trigonométriques $\cos(x)$ et
$\sin(x)$, également développées autour de 0, sont respectivement :

-   Pour le cosinus :
    $\cos(x) = \sum_{n=0}^{\infty} (-1)^n \frac{x^{2n}}{(2n)!} = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots.$

-   Pour le sinus :
    $\sin(x) = \sum_{n=0}^{\infty} (-1)^n \frac{x^{2n+1}}{(2n+1)!} = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots.$

En comparant les séries obtenues pour $e^{ix}$ avec celles de $\cos(x)$
et $\sin(x)$, on observe que : $e^{ix} = \cos(x) + i\sin(x).$ 
On retrouve ici la formule d'Euler et constitue un résultat fondamental en
analyse complexe. Elle montre que l'exponentielle complexe $e^{ix}$ peut
être exprimée en termes des fonctions trigonométriques réelles $\cos(x)$
et $\sin(x)$.

Maintenant que nous avons établi que : $e^{ix} = \cos(x) + i\sin(x),$
nous pouvons appliquer cette formule au cas où $x = \pi$. 

En utilisant
les valeurs des fonctions trigonométriques pour $\pi$ :

$$\cos(\pi) = -1 \quad \text{et} \quad \sin(\pi) = 0,$$ 

nous obtenons :

$$e^{i\pi} = \cos(\pi) + i\sin(\pi) = -1 + 0i = -1.$$ 

Nous avons ainsi
montré que : $e^{i\pi} = -1.$ En ajoutant 1 des deux côtés de
l'équation, nous obtenons l'identité d'Euler : 

$$e^{i\pi} + 1 = 0.$$

Il est important de noter que la série de Taylor utilisée ici pour
$e^{ix}$, ainsi que les séries de Taylor pour $\cos(x)$ et $\sin(x)$,
convergent absolument pour tout $x \in \mathbb{R}$. La validité de la
preuve repose donc sur la convergence de ces séries infinies et sur le
fait que les propriétés des séries formelles sont respectées.