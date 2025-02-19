---
layout: default
title: Cours 4 & 5 - Traitements du Signal 1D et Propriétés de la Transformée de Fourier Discrète
---

**Responsable :** [Jonathan Vacher](jonathan.vacher@u-paris.fr)

**Contributeurs/contributrices :** E. Provenzi, C. Sutour, E. Luçon, Q. Denoyelle.

## 1 Interprétation des coefficients de Fourier

### 1.1 Échantillonnage d'un Polynôme Trigonométrique

**Définition 1 (Polynôme Trigonométrique).** Soit $ P \in \mathcal{F}(\mathbb{R}, \mathbb{C}) $ une fonction de la variable réelle à valeurs complexes. La fonction $ P $ est un polynôme trigonométrique si et seulement s'il existe $ (Q_{1}, Q_{2}) \in \mathbb{C}[X]^{2} $ tel que pour tout $ x \in \mathbb{R} $,

$$
P(x) = Q_{1}(e^{\mathrm{i} x}) + Q_{2}(e^{-\mathrm{i} x})
$$

Autrement dit, il existe $ N \in \mathbb{N} $ et $ (c_{-N}, \ldots, c_{-1}, c_{0}, c_{1}, \ldots, c_{N}) \in \mathbb{C}^{2 N+1} $ tels que pour tout $ x \in \mathbb{R} $,

$$
P(x) = \sum_{m=-N}^{N} c_{m} (e^{\mathrm{i} x})^{m} = \sum_{m=-N}^{N} c_{m} e^{\mathrm{i} m x}
$$

**Remarque 1 (Fonctions Harmoniques).** La fonction $ H_{c}: x \mapsto e^{\mathrm{i} x} $ est appelée harmonique complexe fondamentale et les fonctions $ H_{c ; m}: x \mapsto e^{\mathrm{i} m x} $ pour $ m \in \{2, \ldots, N-1\} $ sont appelées harmoniques complexes d'ordre supérieur.

![Figure 1](attachment:image.png)

*Figure 1. Parties réelles de la fonction harmonique fondamentale et des fonctions harmoniques d'ordre 2 à 5.*

**Proposition 1.** Un polynôme trigonométrique est $ 2 \pi $-périodique.

