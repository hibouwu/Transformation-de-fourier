---
layout: default
title: Cours 6 - Opérateurs Stationnaires et Traitement du Signal
---

Responsable : [Jonathan Vacher](jonathan.vacher@u-paris.fr)

Contributeurs/contributrices : E. Provenzi, C. Sutour, E. Luçon, Q. Denoyelle.

## 1 Opérateurs Stationnaires et Matrices Circulantes

### 1.1 Définitions

#### Opérateurs Stationnaires

La notion d'opérateur stationnaire correspond à une propriété simple que doit vérifier par un opérateur linéaire (une application linéaire!). Cette propriété est reliée à la notion de translation. On a vu que la translation est une opération linéaire que l'on peut effectuer sur un signal, on a noté $R_{k}$ l'opérateur de translation d'indice $k$. Cet opérateur peut tout à fait être défini sur l'ensemble des suites (non-périodiques). Dans ce cas là, appliquer une translation d'indice $k$ revient à donner du retard ou de l'avance à un signal (on peut penser à l'écho qui est un même signal sonore qui revient avec du retard). Dire qu'un opérateur est stationnaire revient à dire que le signal image d'un signal retardé ou avancé est égal au signal image retardé ou avancé. En général, on dit qu'un opérateur convertit un signal d'entrée en un signal de sortie. On peut alors reformuler la notion de stationnarité en disant que pour obtenir la conversion d'un signal d'entrée qui est retardé ou avancé, il suffit simplement de retarder ou d'avancer la conversion du signal d'origine non-retardé ou non-avancé. Enfin, on peut dire que si les opérations réalisées par un opérateur sont indépendantes de l'instant auquel on applique à l'opérateur, alors l'opérateur est stationnaire. La notion de stationnarité est rigoureusement définie de la manière suivante.

**Définition 1.** Un opérateur en $T: \ell_{N} \rightarrow \ell_{N}$ est dit stationnaire (ou invariant par translation) ssi pour tout $k \in \mathbb{Z}$ et pour toute suite $z \in \ell_{N}$,

$$
T\left(R_{k}(z)\right)=R_{k}(T(z))
$$

De manière équivalente, on dit que $T$ est stationnaire ssi, pour tout $k \in \mathbb{Z}$, $T$ commute avec l'opérateur de translation $R_{k}$ i.e.

$$
T \circ R_{k}=R_{k} \circ T
$$

**Exemple 1 (Opérateur Stationnaire).** On définit l'opérateur suivant

$$
\begin{aligned}
T:
& \quad \ell_{N} \quad \longrightarrow \quad \ell_{N} \\
& \left(z_{n}\right)_{n \in \mathbb{Z}} \longmapsto T(z)=\left(T(z)_{n}\right)_{n \in \mathbb{Z}}=\left(3 z_{n-2}+\mathrm{i} z_{n}-(2+\mathrm{i}) z_{n+1}\right)_{n \in \mathbb{Z}}
\end{aligned}
$$

L'opérateur $T$ est bien linéaire. On montre que $T$ est stationnaire. Soit $z \in \ell_{N}$ et soit $(n, k) \in \mathbb{Z}^{2}$, calculons d'une part

$$
T\left(R_{k}(z)\right)_{n}=3 R_{k}(z)_{n-2}+\mathrm{i} R_{k}(z)_{n}-(2+\mathrm{i}) R_{k}(z)_{n+1}=3 z_{n-k-2}+\mathrm{i} z_{n-k}-(2+\mathrm{i}) z_{n-k+1}
$$

Et d'autre part

$$
R_{k}(T(z))_{n}=T(z)_{n-k}=3 z_{n-k-2}+\mathrm{i} z_{n-k}-(2+\mathrm{i}) z_{n-k+1}
$$

Ainsi pour tout $k \in \mathbb{Z}, R_{k}(T(z))=T\left(R_{k}(z)\right)$. Donc $T$ commute avec tous les opérateurs de translation et est donc stationnaire.

**Exemple 2 (Opérateur Non-stationnaire).** On définit l'opérateur suivant

