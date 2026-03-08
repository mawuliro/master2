# Modélisation des Propriétés Mécaniques des Matériaux Composites
# Modelling of the Mechanical Properties of Composite Materials

**Auteur / Author:** HOUNKPE Mawulikplimi Roland  
**Formation / Degree:** Master — Physique Théorique, Université de Lomé (2023–2025)  
**Directeur / Supervisor:** Dr. Ayodele Adessina (Cerema – Université Gustave Eiffel)  
**Co-directeur / Co-supervisor:** Prof. Kokou N'Wuitcha (Université de Lomé)

---

## Table des matières / Table of Contents

- [Description du projet / Project Description](#description)
- [Objectif du mémoire / Thesis Objective](#objectif)
- [Structure du mémoire / Thesis Structure](#structure)
- [Organisation des notebooks / Notebook Organization](#notebooks)
- [Bibliothèque echoes / The echoes Library](#echoes)
- [Paramètres globaux / Global Parameters](#parametres)
- [Note sur les résultats / Note on Results](#note)
- [Résultats principaux / Key Results](#resultats)
- [Dépendances / Dependencies](#dependances)
- [Références / References](#references)

---

## Description du projet / Project Description <a name="description"></a>

**[FR]**  
Ce projet constitue le support numérique du mémoire de Master en Physique Théorique. Il
regroupe trois notebooks Jupyter qui implémentent l'homogénéisation analytique de
matériaux composites selon le schéma de Mori–Tanaka, via la bibliothèque Python
`echoes`. Les simulations portent sur trois configurations de volumes élémentaires
représentatifs (VER) de complexité croissante, et permettent de conduire des études
paramétriques systématiques reliant microstructure et propriétés élastiques effectives.

**[EN]**  
This project is the numerical support for a Master's thesis in Theoretical Physics. It
contains three Jupyter notebooks implementing analytical homogenization of composite
materials using the Mori–Tanaka scheme, via the Python library `echoes`. Simulations
cover three representative volume element (RVE) configurations of increasing complexity,
enabling systematic parametric studies linking microstructure to effective elastic
properties.

---

## Objectif du mémoire / Thesis Objective <a name="objectif"></a>

**[FR]**  
L'objectif est double :

1. **S'approprier le formalisme micromécanique** en élasticité linéaire isotrope — en
   s'appuyant sur la solution d'Eshelby (1957), les tenseurs de localisation, le schéma
   de Mori–Tanaka et le modèle analytique de Hervé–Zaoui pour les inclusions
   multicouches.

2. **Conduire des études paramétriques numériques** sur trois configurations de
   microstructures, afin de quantifier l'influence de chaque paramètre microstructural
   (fraction volumique, contraste de module, forme des inclusions, épaisseur et rigidité
   de l'interphase) sur les propriétés élastiques effectives du composite.

L'enjeu n'est pas de reproduire des résultats connus, mais de **dégager des règles de
conception exploitables** à partir d'une analyse paramétrique rigoureuse.

**[EN]**  
The objective is twofold:

1. **Master the micromechanical formalism** in isotropic linear elasticity — building on
   the Eshelby solution (1957), localization tensors, the Mori–Tanaka scheme, and the
   Hervé–Zaoui analytical model for multi-layer inclusions.

2. **Conduct systematic numerical parametric studies** on three microstructural
   configurations, quantifying the influence of each microstructural parameter (volume
   fraction, modulus contrast, inclusion shape, interphase thickness and stiffness) on
   the effective elastic properties.

The aim is not to reproduce known results, but to **derive actionable design rules**
from a rigorous parametric analysis.

---

## Structure du mémoire / Thesis Structure <a name="structure"></a>

Le mémoire est rédigé en LaTeX (`1-RAPPORT_ROLAND.tex`) et organisé comme suit :

The thesis is written in LaTeX (`1-RAPPORT_ROLAND.tex`) and organized as follows:

```
Introduction générale
│
├── Chapitre 1 — Recherche bibliographique
│   ├── Généralités sur les matériaux composites
│   ├── Méthodes de modélisation (analytique, numérique, expérimentale)
│   ├── Micromécanique et homogénéisation (VER, Voigt, Reuss)
│   ├── Élasticité linéaire, isotropie, notations de Kelvin–Mandel
│   ├── Le problème d'Eshelby (inclusion + inhomogénéité)
│   └── Schémas d'homogénéisation : dilué, auto-cohérent, Mori–Tanaka
│
├── Chapitre 2 — Modélisation des propriétés effectives
│   ├── VER à inclusions sphériques simples
│   ├── VER à inclusions composites (bicouches)
│   ├── VER à inclusions mixtes (simples + composites)
│   └── Formulation du problème à n couches : modèle d'Hervé–Zaoui
│       ├── Chargement hydrostatique → k_eff  (matrices de transfert)
│       └── Chargement déviatorique  → μ_eff  (équation quadratique)
│
├── Chapitre 3 — Résultats et Discussions
│   ├── VER 1 : Inclusions sphériques simples
│   │   ├── Effet de la fraction volumique
│   │   ├── Effet du contraste de module
│   │   └── Effet de la forme (oblate / sphère / prolate)
│   ├── VER 2 : Inclusions composites (bicouches)
│   │   ├── Influence de la fraction volumique
│   │   ├── Influence du contraste entre phases
│   │   └── Influence de l'épaisseur de l'interphase (paramètre ε)
│   └── VER 3 : Inclusions mixtes
│       ├── Effet des fractions volumiques
│       ├── Effet des contrastes de module (C1 → C4)
│       ├── Effet de la forme de l'inclusion simple
│       └── Couplage forme–épaisseur d'interphase
│
└── Conclusion générale
```

---

## Organisation des notebooks / Notebook Organization <a name="notebooks"></a>

Le projet contient **trois notebooks Jupyter**, chacun correspondant à un VER du
mémoire. Ils sont indépendants et peuvent être exécutés dans n'importe quel ordre.

The project contains **three Jupyter notebooks**, each corresponding to one RVE in
the thesis. They are independent and can be run in any order.

```
.
├── ver_simple_spherique.ipynb     # VER 1 : inclusions sphériques simples
├── ver_composite.ipynb            # VER 2 : inclusions composites bicouches
├── ver_mixte.ipynb                # VER 3 : inclusions mixtes
├── 1-RAPPORT_ROLAND.tex           # Mémoire complet en LaTeX
└── README.md                      # Ce fichier / This file
```

---

### `ver_simple_spherique.ipynb` — VER à inclusions simples / Simple Inclusions RVE

**[FR]** Configuration la plus élémentaire : une matrice homogène ($E_m = 10$ GPa,
$\nu = 0.2$) contenant des inclusions sphéroïdales de module $E_i$ et de fraction
volumique $f_i$. Le schéma de Mori–Tanaka est appliqué directement.

**[EN]** The most elementary configuration: a homogeneous matrix ($E_m = 10$ GPa,
$\nu = 0.2$) containing spheroidal inclusions of modulus $E_i$ and volume fraction
$f_i$. The Mori–Tanaka scheme is applied directly.

| Section | Paramètres variés | Paramètres fixes |
|---|---|---|
| Fraction volumique | $f_i \in [0, 0.6]$, $E_i \in \{5,10,20,50\}$ GPa | sphère ($\omega=1$) |
| Contraste de module | $E_i/E_m \in [0.1, 5]$ | $f_i \in \{0.3,0.4,0.5,0.6\}$ |
| Forme (contrasté) | $\omega \in [0.1, 10]$ (log) | $E_i = 70$ GPa |
| Forme (neutre / validation) | $\omega \in [0.1, 10]$ (log) | $E_i = E_m = 10$ GPa |

**Figures générées :**
```
module_young_effectif_mori_tanaka.png  /  compressibilite_effectif_mori_tanaka.png
cisaillement_effectif_mori_tanaka.png
effet_contraste_E.png / _K.png / _mu.png
effet_forme_E.png / _K.png / _mu.png
effet_forme_E_id.png / _K_id.png / _mu_id.png
```

---

### `ver_composite.ipynb` — VER à inclusions bicouches / Two-Layer Inclusions RVE

**[FR]** Configuration intermédiaire : des inclusions composites sphériques à deux
couches (cœur $E_1$ + interphase $E_2$) plongées dans la matrice ($E_m = 10$ GPa,
$\nu = 0.1$). Le modèle de Hervé–Zaoui est d'abord appliqué à l'inclusion pour
calculer son tenseur de rigidité effectif $\mathbb{C}_{\text{inc}}^{\text{eff}}$, qui
est ensuite traité comme une inclusion homogène dans le schéma de Mori–Tanaka.

Géométrie de référence : $R_1 = 1.8$, $R_2 = 2.0$
→ fraction cœur $\approx 72.9\%$, fraction interphase $\approx 27.1\%$.

**[EN]** Intermediate configuration: composite spherical inclusions with two layers
(core $E_1$ + interphase $E_2$) in the matrix ($E_m = 10$ GPa, $\nu = 0.1$). The
Hervé–Zaoui model is first applied to compute the effective stiffness tensor
$\mathbb{C}_{\text{inc}}^{\text{eff}}$, which is then treated as a homogeneous
inclusion in the Mori–Tanaka scheme.

Reference geometry: $R_1 = 1.8$, $R_2 = 2.0$
→ core fraction $\approx 72.9\%$, interphase fraction $\approx 27.1\%$.

| Section | Paramètres variés | Paramètres fixes |
|---|---|---|
| Fraction vol. — cas 1 (interphase rigide) | $f_i \in [0,0.6]$, $E_1 \in \{5,10,20,50\}$ GPa | $E_2 = 15$ GPa |
| Fraction vol. — cas 2 (interphase neutre) | $f_i \in [0,0.6]$, $E_1 \in \{5,10,20,50\}$ GPa | $E_2 = 10$ GPa |
| Fraction vol. — cas 3 (interphase souple) | $f_i \in [0,0.6]$, $E_1 \in \{5,10,20,50\}$ GPa | $E_2 = 5$ GPa |
| Contraste $E_1/E_m$ | $E_1/E_m \in [0.1,5]$, $f_i \in \{0.3…0.6\}$ | $E_2 = 15$ GPa |
| Contraste $E_2/E_m$ | $E_2/E_m \in [0,10]$ | $E_1 = E_m$ (cœur neutre) |
| Gradient interne $E_2/E_1$ | $E_2/E_1 \in [0,5]$ | $E_1 = 10$ GPa |
| Épaisseur ε — fraction | $\varepsilon/R_2 \in [0,1]$, $f_i \in \{0.3…0.6\}$ | $E_1=50$, $E_2=15$ GPa |
| Épaisseur ε — contraste $E_1$ | $\varepsilon/R_2 \in [0,1]$, $E_1 \in \{5,10,20,50\}$ GPa | $f_i=0.5$, $E_2=15$ GPa |
| Épaisseur ε — contraste $E_2$ | $\varepsilon/R_2 \in [0,1]$, $E_2 \in \{5,10,20,50\}$ GPa | $f_i=0.5$, $E_1=20$ GPa |

**Figures générées :**
```
bicouche_E/K/mu_1.png / _2.png / _3.png
cas1_E1_Em_E/K/mu.png  |  cas2_E2_Em_E/K/mu.png  |  cas3_E2_E1_E/K/mu.png
eps_fi_E/K/mu.png  |  eps_ctE1_E/K/mu.png  |  eps_ctE2_E/K/mu.png
```

---

### `ver_mixte.ipynb` — VER à inclusions mixtes / Mixed Inclusions RVE

**[FR]** Configuration la plus complexe : deux populations coexistent dans la même
matrice ($E_m = 10$ GPa, $\nu = 0.2$) — des inclusions simples sphéroïdales (module
$E_s$, fraction $f_s$, rapport d'aspect $\omega$) et des inclusions composites
bicouches (cœur $E_c$, interphase $E_{sh}$, fraction $f_c$). Hervé–Zaoui est appliqué
en amont pour homogénéiser chaque inclusion composite, puis les deux populations sont
traitées conjointement par Mori–Tanaka.

**[EN]** The most complex configuration: two populations coexist in the same matrix
($E_m = 10$ GPa, $\nu = 0.2$) — simple spheroidal inclusions (modulus $E_s$, fraction
$f_s$, aspect ratio $\omega$) and two-layer composite inclusions (core $E_c$,
interphase $E_{sh}$, fraction $f_c$). Hervé–Zaoui is applied upstream to homogenize
each composite inclusion; both populations are then processed jointly by Mori–Tanaka.

| Section | Description |
|---|---|
| Fractions — étude 1 | $f_s = f_c \in [0, 0.3]$, 4 combinaisons de contrastes |
| Fractions — étude 2 | $f_s \in [0, 0.5]$, $f_c = 0.10$ fixe |
| Fractions — étude 3 | $f_c \in [0, 0.5]$, $f_s = 0.10$ fixe |
| Contraste C1 | $E_s/E_m$ varie, inclusions composites neutres |
| Contraste C2 | $E_c/E_m$ varie, inclusion simple et interphase neutres |
| Contraste C3 | $E_{sh}/E_m$ varie, inclusion simple et cœur neutres |
| Contraste C4 | $E_{sh}/E_c$ varie (gradient interne), inclusion simple neutre |
| Forme — cas 1 | $\omega \in [0.1,10]$, $E_s=E_c=50$ GPa, $E_{sh}=15$ GPa |
| Forme — cas 2 | $\omega \in [0.1,10]$, $E_s=20$, $E_c=50$, $E_{sh}=15$ GPa |
| Forme — cas 3 | $\omega \in [0.1,10]$, $E_s=50$, $E_c=20$, $E_{sh}=15$ GPa |
| ε + forme — cas 1 | $\varepsilon/R_2 \in [0,1]$, 5 valeurs de $\omega$, $E_s=E_c=50$ GPa |
| ε + forme — cas 2 | $\varepsilon/R_2 \in [0,1]$, 5 valeurs de $\omega$, $E_s=50$, $E_c=20$ GPa |
| ε + forme — cas 3 | $\varepsilon/R_2 \in [0,1]$, 5 valeurs de $\omega$, $E_s=30$, $E_c=50$ GPa |

Chaque étude de forme et chaque étude ε inclut un **cas de validation** ($E_s = E_m$) :
les cinq courbes de forme doivent se superposer, confirmant l'absence de couplage
parasite entre les deux leviers.

Each shape and ε study includes a **validation case** ($E_s = E_m$): the five shape
curves must overlap, confirming no spurious coupling between the two levers.

**Figures générées :**
```
et1/2/3_E/K/mu.png
C1_A/B_E/K/mu.png  ...  C4_A/B_E/K/mu.png
forme_A/B_E/K/mu.png (3 jeux)
eps_forme_E/K/mu.png + eps_forme_neutre_E/mu.png (3 jeux, validation)
```

---

## Bibliothèque echoes / The echoes Library <a name="echoes"></a>

**`echoes`** (*Extended Calculator of HOmogEnization Schemes*) est une bibliothèque
Python développée par Jean-François Barthélémy (Cerema – Université Gustave Eiffel),
directeur de ce mémoire. Son noyau est écrit en C++ et exposé via une interface Python.
Elle supporte l'élasticité linéaire, la conduction, la viscoélasticité et
l'homogénéisation non linéaire.

**`echoes`** is a Python library developed by Jean-François Barthélémy (Cerema –
Université Gustave Eiffel), the thesis supervisor. Its core is written in C++ and
exposed through a Python interface. It supports linear elasticity, conductivity,
viscoelasticity and nonlinear homogenization.

- **Documentation / Manuel :** [https://jfbarthelemy.github.io/echoes](https://jfbarthelemy.github.io/echoes)
- **DOI :** [10.5281/zenodo.14959866](https://doi.org/10.5281/zenodo.14959866)

**Installation :**
```bash
# 1. Télécharger le fichier .whl approprié depuis le lien DOI ci-dessus
# 2. Installer via pip :
pip install -U echoes-XYZ.whl   # remplacer par le nom exact du fichier
```

**Fonctions principales utilisées dans ce projet / Main functions used:**

| Fonction | Rôle |
|---|---|
| `stiff_Enu(E, nu)` | Construit le tenseur de rigidité isotrope depuis $E$ et $\nu$ |
| `sphere(C0)` | Tenseur de Hill pour inclusion sphérique |
| `spheroidal(C0, omega)` | Tenseur de Hill pour inclusion sphéroïdale de rapport $\omega$ |
| `sphere_nlayers(radii, stiffs)` | Modèle Hervé–Zaoui : inclusion sphérique à $n$ couches |
| `rve(C0)` | Crée un VER avec matrice $\mathbb{C}_0$ |
| `ellipsoid(C_i, P, f)` | Ajoute une phase d'inclusion au VER |
| `homogenize(MT)` | Calcule le tenseur effectif par Mori–Tanaka |

---

## Paramètres globaux / Global Parameters <a name="parametres"></a>

Tous les notebooks partagent les mêmes conventions de base :

| Paramètre | Valeur |
|---|---|
| Module de la matrice | $E_m = 10$ GPa |
| Coefficient de Poisson (VER 1 & 3) | $\nu = 0.2$ |
| Coefficient de Poisson (VER 2) | $\nu = 0.1$ |
| Fraction volumique max | $f_i \leq 0.6$ |
| Dimensions des figures | $(9, 6)$ pouces |
| Couleurs | `['blue', 'green', 'black', 'red']` |
| Marqueurs | `['o', 's', '^', 'D']` |

**Configuration matplotlib commune :**
```python
plt.rcParams.update({
    "axes.linewidth": 2,      "axes.labelsize": 16,    "axes.labelweight": "bold",
    "xtick.labelsize": 12,    "ytick.labelsize": 12,
    "xtick.major.width": 1.5, "ytick.major.width": 1.5
})
```

---

## Note sur les résultats / Note on Results <a name="note"></a>

**[FR]** Dans le mémoire, **seul le module de Young effectif $\tilde{E}$ est commenté
et analysé** dans le corps du texte. Les modules de compressibilité $\tilde{k}$ et de
cisaillement $\tilde{\mu}$ sont calculés et tracés par les notebooks pour chaque étude
paramétrique (trois figures sont systématiquement produites : $\tilde{E}$, $\tilde{k}$,
$\tilde{\mu}$), mais leur analyse détaillée n'est pas développée dans le rapport. Ces
figures sont disponibles comme données complémentaires. Ce choix repose sur le fait que
les trois modules sont liés par :

$$\tilde{E} = \frac{9\,\tilde{k}\,\tilde{\mu}}{3\,\tilde{k} + \tilde{\mu}}$$

Connaître l'évolution de $\tilde{E}$ suffit donc à comprendre le comportement global,
les tendances observées sur $\tilde{k}$ et $\tilde{\mu}$ étant cohérentes avec celles
de $\tilde{E}$.

**[EN]** In the thesis, **only the effective Young's modulus $\tilde{E}$ is commented
and analysed** in the main text. The bulk modulus $\tilde{k}$ and shear modulus
$\tilde{\mu}$ are computed and plotted by the notebooks for every parametric study
(three figures are systematically produced: $\tilde{E}$, $\tilde{k}$, $\tilde{\mu}$),
but their detailed analysis is not developed in the report. These figures are available
as supplementary data. This choice is justified by the fact that tracking $\tilde{E}$
is sufficient to understand the global behaviour, the trends in $\tilde{k}$ and
$\tilde{\mu}$ being consistent with those in $\tilde{E}$.

---

## Résultats principaux / Key Results <a name="resultats"></a>

**[FR]**

**VER 1 — Inclusions sphériques simples**
- La fraction volumique amplifie l'effet du contraste de module, de manière non linéaire.
- La sphère ($\omega = 1$) est paradoxalement la géométrie *la moins efficace* : son
  tenseur d'Eshelby isotrope disperse la perturbation uniformément sans privilégier
  aucun mode de transfert de charge.
- En l'absence de contraste ($E_i = E_m$), la forme n'a aucun effet sur $\tilde{E}$,
  quelle que soit $f_i$ — ce cas sert de test de cohérence du modèle.

**VER 2 — Inclusions composites bicouches**
- L'interphase périphérique (~27% du volume) exerce une influence sur $\tilde{E}$
  supérieure à celle du cœur (~73%), car elle est en contact direct avec la matrice
  et conditionne tout transfert de charge.
- Le signe du gradient interne $E_1 - E_2$ détermine la monotonie de $\tilde{E}$ avec
  l'épaisseur de l'interphase : croissante si $E_1 > E_2$, décroissante si $E_1 < E_2$.
- La conception doit cibler la couche périphérique pour optimiser l'efficacité
  mécanique de l'inclusion composite.

**VER 3 — Inclusions mixtes**
- À fraction volumique identique, l'inclusion simple est *toujours* plus efficace que
  l'inclusion composite : l'interphase filtre le signal mécanique du cœur avant qu'il
  n'atteigne la matrice.
- La hiérarchie interne de l'inclusion composite (interphase > cœur) est robuste et
  retrouvée intacte dans le contexte mixte.
- La forme de l'inclusion simple et l'épaisseur de l'interphase composite sont des
  leviers **additifs et indépendants** : ils peuvent être optimisés séparément sans
  que l'un n'invalide les conclusions tirées sur l'autre.

**[EN]**

**RVE 1 — Simple spherical inclusions**
- Volume fraction amplifies the modulus contrast effect, in a non-linear manner.
- The sphere ($\omega = 1$) is paradoxically the *least efficient* geometry: its
  isotropic Eshelby tensor distributes the perturbation uniformly without favouring
  any load-transfer mode.
- In the absence of contrast ($E_i = E_m$), shape has no effect on $\tilde{E}$ for
  any $f_i$ — this case serves as an internal consistency test.

**RVE 2 — Two-layer composite inclusions**
- The peripheral interphase (~27% of volume) exerts a greater influence on $\tilde{E}$
  than the core (~73%), as it is in direct contact with the matrix and governs all load
  transfer.
- The sign of the internal gradient $E_1 - E_2$ controls the monotonicity of $\tilde{E}$
  with interphase thickness: increasing if $E_1 > E_2$, decreasing if $E_1 < E_2$.
- Design should target the peripheral layer to optimize the mechanical efficiency of
  the composite inclusion.

**RVE 3 — Mixed inclusions**
- At equal volume fraction, the simple inclusion is *always* more efficient than the
  composite inclusion: the interphase filters the core's mechanical signal before it
  reaches the matrix.
- The internal hierarchy of the composite inclusion (interphase > core) is structural
  and is recovered intact in the mixed context.
- The shape of the simple inclusion and the interphase thickness of the composite
  inclusion are **additive and independent** levers: they can be optimised sequentially
  without one invalidating conclusions drawn on the other.

---

## Dépendances / Dependencies <a name="dependances"></a>

```
Python    >= 3.8
echoes              (voir section Bibliothèque echoes pour l'installation)
numpy
matplotlib
jupyter
```

---

## Références / References <a name="references"></a>

- **Eshelby, J.D. (1957)** — The determination of the elastic field of an ellipsoidal
  inclusion, and related problems. *Proc. R. Soc. London A*, 241, 376–396.
- **Mori, T. & Tanaka, K. (1973)** — Average stress in matrix and average elastic
  energy of materials with misfitting inclusions. *Acta Metallurgica*, 21(5), 571–574.
- **Hervé, E. & Zaoui, A. (1993)** — n-layered inclusion-based micromechanical
  modelling. *Int. J. Eng. Sci.*, 31(1), 1–10.
- **Barthélémy, J.-F. (2022)** — *echoes: Extended Calculator of HOmogEnization
  Schemes*. Zenodo.
  [https://doi.org/10.5281/zenodo.14959866](https://doi.org/10.5281/zenodo.14959866) —
  [Documentation en ligne](https://jfbarthelemy.github.io/echoes)