**Définition 2 (Échantillonnage d'une Fonction Périodique).** Soit $ f \in \mathcal{F}(\mathbb{R}, \mathbb{C}) $ une fonction $ T $-périodique (i.e. pour tout $ x \in \mathbb{R}, f(x+T) = f(x) $) et $ N \in \mathbb{N}^{*} $. L'échantillonnage à la fréquence $ N / \tau $ (ou de période $ T / N $) de la fonction $ f $ est la suite $ u = (u_{n})_{n \in \mathbb{Z}} $ définie pour tout $ n \in \mathbb{Z} $ par

$$
u_{n} = f\left(\frac{T n}{N}\right)
$$

En pratique, on échantillonnera souvent des fonctions $ 2 \pi $-périodique, on aura

$$
u_{n} = f\left(\frac{2 \pi n}{N}\right)
$$

**Proposition 2.** La suite $ u $ échantillonnant une fonction $ T $-périodique $ f $ à la fréquence $ N / \tau \in \mathbb{N}^{*} $ est $ N $-périodique i.e. $ u \in \ell_{N} $.

**Démonstration.** Voir cours manuscrit.

La proposition suivante fait lien entre les polynômes trigonométriques et la transformée de Fourier discrète via la notion d'échantillonnage.

**Proposition 3.** Soit $ P $ un polynôme trigonométrique et $ z $ la suite échantillonnant $ P $ à la fréquence $ N / z \tau $. Pour tout $ (x, n) \in \mathbb{R} \times \mathbb{Z} $,

$$
P(x) = \sum_{m=0}^{N-1} c_{m} e^{\mathrm{i} m x} \quad \text{et} \quad z_{n} = P\left(\frac{2 \pi n}{N}\right) = \sum_{m=0}^{N-1} c_{m} e^{2 \mathrm{i} \pi \frac{n}{N} \mathrm{i}}
$$

avec $ (c_{0}, \ldots, c_{N-1}) \in \mathbb{C}^{N} $. Alors pour tout $ m \in \{0, \ldots, N-1\} $,

$$
\hat{z}_{m} = \mathcal{F}_{N}(z)_{m} = N c_{m}
$$

**Démonstration.** Voir cours manuscrit.

Ce résultat signifie deux choses :
(i) une suite périodique $ z \in \ell_{N} $ peut toujours être vu comme le résultat de l'échantillonnage à la fréquence $ N / z \tau $ du polynôme

$$
P(x) = \sum_{m=0}^{N-1} \frac{z_{m}}{N} e^{\mathrm{i} m x}
$$

(ii) la transformée de Fourier discrète $ \hat{z} \in \ell_{N} $ d'une suite périodique $ z \in \ell_{N} $ est la suite des coefficients du polynôme échantillonné à la constante $ N $ près.

**Limite de l'échantillonnage et symétries** L'échantillonnage limite la possibilités de représenter les fonctions harmoniques d'ordre trop grand! Cette limitation est exprimée par la proposition suivante.

**Proposition 4.** Soient $ (H_{m})_{m \in \mathbb{Z}} $ les fonctions harmoniques réelles et $ (h_{m})_{m \in \mathbb{Z}} \subset \ell_{N} $ les suites de leurs échantillons à la fréquence $ N / z \tau $ (on suppose $ N $ pair ici). Pour tout $ m \in \mathbb{Z} $ et tout $ (x, n) \in \mathbb{R} \times \mathbb{Z} $,

$$
H_{m}(x) = \cos (m x) \quad \text{et} \quad h_{m, n} = \cos \left(\frac{2 \pi m n}{N}\right)
$$

Alors pour tout $ (m, n) \in \mathbb{Z}^{2} $,

$$
h_{m+N, n} = h_{m, n} \quad \text{et} \quad h_{N-m, n} = h_{m, n}
$$

**Démonstration.** Voir cours manuscrit.

Cette proposition signifie
(i) que pour tout $ k \in \mathbb{Z} $ les suites $ h_{m+k N} $ et $ h_{m} $ sont identiques pour tout $ m \in \{0, \ldots, N-1\} $.
(ii) que les suites $ h_{m} $ et $ h_{N-m} $ sont identiques pour tout $ m \in \{0, \ldots, N-1\} $ (ou $ m \in \left\{0, \ldots, \frac{N}{2}\right\} $ pour ne pas dire 2 fois la même chose).

Autrement dit lorsque l'on s'autorise à avoir $ N $ échantillons, on ne peut représenter de manière unique à l'aide de leurs échantillons que les fonctions harmoniques $ H_{m} $ pour $ m \in \left\{0, \ldots, \frac{N}{2}\right\} $. Lorsque $ m \in \left\{\frac{N}{2}+1, \ldots, N-1\right\} $, les fonctions harmoniques $ H_{m} $ ont les mêmes échantillons que les précédentes (i.e. lorsque $ m \in \left\{0, \ldots, \frac{N}{2}\right\} $). Un exemple est donné dans la figure 2 pour $ N = 6 $. En conclusion, étant donné un échantillonnage à la fréquence $ N / z \tau $, on peut représenter de manière unique (cf. exercice TD 3) les fonctions harmoniques jusqu'à l'ordre $ N / z $ (les autres fonctions Harmoniques restent inaccessibles car leurs échantillons ne sont pas différents des fonctions Harmoniques précédentes). Autrement dit, la fréquence maximale d'un signal que l'on peut représenter à l'aide de $ N $ échantillons est $ N / 2 $. Il s'agit de la fonction harmonique d'ordre $ N / 2 $ i.e. pour tout $ n \in \mathbb{Z} $,

$$
h_{\frac{N}{2}, n} = \cos (\pi n) = (-1)^{n}
$$

On comprend intuitivement qu'il s'agit bien de la suite qui oscille le plus en passant de 1 à -1 à chaque incrément d'indice d'une unité. Le résultat limitant la fréquence maximale que l'on peut représenter à l'aide d'un certain nombre d'échantillon correspond au théorème de Shannon.

![Figure 2](attachment:image.png)

*FIGURE 2. Échantillonnage des fonctions harmoniques à la fréquence $ N = 6 \times 2 \pi $. En haut à gauche : partie réelle de l'harmonique fondamentale et son échantillonnage. En haut à droite : les harmoniques d'ordre 5 et 7 ont les mêmes échantillons que l'harmonique fondamentale. En bas à gauche : partie réelle de l'harmonique d'ordre 2 et son échantillonnage. En bas à droite : les harmoniques d'ordre 4 et 8 ont les mêmes échantillons que l'harmonique d'ordre 2.*

**Multiplier des signaux entre-eux** On sait que l'ensemble des suites muni de l'addition et de la multiplication par un scalaire forme un espace vectoriel $ (\ell_{n}, +, \cdot) $. Il est possible d'enrichir les opérations entre les suites en définissant une notion de produit. De manière intuitive, comme pour l'addition, le produit $ u v $ de deux suites $ (u, v) \in \ell_{N} $ peut être définie comme la suites des produits terme à terme i.e. pour tout $ n \in \mathbb{Z} $,

$$
(u v)_{n} = u_{n} v_{n}
$$

Or on a vu que des suites périodiques peuvent toujours être vu comme l'échantillonnage de polynômes dont les coefficients correspondent aux transformées de Fourier discrètes de ces suites, ainsi peut poser pour tout $ x \in \mathbb{R} $

$$
P_{n}(x) = \sum_{m=0}^{N-1} \frac{\tilde{u}_{m}}{N} e^{\mathrm{i} m x}, \quad P_{v}(x) = \sum_{m=0}^{N-1} \frac{\tilde{v}_{m}}{N} e^{\mathrm{i} m x} \quad \text{et} \quad P_{u v}(x) = \sum_{m=0}^{N-1} \frac{(\widehat{u v})_{m}}{N} e^{\mathrm{i} m x}
$$

où pour tout $ n \in \mathbb{Z}, u_{n} = P_{n}\left(2 \pi n / \mathcal{N}\right), v_{n} = P_{v}\left(2 \pi n / \mathcal{N}\right) $ et $ (u v)_{n} = P_{u v}\left(2 \pi n / \mathcal{N}\right) $. Or, par définition la suite produit $ u v $ est définie par le produit terme à terme donc l'équation (1) se réécrit pour tout $ n \in \mathbb{Z} $,

$$
P_{u v}\left(\frac{2 \pi n}{N}\right) = P_{u}\left(\frac{2 \pi n}{N}\right) P_{v}\left(\frac{2 \pi n}{N}\right)
$$

Calculons donc le produit des polynômes $ P_{n} $ et $ P_{v} $, pour tout $ x \in \mathbb{R} $, on a

$$
\begin{aligned}
P_{n}(x) P_{v}(x) & = \sum_{m=0}^{N-1} \frac{\hat{u}_{m}}{N} e^{\mathrm{i} m x} \sum_{m=0}^{N-1} \frac{\hat{v}_{m}}{N} e^{\mathrm{i} m x} = \frac{1}{N^{2}} \sum_{k=0}^{N-1} \sum_{l=0}^{N-1} \hat{u}_{k} e^{\mathrm{i} k x} \hat{u}_{l} e^{\mathrm{i} l x} = \frac{1}{N^{2}} \sum_{k=0}^{N-1} \sum_{l=0}^{N-1} \hat{u}_{k} \hat{u}_{l} e^{(\mathrm{i} k+l) x} \\
& = \frac{1}{N^{2}} \sum_{m=0}^{N-1} \sum_{k=0}^{N-1} \sum_{l=0}^{N-1} \hat{u}_{k} \hat{u}_{l} \delta_{k+l, n} e^{(\mathrm{i} k+l) x} = \frac{1}{N^{2}} \sum_{m=0}^{N-1} e^{\mathrm{i} m x} \sum_{k=0}^{N-1} \sum_{l=0}^{N-1} \hat{u}_{k} \hat{u}_{l} \delta_{k+l, n} \\
& = \frac{1}{N^{2}} \sum_{m=0}^{N-1} e^{\mathrm{i} m x} \sum_{k=0}^{N-1} \hat{u}_{k} \hat{u}_{m-k} = \sum_{m=0}^{N-1} \left(\frac{1}{N^{2}} \sum_{k=0}^{N-1} \hat{u}_{k} \hat{u}_{m-k}\right) e^{\mathrm{i} m x}
\end{aligned}
$$

Or puisque

$$
P_{n}(x) P_{v}(x) = P_{n v}(x) = \sum_{m=0}^{N-1} \frac{(\widehat{u v})_{m}}{N} e^{\mathrm{i} m x}
$$

on en déduit par unicité des coefficients de Fourier que

$$
(\widehat{u v})_{m} = \frac{1}{N} \sum_{k=0}^{N-1} \hat{u}_{k} \hat{u}_{m-k}
$$

La transformée de Fourier discrète du produit de deux suites mène à une expression remarquable. En fait, il s'agit d'une nouvelle notion de produit : c'est le produit de convolution. On a la définition suivante.

**Définition 3 (Produit de Convolution).** Soit $ (u, v) \in \ell_{N}^{2} $, on définit le produit de convolution de $ u $ et $ v $ comme la suite $ u * v $ avec pour tout $ n \in \mathbb{Z} $,

$$
(u * v)_{n} = \sum_{k=0}^{N-1} u_{k} v_{n-k}
$$

**Proposition 5 (Symétrie du Produit de Convolution).** Soit $ (u, v) \in \ell_{N}^{2} $, le produit de convolution de $ u $ et $ v $ vérifie pour tout $ n \in \mathbb{Z} $,

$$
(u * v)_{n} = \sum_{k=0}^{N-1} u_{k} v_{n-k} = \sum_{k=0}^{N-1} u_{n-k} v_{k}
$$

**Démonstration.** Voir cours manuscrit.

![Figure 3](attachment:image.png)

*Figure 3. Illustration du produit de convolution de deux suites $ (u, v) \in \ell_{3}^{2} $.*

### 1.2 Signaux et Spectres

Un signal est une mesure physique réalisée par un capteur. À l'ère du numérique un signal est une collection discrète de mesures physiques. Ces mesures dépendent généralement du temps (la température mesurée à un endroit, le son, etc.) ou de l'espace (la température mesurée à différents endroits, les images, etc.). On a donc bien à faire à une suite de $ N $ mesures $ z = (z_{n})_{n \in \mathbb{Z}} \in \ell_{N} $. Jusqu'ici on a supposé que des indices $ n \in \mathbb{Z} $, c'est-à-dire à une seule dimension. Cela correspond généralement à un signal temporel. On pourrait de la même manière considérer des indices $ (m, n) \in \mathbb{Z}^{2} $. Cela correspondrait alors par exemple à un signal spatial comme une image, les indices $ (m, n) $ correspondant à la position d'un pixel. De plus, on a supposé que notre signal était périodique, c'est le cas par exemple pour la température au cours de l'année. Bien que ça ne soit pas le cas de la plupart des signaux (le son, les images, etc.), c'est tout de même une hypothèse très pratique car elle permet d'étudier un signal sur un domaine borné.

En pratique on dit que la transformée de Fourier discrète permet de passer d'une représentation temporelle ou spatial à une représentation fréquentielle (on à l'espace de Fourier). Une analogie intéressante consiste à voir la transformée de Fourier comme l'équivalent du prisme de Newton pour les mathématiques. Le prisme de Newton permet de decomposer la lumière blanche en ses composantes colorées. Or la couleur de la lumière est caractérisée par la fréquence (ou longueur d'onde) de l'onde électromagnétique qui modélise la lumière. Les lumières de différentes couleurs correspondent donc bien à des ondes des différentes fréquences qui, sommées ensemble, forment la lumière blanche. La transformée de Fourier nous permet de mettre en évidence les différentes "couleurs" qui composent un signal quelconque.