$$
\begin{aligned}
T:
&\quad \ell_{N} \longmapsto \quad \ell_{N} \\
&\left(z_{n}\right)_{n \in \mathbb{Z}} \longmapsto T(z)=\left(T(z)_{n}\right)_{n \in \mathbb{Z}}=\left(z_{n}+z_{0}\right)_{n \in \mathbb{Z}}
\end{aligned}
$$

L'opérateur $T$ est bien linéaire. Pour montrer que $T$ n'est pas stationnaire, il suffit de montrer qu'il ne commute pas avec au moins une translation pour au moins un suite $z \in \ell_{N}$. Soit $n \in \mathbb{Z}$, calculons d'une part

$$
T\left(R_{1}(z)\right)_{n}=R_{1}(z)_{n}+R_{1}(z)_{0}=z_{n-1}+z_{-1}
$$

Et d'autre part

$$
R_{1}(T(z))_{n}=T(z)_{n-1}=z_{n-1}+z_{0}
$$

Ainsi pour $z=\delta_{0}$, on a $z_{0}=1 \neq 0=z_{-1}$. Donc $T$ ne commute pas avec $R_{1}$.

#### Matrices Circulantes

On généralise la notion de périodicité aux matrices.

**Définition 2 (Matrices Périodiques).** Soit $A \in \mathcal{M}_{N}(\mathbb{C})$ une matrice de coefficients $\left(a_{m, n}\right)_{(m, n) \in\{0, \ldots, N-1\}^{2}}$. La matrice $A$ est $N$-périodique ssi pour tout $(m, n, k) \in \mathbb{Z}^{3}$,

$$
a_{m+k N, n}=a_{m, n} \quad \text { et } \quad a_{m, n+k N}=a_{m, n}
$$

A是N阶矩阵，任何被不可分割的完整的A组成的一个完整的矩阵都是周期矩阵

La notion de matrice périodique permet de définir les matrices circulantes de manière simple.

**Définition 3 (Matrices Circulantes).** Soit $A \in \mathcal{M}_{N}(\mathbb{C})$ une matrice $N$-périodique de coefficients $\left(a_{m, n}\right)_{(m, n) \in\{0, \ldots, N-1\}^{2}}$. La matrice $A$ est circulante ssi pour tout $(m, n) \in \mathbb{Z}^{2}$,

$$
a_{m+1, n+1}=a_{m, n}
$$

A中的元素斜着相等

Une première proposition fournit une définition équivalente.

**Proposition 1.** Soit $A \in \mathcal{M}_{N}(\mathbb{C})$ une matrice $N$-périodique de coefficients $\left(a_{m, n}\right)_{(m, n) \in\{0, \ldots, N-1\}^{2}}$. La matrice $A$ est circulante ssi pour tout $(m, n, k) \in \mathbb{Z}^{3}$,

$$
a_{m+k, n+k}=a_{m, n}
$$

La définition revient à dire qu'une matrice $A$ est circulante ssi ses coefficients sont constants sur toutes ses diagonales. Autrement dit $A$ s'écrit

$$
A=\left(\begin{array}{ccccc}
a_{0} & a_{1} & a_{2} & \ldots & a_{N-1} \\
a_{N-1} & a_{0} & a_{1} & \ldots & a_{N-2} \\
a_{N-2} & a_{N-1} & a_{0} & \ldots & a_{N-3} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
a_{1} & a_{2} & a_{3} & \ldots & a_{0}
\end{array}\right)
$$

**Exemple 3.** La matrice suivante est circulante

$$
A=\left(\begin{array}{cccc}
3 & 2+i & -1 & 4 i \\
4 i & 3 & 2+i & -1 \\
-1 & 4 i & 3 & 2+i \\
2+i & -1 & 4 i & 3
\end{array}\right)
$$

La matrice suivante n'est pas circulante

$$
B=\left(\begin{array}{lll}
2 & i & 3 \\
3 & 2 & i \\
i & 2 & 3
\end{array}\right)
$$

Pour être circulante, la 3-ième ligne devrait être $(i, 3,2)$.

Une autre manière de voir (ou définir) une matrice circulante est d'utiliser le opérateur de translation.