**Définition 4.** Soit $ z \in \ell_{N} $ et $ \hat{z} = \mathcal{F}_{N}(z) \in \ell_{N} $ sa transformée de Fourier discrète. On peut écrire $ \hat{z} $ sous la forme complexe polaire (module et argument), pour tout $ m \in \mathbb{Z} $

$$
\hat{z}_{m} = \left|\hat{z}_{m}\right| e^{\mathrm{i} \arg \left(\hat{z}_{m}\right)}
$$

Le module $ \left|\hat{z}_{m}\right| $ est appelé amplitude de la fréquence $ m $ et l'argument $ \arg \left(\hat{z}_{m}\right) $ est appelé phase de la fréquence $ m $. De plus, on utilise le vocabulaire suivant
(i) $ \left\{\hat{z}_{m}, m \in \{0, \ldots, N-1\}\right\} $ est le spectre de $ z $,
(ii) $ \left\{\left|\hat{z}_{m}\right|, m \in \{0, \ldots, N-1\}\right\} $ est le spectre d'amplitude de $ z $,
(iii) $ \left\{\left|\hat{z}_{m}\right|^{2}, m \in \{0, \ldots, N-1\}\right\} $ est le spectre de puissance de $ z $,
(iv) $ \left\{\arg \left(\hat{z}_{m}\right), m \in \{0, \ldots, N-1\}\right\} $ est le spectre de phases de $ z $.

**Quelques interprétations** L'identité de Plancherel s'interprète comme la conservation de l'énergie totale du signal

$$
\|z\|^{2} = \frac{1}{N} \sum_{m=0}^{N-1} \left|\hat{z}_{m}\right|^{2} = \frac{1}{N} \|\hat{z}\|^{2}
$$

On observe en fait que l'énergie totale du signal se décompose comme la somme des énergies associées à chaque harmonique (le facteur $ \nicefrac{{1}}{{N}} $ apparaît à cause de notre choix de normalisation dans la définition de la transformée de Fourier discrète).

Un coefficient de Fourier joue un rôle particulier, c'est $ \hat{z}_{0} $. Ce coefficient correspond en fait à la valeur moyenne de $ z $

$$
\hat{z}_{0} = \sum_{n=0}^{N-1} z_{n} e^{2 i \pi \frac{n \pi}{N}} = \sum_{n=0}^{N-1} z_{n} = N \langle z \rangle
$$

où $ \langle z \rangle = \frac{1}{N} \sum_{n=0}^{N-1} z_{n} $ est la valeur moyenne du signal $ z $. On peut alors réécrire le signal $ z $ de la manière suivante

$$
z_{n} = \frac{1}{N} \sum_{m=0}^{N-1} \hat{z}_{m} e^{2 i \pi \frac{m \pi}{N}} = \frac{1}{N} N \langle z \rangle + \frac{1}{N} \sum_{m=1}^{N-1} \hat{z}_{m} e^{2 i \pi \frac{m \pi}{N}} = \langle z \rangle + \frac{1}{N} \sum_{m=1}^{N-1} \hat{z}_{m} e^{2 i \pi \frac{m \pi}{N}}
$$