**Proposition 2.** Soit $A \in \mathcal{M}_{N}(\mathbb{C})$ une matrice $N$-périodique de coefficients $\left(a_{m, n}\right)_{(m, n) \in\{0, \ldots, N-1\}^{2}}$. La matrice $A$ est circulante ssi il existe une suite $a \in \ell_{N}$ telle que

$$
A=\left(\begin{array}{c}
a \\
\hdashline R_{1}(a) \\
\hdashline R_{2}(a) \\
\vdots \\
\hdashline R_{N-1}(a)
\end{array}\right)
$$

### 1.2 Réduction des Opérateurs Stationnaires

Le premier théorème indique que la transformée de Fourier diagonalise les opérateurs stationnaires.

**Théorème 1.** Soit $T \in \mathcal{L}\left(\ell_{N}\right)$ un opérateur linéaire stationnaire. Alors, $T$ est diagonalisable dans la base de Fourier $\mathcal{E}=\left(\mathcal{E}_{m}\right)_{m \in\{0, \ldots, N-1\}}$.

**Démonstration.**

Soit $K \in \llbracket 0, N-1 \rrbracket , \exists (a_0, \dots, a_{N-1}) \in \mathbb{C}^N$, tel que :

$$
T(\mathcal{E}_k) = \sum_{n=0}^{N-1} a_n \mathcal{E}_n
$$

$T$ est stationnaire, donc il commute avec les translations, en particulier avec $R_1$, c'est-à-dire :

$$
T \circ R_1 = R_1 \circ T
$$

Évaluons ces deux termes en $\mathcal{E}_k$ :

$$
\begin{aligned}
T \circ R_1 (\mathcal{E}_k) 
&= R_1(\mathcal{E}_k) \\
&= \mathcal{E}_{k,n-1} \\
&= e^{\frac{2i\pi k(n-1)}{N}} \\
&= e^{-\frac{2i\pi k}{N}} \underbrace{ e^{\frac{2i\pi k}{N}} }_{\mathcal{E}_{k,n}}
\end{aligned}
$$

Donc,

$$
R_1(\mathcal{E}_k) = e^{-\frac{2i\pi k}{N}} \mathcal{E}_k
$$

Ainsi,

$$
\begin{aligned}
T \circ R_1 (\mathcal{E}_k) 
&= T \left( R_1 (\mathcal{E}_k) \right) \\
&= T \left( e^{-\frac{2i\pi k}{N}} \mathcal{E}_k \right) \\
&= e^{-\frac{2i\pi k}{N}} T(\mathcal{E}_k) \\
&= e^{-\frac{2i\pi k}{N}} \sum_{n=0}^{N-1} a_n \mathcal{E}_n
\end{aligned}
$$

De plus,

$$
\begin{aligned}
R_1 \circ T (\mathcal{E}_k) 
&= R_1 \left( T(\mathcal{E}_k) \right) \\
&= R_1 \left( \sum_{n=0}^{N-1} a_n \mathcal{E}_n \right) \\
&= \sum_{n=0}^{N-1} a_n R_1(\mathcal{E}_n) \\
&= \sum_{n=0}^{N-1} a_n e^{-\frac{2i\pi n}{N}} \mathcal{E}_n
\end{aligned}
$$

Donc,

$$
e^{-\frac{2i\pi k}{N}} \sum_{n=0}^{N-1} a_n \mathcal{E}_n = \sum_{n=0}^{N-1} a_n e^{-\frac{2i\pi n}{N}} \mathcal{E}_n
$$

donc,

$$
\sum_{n=0}^{N-1} a_n \left( e^{-\frac{2i\pi k}{N}} - e^{-\frac{2i\pi n}{N}} \right) \mathcal{E}_n = 0
$$

La famille $\{ \mathcal{E}_n \}_{n \in \llbracket 0, N-1 \rrbracket}$ étant une base, elle est **libre**, donc :

$$
\forall n \in \llbracket 0, N-1 \rrbracket, \quad a_n \left( e^{-\frac{2i\pi k}{N}} - e^{-\frac{2i\pi n}{N}} \right) = 0
$$

D'où,