Par emprunt du vocabulaire utilisé pour l'électricité, le coefficient de Fourier $ \hat{z}_{0} $ correspond à la composante "DC" du signal (courant continu), tandis que les autres termes constituent la composante "AC" (courant alternatif).

## 2 Propriétés de la Transformée de Fourier Discrète

Dans cette section, on démontrera les plus importantes propriétés de la transformée de Fourier discrète. On rappelle la propriété suivante de translation de l'index d'une somme.

**Proposition 6.** Soit $ u \in \mathbb{C}^{\mathbb{Z}} $ une suite complexe alors pour tout $ (m, n, k) \in \mathbb{Z}^{3} $

$$
\sum_{l=m}^{n} a_{l} = \sum_{l=m-k}^{n-k} a_{l+k} = \sum_{l=m+k}^{n+k} a_{l-k}
$$

**Démonstration.** Voir cours manuscrit.

Cette propriété appliquée à une suite périodique donne le lemme suivant.

**Lemme 1.** Soit $ z \in \ell_{N} $ une suite complexe $ N $-périodique alors pour tout $ m \in \mathbb{Z} $

$$
\sum_{n=m}^{m+N-1} z_{n} = \sum_{n=0}^{N-1} z_{n}
$$

i.e. la somme de $ z $ sur tout intervalle de taille $ N $ est constante.

**Démonstration.** Voir cours manuscrit.

### 2.1 Translation d'un Signal et Opérateurs de Translation

Dans cette section on s'intéresse à l'effet qu'a une translation sur la transformée de Fourier discrète d'un signal $ z \in \ell_{N} $. Pour formaliser ceci, on commence par définir ce qu'est une translation en définissant un opérateur (i.e. une application linéaire) de $ \ell_{N} $ effectuant cette opération.

**Définition 5.** Soit $ z \in \ell_{N} $ une suite complexe $ N $-périodique et $ k \in \mathbb{Z} $. On appelle opérateur de translation de longueur $ k $, l'application linéaire suivante

$$
\begin{aligned}
R_{k}: & \ell_{N} \longrightarrow \ell_{N} \\
& z \longmapsto R_{k}(z) \left(\text{ou } R_{k} z\right)
\end{aligned}
$$

où $ R_{k}(z) $ est la suite définie pour tout $ n \in \mathbb{Z} $ par

$$
R_{k}(z)_{n} = z_{n-k} \quad \left(\text{ou } R_{k} z_{n} = z_{n-k}\right)
$$

**Exemple 1 (Exemple d'opérateur de translation).** Soit $ z \in \ell_{6} $ avec

$$
\left(z_{0}, z_{1}, z_{2}, z_{3}, z_{4}, z_{5}\right) = (2, 3-i, 2 i, 4+i, 0, 1)
$$

Regardons l'effet d'une translation de longueur $ k = 2 $. On a

$$
\begin{aligned}
R_{2}(z)_{0} & = z_{0-2} = z_{-2} = z_{-2+6} = z_{4} = 0 \\
R_{2}(z)_{1} & = z_{1-2} = z_{-1} = z_{-1+6} = z_{5} = 1 \\
R_{2}(z)_{2} & = z_{2-2} = z_{0} = 2 \\
R_{2}(z)_{3} & = z_{3-2} = z_{1} = 3 \\
\ldots & = \ldots
\end{aligned}
$$

Ainsi

$$
\left(R_{2}(z)_{0}, R_{2}(z)_{1}, R_{2}(z)_{2}, R_{2}(z)_{3}, R_{2}(z)_{4}, R_{2}(z)_{5}\right) = (0, 1, 2, 3-i, 2 i, 4+i)
$$

L'effet de $ R_{2} $ sur $ z $ est juste de déplacer à droite de 2 positions les éléments de la suite en replaçant au début les éléments de la fin. De la même manière pour la translation de longueur $ k = -2 $, on a

$$
\left(R_{-2}(z)_{0}, R_{-2}(z)_{1}, R_{-2}(z)_{2}, R_{-2}(z)_{3}, R_{-2}(z)_{4}, R_{-2}(z)_{5}\right) = (2 i, 4+i, 0, 1, 2, 3-i)
$$

Un opérateur de translation peut être appliqué à une suite $ z \in \ell_{N} $. Dans ce cas on peut étudier l'effet de cette translation sur la transformée de Fourier $ \hat{z} $ de $ z $. Réciproquement, on peut appliquer un opérateur de translation sur la transformée de Fourier $ \hat{z} $ et étudier l'effet de cette translation sur le signal $ z $ d'origine. Cela conduit aux deux théorèmes suivants.

**Théorème 1.** Soit $ z \in \ell_{N} $ et $ k \in \mathbb{Z} $ alors

$$
\mathcal{F}_{N}\left(R_{k}(z)\right) = \overline{R_{k}(z)} = \overline{\mathcal{E}}_{k} \hat{z}
$$

où on rappelle que pour tout $ m \in \mathbb{Z}, \overline{\mathcal{E}}_{k, m} = e^{2 i \pi \frac{m k}{N}} $.

**Démonstration.** Voir cours manuscrit.

**Remarque 2.** On observe que, en écrivant $ \hat{z}_{m} = \left|\hat{z}_{m}\right| e^{i \operatorname{Arg}\left(\hat{z}_{m}\right)} $, comme $ \left|e^{-2 i \pi \frac{m k}{N}}\right| = 1 $, le produit $ e^{-2 i \pi \frac{m k}{N}} \hat{z}_{m} $ change seulement la phase de $ \hat{z}_{m} $. Cela signifie aussi que la translation ne change pas le module des coefficients de Fourier de $ z $ i.e.

$$
\left|\mathcal{F}_{N}\left(R_{k}(z)\right)_{m}\right| = \left|\mathcal{F}_{N}(z)_{m}\right|
$$

Les modules des coefficients de Fourier de $ z $ et de toutes ses translations $ R_{k}(z) $ pour $ k \in \mathbb{Z} $ sont égaux. Le module des coefficients de Fourier d'un signal porte une information sur l'importance de la fréquence $ m $ présente dans ce signal mais pas sur sa position dans ce signal. Au contraire les phases portent une information locale à propos du signal. Celle-ci est difficile à interpréter. Cependant, on peut dire qu'une discontinuité dans un signal requiert un alignement des phases de plusieurs fréquences pour être correctement représentée. Le théorème 1 est illustré à la figure 4.

![Figure 4](attachment:image.png)

*Figure 4. Translation du signal $ z = e_{2} $ d'indice $ k = 5 $. Le signal translaté est $ R_{5}\left(e_{2}\right) = e_{7} $. À droite en vert, l'argument du signal $ \overline{\mathcal{E}}_{5} $ et en rouge l'argument du signal $ \overline{\mathcal{E}}_{5} \mathcal{F}_{32}(z) $ à comparer à $ \mathcal{F}_{32}\left(R_{5}(z)\right) $.*

**Théorème 2.** Soit $ z \in \ell_{N} $ et $ k \in \mathbb{Z} $ alors

$$
R_{k}\left(\mathcal{F}_{N}(z)\right) = R_{k}(\hat{z}) = \mathcal{F}_{N}\left(\mathcal{E}_{k} z\right) = \overline{\mathcal{E}_{k} z}
$$

où on rappelle que pour tout $ m \in \mathbb{Z}, \overline{\mathcal{E}}_{k, m} = e^{2 i \pi \frac{m k}{N}} $. Ce résultat peut se réécrire

$$
\mathcal{F}_{N}^{-1}\left(R_{k}\left(\mathcal{F}_{N}(z)\right)\right) = \mathcal{F}_{N}^{-1}\left(R_{k}(\hat{z})\right) = \mathcal{E}_{k} z
$$

**Démonstration.** Voir cours manuscrit.

La translation de longueur $ k $ d'une suite $ z $ correspond à la multiplication terme à terme de la transformée de Fourier de cette suite par la suite conjuguée de la $ k $-ième suite de la base de Fourier. De même, la translation de longueur $ k $ de la transformée de Fourier d'une suite correspond à la transformée de Fourier de la multiplication de cette suite par la $ k $-ième suite de la base de Fourier. Les théorèmes 1 et 2 peuvent être résumé par la tableau suivant.

| Représentation originale | Espace de Fourier |
| :--: | :--: |
| $ z_{n-k} $ | $ e^{-2 i \pi \frac{n k}{N}} \hat{z}_{m} $ |
| $ e^{2 i \pi \frac{n k}{N}} z_{n} $ | $ \hat{z}_{m-k} $ |

### 2.2 Conjugaison d'un Signal et Opérateurs de Conjugaison

Dans cette section, on s'intéresse à l'effet qu'a l'opération de conjugaison d'une suite sur sa transformée de Fourier discrète. La conjuguée d'une suite est simplement la suite des termes conjugués de cette suite. Pour écrire simplement les résultats on a besoin de la notion de suite renversée suivante.

**Définition 6 (Suite renversée).** Soit $ z \in \ell_{N} $ la suite renversée de $ z $, notée $ z^{-} $ est définie pour tout $ n \in \mathbb{Z} $ par

$$
z_{n}^{-} = z_{-n}
$$

On a le théorème suivant reliant la transformée de Fourier de la suite conjuguée au renversement de la conjuguée de la transformée de Fourier de cette suite.

**Théorème 3.** Soit $ z \in \ell_{N} $ alors

$$
\mathcal{F}_{N}(\bar{z}) = \overline{\mathcal{F}_{N}(z)^{-}}
$$

Autrement dit, pour tout $ m \in \mathbb{Z} $,

$$
\mathcal{F}_{N}(\bar{z})_{m} = \overline{\mathcal{F}_{N}(z)}_{-m} = \overline{\mathcal{F}_{N}(z)}_{N-m}
$$

**Démonstration.** Voir cours manuscrit.

**Corollaire 1.** Soit $ z \in \ell_{N} $. On a l'équivalence suivante. La suite $ z $ est réelle (i.e. pour tout $ n \in \mathbb{N}, z_{n} \in \mathbb{R} $) ssi pour tout $ m \in \mathbb{Z}, \mathcal{F}_{N}(z)_{m} = \overline{\mathcal{F}_{N}(z)}_{-m} = \overline{\mathcal{F}_{N}(z)}_{N-m} $.

**Démonstration.** Voir cours manuscrit.

![Figure 5](attachment:image.png)

*Figure 5. Illustration du corollaire 1. Symétrie de la transformée discrète d'un signal à valeurs réelles.*

### 2.3 Convolutions entre Signaux et Opérateurs de Convolution

On a définit l'opération de convolution 3 dans la section 1. Donnons un exemple d'un calcul de convolution à la main.

**Exemple 2.** Soit $ (z, w) \in \ell_{4}^{2} $ avec $ \left(z_{0}, z_{1}, z_{2}, z_{3}\right) = (1, 1, 0, 2) $ et $ \left(w_{0}, w_{1}, w_{2}, w_{3}\right) = (i, 0, 1, 2) $. Alors

$$
\begin{aligned}
& (z * w)_{0} = 2 + i \\
& (z * w)_{1} = 2 + i \\
& (z * w)_{2} = 5 \\
& (z * w)_{3} = 3 + i
\end{aligned}
$$

**Théorème 4.** Soient $ (z, w) \in \ell_{N}^{2} $ deux suites complexes $ N $-périodique. On a les résultats suivants

$$
\mathcal{F}_{N}(z * w) = \mathcal{F}_{N}(z) \mathcal{F}_{N}(w)
$$

et

$$
\mathcal{F}_{N}(z w) = \frac{1}{N} \mathcal{F}_{N}(z) * \mathcal{F}_{N}(w)
$$

Autrement dit, la transformée de Fourier discrète du produit de convolution de deux suites est le produit de leur transformée de Fourier discrète. De plus, la transformée de Fourier discrète du produit de deux suites est le produit de convolution de leur transformée de Fourier discrète (divisé par $ N $). Ceci est resumé dans le tableau suivant.

| Représentation originale | Espace de Fourier |
| :--: | :--: |
| $ \bar{z} * w $ | $ \bar{z} w $ |
| $ N z w $ | $ \bar{z} * \bar{w} $ |

**Démonstration.** Voir cours manuscrit.

Le théorème 4 offre une possibilité alternative pour calculer la convolution entre deux signaux $ z $ et $ w $. On peut d'abord effectuer la transformée de Fourier discrète des deux signaux, faire le produit, puis calculer la transformée de Fourier discrète inverse. On peut alors comparer la complexité des deux méthodes de calcul. Supposons que le signal $ z $ est de taille $ N $ et que le signal $ w $ est de taille $ K $ avec $ K < N $. La complexité de l'opération de convolution directe est $ \mathcal{O}(N K) $, en revanche, si on utilise la FFT, la complexité est $ \mathcal{O}(N \log N) $. Par conséquent, il est avantageux de transformer la convolution en un produit terme à terme avec la FFT dès que $ K > \log_{2}(N) $. Par exemple, si $ N = 1024 $, alors $ \log_{2}(N) = 10 $, donc il vaut mieux faire la convolution $ z * w $ dans le domaine de Fourier dès que $ K > 10 $.

Si on fixe un vecteur dans la convolution, on peut définir l'endomorphisme de $ \ell_{N} $ suivant.

**Définition 7 (Opérateur de Convolution).** Soit $ w \in \ell_{N} $. L'opérateur de convolution cannoniquement associé à $ w $ est l'application

\end{aligned}
$$
```$$
\begin{aligned}
T_{w}: & \ell_{N} \longrightarrow \ell_{N} \\
& z \longmapsto T_{w}(z) = w * z