$$
\forall n \neq k, \quad a_n = 0
$$

Car,

$$
e^{-\frac{2i\pi k}{N}} \neq e^{-\frac{2i\pi n}{N}}, \quad \text{si } k \neq n
$$

Finalement,

$$
T(\mathcal{E}_k) = a_k \mathcal{E}_k
$$

Donc, $\mathcal{E}_k$ est un **vecteur propre** de $T$.

**Fin** de la démonstration.

L'interprétation matricielle du théorème 1 est la suivante. Soit $A$ la matrice de $T$ dans la base canonique de $\ell_{N}$. On rappelle que la matrice de la transformée de Fourier (donnant les coefficients de la base de Fourier dans la base canonique) est la matrice de passage de la base canonique à la base de Fourier. Ainsi il s'agit de la matrice de passage qui permet de diagonaliser $A$, on a

$$
D=W_{N} A W_{N}^{-1} \quad \text { et } \quad A=W_{N}^{-1} D W_{N}
$$

La matrice $W_{N}^{-1}$ permet de passer de la base de vecteurs propres de $A$ à la base canonique.

### 1.3 Caractérisation des Opérateurs Stationnaires

Le théorème suivant, le plus important du chapitre, permettra d'expliciter les valeurs propres d'un opérateur stationnaire $T$ d'une façon très simple et aussi de caractériser $T$ comme opérateur de convolution, dans la représentation originale de $z$, et comme un multiplicateur, dans la représentation fréquentielle.

**Théorème 2.** Soit $T \in \mathcal{L}\left(\ell_{N}\right)$ un opérateur linéaire. Les propriétés suivantes sont équivalentes.
(i) $T$ est stationnaire;
(ii) La matrice $A$ représentant $T$ dans la base canonique de $\ell_{N}$ est circulante;
(iii) $T$ est un opérateur de convolution.

**Démonstration.** $ (i) \Rightarrow (ii) $, soit $T$ est **stationnaire**. Soit $A$ la matrice de $T$ dans la base canonique :

$$
A =
\begin{bmatrix}
a_{0,0} & a_{0,1} & \cdots & a_{0, N-1} \\
a_{1,0} & a_{1,1} & \cdots & a_{1, N-1} \\
\vdots  & \vdots  & \ddots & \vdots  \\
a_{N-1,0} & a_{N-1,1} & \cdots & a_{N-1,N-1}
\end{bmatrix}
$$

où $T(e_0), T(e_1), \dots, T(e_{N-1})$ sont les colonnes de cette matrice.

Par définition,

$$
T(e_k) = \sum_{n=0}^{N-1} a_{n,k} e_n
$$

$$
R_1(e_k)_n = e_{k,n-1} =
\begin{cases}
1, & \text{si } k = n-1 \\
0, & \text{sinon}
\end{cases}
 = e_{k+1,n}
$$

$T$ est stationnaire, donc $T \circ R_1 (e_k) = R_1 \circ T (e_k)$

Calculs des termes

$$
T \circ R_1 (e_k) = T(e_{k+1}) = \sum_{n=0}^{N-1} a_{n, k+1} e_n
$$

$$
R_1 \circ T (\mathcal{E}_k) = R_1 \left( \sum_{n=0}^{N-1} a_{n,k} e_n \right) = \sum_{n=0}^{N-1} a_{n,k} R_1 (e_n)
$$

$$
= \sum_{n=0}^{N-1} a_{n,k} e_{n+1} = \sum_{n=1}^{N} a_{n-1,k} e_{n}
$$

Finalement,

$$
\sum_{n=0}^{N-1} a_{n,k+1} e_n = \sum_{n=1}^{N} a_{n-1,k} e_n = \sum_{n=0}^{N-1} a_{n-1,k} e_n
$$

d'où
$$
\sum_{n=0}^{N-1} (a_{n,k+1} - a_{n-1,k}) e_n = 0
$$

La famille $\{e_n\}_{n \in \llbracket 0, N-1 \rrbracket}$ étant une base, elle est libre, donc :

$$
\forall n \in \llbracket 0, N-1 \rrbracket, \quad a_{n,k+1} = a_{n-1,k}
$$

Ou encore,

$$
a_{n+1,k+1} = a_{n,k}
$$

$$(ii) \Rightarrow (iii) \quad A \text{ est circulante}$$

$$
A =
\begin{bmatrix}
a_0 & a_1 & a_2 & \cdots & a_{N-1} \\
a_{N-1} & a_0 & a_1 & \cdots & a_{N-2} \\
a_{N-2} & a_{N-1} & a_0 & \cdots & a_{N-3} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
a_1 & a_2 & a_3 & \cdots & a_0
\end{bmatrix} =
\left(\begin{array}{c}
a \\
\hdashline R_{1}(a) \\
\hdashline R_{2}(a) \\
\vdots \\
\hdashline R_{N-1}(a)
\end{array}\right)
$$

Soit $a \in \rho_N$ tq les lignes de $A$ sont : $R_k(a)$. Soit $z \in \rho_N$.

$$
(Az)_n = \sum_{k=0}^{N-1} R_n(a)_k z_k = \sum_{k=0}^{N-1} \underset{a_{n-k}^{-}}{a_{k-n}} z_k
$$

$$
= ( a^{-} * z )_n
$$

Donc $T$ est un **opérateur de convolution associé** au vecteur $\omega = a^{-}$.

**$(iii) \Rightarrow (ii)$** $T$ est un opérateur de convolution, donc :

$$
\exists \omega \in \rho_N \text{ tq } \forall z \in \rho_N, \quad T(z) = \omega * z
$$

Soit $k \in \mathbb{Z}, n \in \mathbb{Z}$, calculons $T \circ R_k(z)_n$.
$$
\begin{aligned}
T R_k (z)_n &= (\omega * R_k (z))_n \\
            &= \sum_{\ell=0}^{N-1} \omega_\ell R_k (z)_{n-\ell} \\
            &= \sum_{\ell=0}^{N-1} \omega_\ell z_{n-\ell-k}
\end{aligned}
$$

Posons $\upsilon = \sum_{\ell=0}^{N-1} \omega_\ell R_\ell (z)$. alors on écrit :

$$
\begin{aligned}
T R_k (z)_n &= \upsilon_{n-k} \\
            &= R_k (\upsilon)_n \\
            &= R_k \left( \sum_{\ell=0}^{N-1} \omega_\ell R_\ell (z) \right)_n \\
            &= R_k (\omega * z)_n \\
            &= R_k \circ T (z)_n
\end{aligned}
$$

**fin** de la démonstration.

Un peu de vocabulaire utilisé en traitement du signal.

**Définition 4.** Soit $T \in \mathcal{L}\left(\ell_{N}\right)$ un opérateur stationnaire. On note $\delta=\epsilon_{0}$ le premier vecteur de la base canonique de $\ell_{N}$.
(i) $\delta$ est l'impulsion unitaire,
(ii) $w=T(\delta)$ est la réponse impulsionnelle de $T$, on parle de filtrage par $w$;
(iii) $\hat{w}=\mathcal{F}_{N}(w)$ est la fonction de transfert associé à l'opérateur $T$.

## 2 Filtrage en Traitement du Signal

### 2.1 Filtres Passe-haut, Passe-bas, Passe-bande

Les opérateurs stationnaires agissent sur les signaux via l'application d'un filtrage par convolution. Le filtre $w$ associé à un opérateur $T_{w}$ caractérise entièrement l'opérateur ( $w=T(\delta)$ il s'agit de la réponse impulsionnelle!). En traitement du signal, on caractérise les filtres par leur effet sur le spectre du signal. En effet pour un opérateur $T_{w}$ et un signal $z$ on a

$$
\mathcal{F}_{N}\left(T_{w}(z)\right)=\mathcal{F}_{N}(w * z)=\mathcal{F}_{N}(w) \mathcal{F}_{N}(z)=\hat{w} \hat{z}
$$

Les opérateurs stationnaires sont aussi appelés multiplicateurs de Fourier puisque c'est précisément l'opération qui est effectuée. On précise le vocabulaire utilisé en traitement du signal.

- Si $\hat{w}_{0}=0$ alors $T_{w}(z)$ a une moyenne nulle, on parle de filtrage à moyenne nulle;
- Si $\left|\hat{w}_{0}\right|=1$ alors $T_{w}$ conserve la moyenne de $z$, on parle de filtrage conservatif;

Soit $M \in\{0, \ldots, N / 2\}$ (on suppose que $N$ est pair).

- Si $\left|\hat{w}_{m}\right|>1$ pour $m \leqslant M$ et $\left|\hat{w}_{m}\right| \in[0,1[$ pour $m \geqslant M$ alors $T_{w}$ amplifie les basses fréquences et réduit les hautes fréquences. On parle de filtre passe-bas;
- Si $|\hat{h}(m)|>1$ pour $m \geqslant M$ et $|\hat{h}(m)| \in[0,1[$ pour $m \leqslant M$ alors $T$ amplifie les hautes fréquences et réduit les basses fréquences. On parle de filtre passe-haut;
- Si $|\hat{h}(m)|>1$ pour des valeurs intermédiaires de $m$ alors $T$ amplifie les fréquences moyennes. On parle de filtre passe-bande;
- Si $|\hat{h}(m)|>1$ pour tout valeur de $m$ alors $T$ est un amplificateur de fréquence.

### 2.2 Analyse Fréquentielle de Quelques Opérateurs

#### Opérateurs de Dérivée Discrets

Dans cette section on analyse deux opérateurs stationnaires qui représentent la version discrète des dérivées première et seconde. On verra qu'il s'agit de filtres passe-hauts.

**Définition 5 (Opérateurs de dérivée discrets).** L'opérateur de dérivée première discret est

$$
\begin{aligned}
D_{1}: & \ell_{N} \longrightarrow \ell_{N} \\
& z \longmapsto D_{1}(z)=\left(z_{n+1}-z_{n}\right)_{n \in \mathbb{Z}}
\end{aligned}
$$

On définit l'opérateur de dérivée p-ième discret par $D_{p}=R_{\left[\frac{p}{2}\right]} \circ D_{1}^{p}=R_{\left[\frac{p}{2}\right]} \circ D_{1} \circ \cdots \circ D_{1}$. En particulier l'opérateur de dérivée seconde discret est

$$
\begin{aligned}
D_{2}: & \ell_{N} \longrightarrow \ell_{N} \\
& z \longmapsto D_{2}(z)=\left(z_{n+1}-2 z_{n}+z_{n-1}\right)_{n \in \mathbb{Z}}
\end{aligned}
$$

**Remarque 1.** L'opérateur de translation est nécessaire pour recentrer les dérivées d'ordre impaires en $n$. En effet, pour la dérivée seconde on a

$$
D_{1} \circ D_{1}(z)_{n}=D_{1}(z)_{n+1}-D_{1}(z)_{n}=z_{n+2}-z_{n+1}-\left(z_{n+1}-z_{n}\right)=z_{n+2}-2 z_{n+1}+z_{n}
$$

Le résultat est symétrique par rapport à $z_{n+1}$ mais on préfère que cette symétrie soit centré en $z_{n}$. D'où l'ajout de l'opérateur de translation $R_{1}$.

On a les propositions suivantes qui donnent les matrices et les spectres des opérateurs de dérivée première et seconde.

**Proposition 3 (Caractérisation de l'opérateur de dérivée première discret).** La réponse impulsionnelle de $D_{1}$ est $w_{1}=D_{1}(\delta)=(-1,0, \ldots, 0,1)$. La matrice de $D_{1}$ est

$$
A_{D_{1}}=\left(\begin{array}{ccccc}
-1 & 1 & 0 & \ldots & 0 \\
0 & -1 & 1 & \ldots & 0 \\
\vdots & & \ddots & \ddots & \vdots \\
0 & 0 & \ldots & -1 & 1 \\
1 & 0 & \ldots & 0 & -1
\end{array}\right)
$$

Enfin le spectre de $w_{1}$ est définie pour tout $m \in \mathbb{Z}$ par

$$
\hat{w}_{1, m}=2 \mathrm{i} e^{\mathrm{i} \pi \frac{m}{N}} \sin \left(\frac{\pi m}{N}\right)
$$

**Démonstration.**

$$
\begin{aligned}
T :
&\ell_N \to \ell_N\\
& z \mapsto (z_{n+1} - z_n)_n
\end{aligned}
$$

Réponse impulsionnelle $e_0 = (1,0,\dots,0)$

$$
\begin{aligned}
\omega_n &= T(\delta)_n = T(e_0)_n \\
         &= e_{0,n+1} - e_{0,1} \\
         &= \begin{cases}
            -1, & \text{si } n \equiv 0 \mod N \\
            1,  & \text{si } n \equiv -1 \mod N = N-1 \mod N \\
            0,  & \text{sinon}
            \end{cases} \\
         &= (-1, 0, \dots, 0, 1)
\end{aligned}
$$

D'où la matrice de $T$ grâce au Th.2.

Calcul du spectre de $\omega$

$$
\begin{aligned}
\hat{\omega}_n &= \mathcal{F_N}(\omega)_n \\
               &= \sum_{k=0}^{N-1} \omega_k e^{-\frac{2i\pi kn}{N}} \\
               &= -1 + 1 \cdot e^{-\frac{2i\pi (N-1) n}{N}} \\
               &= e^{-\frac{2i\pi n}{N} - 2i \pi n} - 1 \\
               &= e^{-\frac{i\pi n}{N}} \left(e^{-\frac{i\pi n}{N}} - e^{\frac{i\pi n}{N}}\right) \\
               &= e^{-\frac{i\pi n}{N}} \cdot 2i \sin \left(\frac{\pi n}{N}\right)
\end{aligned}
$$

Donc,

$$
\forall n \in [0, N-1], \quad \hat{\omega}_n = -2i e^{-\frac{i\pi n}{N}} \sin \left(\frac{\pi n}{N}\right)
$$

**Proposition 4 (Caractérisation de l'opérateur de dérivée seconde discret).** La réponse impulsionnelle de $D_{2}$ est $w_{2}=D_{2}(\delta)=(2,-1, \ldots, 0,1)$. La matrice de $D_{2}$ est

$$
A_{D_{2}}=\left(\begin{array}{ccccc}
-2 & 1 & 0 & \ldots & 1 \\
1 & -2 & 1 & \ldots & 0 \\
\vdots & & \ddots & \ddots & \vdots \\
0 & 0 & \ldots & -2 & 1 \\
1 & 0 & \ldots & 1 & -2
\end{array}\right)
$$

Enfin le spectre de $w_{2}$ est définie pour tout $m \in \mathbb{Z}$ par

$$
\bar{w}_{2, m}=-4 \sin ^{2}\left(\frac{\pi m}{N}\right)
$$

**Démonstration.** Voir cours manuscrit.

Le tableau 1 résume les propriétés des opérateurs de dérivée première et seconde discrets. Dans les deux cas il s'agit d'un filtre passe-haut. Le filtre de la dérivée seconde amplifie plus les hautes-fréquences que celui de la dérivée première. Il coupe également plus franchement les faibles fréquences grâce à une convergence vers 0 plus rapide (voir figure 1).

| Propriété | Dérivée première $D_{1}$ | Dérivée seconde $D_{2}$ |
| :--: | :--: | :--: |
| $\left\|\dot{w}_{0}\right\|$ | 0 (moyenne nulle) | 0 (moyenne nulle) |
| $\left\|\dot{w}_{S}\right\|$ | 2 | 4 |
| $\left\|\dot{w}_{m}\right\|$ pour $m \neq \frac{N}{2}$ | $<2$ | $<4$ |
| $\left\|\dot{w}_{m}\right\|$ quand $m \rightarrow 0$ | $\rightarrow 0$ (lente) | $\rightarrow 0$ (rapide) |

**Table 1.** Comparaison des propriétés des opérateurs $T_{1}$ et $T_{2}$

![Figure 1](data:image/png;base64,...)

**Figure 1.** Spectres d'amplitude des opérateurs de dérivée première et seconde pour $N=32$, tracé sur $\{0, \ldots, 16\}$.
