<div align="center">

# Modélisation des Propriétés Mécaniques des Matériaux Composites

**HOUNKPE Mawulikplimi Roland**
*Master Physique Théorique · Université de Lomé · 2023–2025*

[![Directeur](https://img.shields.io/badge/Directeur-Dr.%20A.%20Adessina%20%28Cerema–UGE%29-1a3a5c?style=flat-square)](https://jfbarthelemy.github.io/echoes)
[![Co-directeur](https://img.shields.io/badge/Co--directeur-Prof.%20K.%20N%27Wuitcha%20%28UL%29-2a4a35?style=flat-square)](#)
[![echoes](https://img.shields.io/badge/Library-echoes-b8922a?style=flat-square&logo=python&logoColor=white)](https://jfbarthelemy.github.io/echoes)
[![Jupyter](https://img.shields.io/badge/Notebooks-3%20Jupyter-orange?style=flat-square&logo=jupyter&logoColor=white)](#)
[![LaTeX](https://img.shields.io/badge/Rapport-LaTeX-c0392b?style=flat-square&logo=latex&logoColor=white)](#)

*Homogénéisation analytique · Mori–Tanaka · Hervé–Zaoui · VER de complexité croissante*

</div>

---

# 🇫🇷 Version Française

---

## Table des matières

- [01 · Description du projet](#01--description-du-projet)
- [02 · Objectif du mémoire](#02--objectif-du-mémoire)
- [03 · Structure du mémoire](#03--structure-du-mémoire)
- [04 · Organisation des notebooks](#04--organisation-des-notebooks)
- [05 · Bibliothèque echoes](#05--bibliothèque-echoes)
- [06 · Paramètres globaux](#06--paramètres-globaux)
- [07 · Note sur les résultats](#07--note-sur-les-résultats)
- [08 · Résultats principaux](#08--résultats-principaux)
- [09 · Références](#09--références)

---

## 01 · Description du projet

Ce projet est le support numérique d'un mémoire de Master en **Physique Théorique**.
Il regroupe **3 notebooks Jupyter** implémentant l'homogénéisation analytique de matériaux composites via la bibliothèque Python `echoes`, selon le schéma de **Mori–Tanaka**.

Les simulations couvrent **trois configurations de VER** (Volume Élémentaire Représentatif) de complexité croissante, permettant des études paramétriques systématiques reliant microstructure et propriétés élastiques effectives.

```
.
├── ver_simple_spherique.ipynb   ← VER 1 : inclusions sphéroïdales simples
├── ver_composite.ipynb          ← VER 2 : inclusions composites bicouches
├── ver_mixte.ipynb              ← VER 3 : inclusions mixtes (2 populations)
├── 1-RAPPORT_ROLAND.tex         ← Mémoire complet (LaTeX)
└── README.md
```

---

## 02 · Objectif du mémoire

> *L'enjeu n'est pas de reproduire des résultats connus, mais de dégager des **règles de conception exploitables** à partir d'une analyse paramétrique rigoureuse.*

| # | Axe | Description |
|:-:|:---|:---|
| **01** | **Formalisme** | Maîtriser le cadre micromécanique en élasticité linéaire isotrope — solution d'Eshelby (1957), tenseurs de localisation, schéma Mori–Tanaka, modèle Hervé–Zaoui pour inclusions multicouches |
| **02** | **Paramétrique** | Quantifier l'influence de chaque paramètre microstructural (fraction volumique, contraste de module, forme, épaisseur et rigidité d'interphase) sur les propriétés élastiques effectives |

---

## 03 · Structure du mémoire

> Rédigé en LaTeX — fichier `1-RAPPORT_ROLAND.tex`

```
1-RAPPORT_ROLAND.tex
│
├── Introduction générale
│
├── Chapitre 1 ── Recherche bibliographique
│   ├── Matériaux composites       (historique · constituants · applications industrielles)
│   ├── Méthodes de modélisation   (analytique · FEM · FFT · expérimental)
│   ├── Micromécanique             (VER · Voigt · Reuss · lemme Hill–Mandel)
│   ├── Élasticité linéaire        (isotropie · notation Kelvin–Mandel)
│   ├── Problème d'Eshelby         (inclusion + inhomogénéité · tenseur de Hill P)
│   └── Schémas d'homogénéisation  (dilué · auto-cohérent · Mori–Tanaka)
│
├── Chapitre 2 ── Modélisation des propriétés effectives
│   ├── VER à inclusions sphériques simples
│   ├── VER à inclusions composites bicouches
│   ├── VER à inclusions mixtes
│   └── Modèle Hervé–Zaoui à n couches
│       ├── Chargement hydrostatique ──→ k_eff   (matrices de transfert)
│       └── Chargement déviatorique  ──→ mu_eff  (équation quadratique)
│
├── Chapitre 3 ── Résultats & Discussions
│   ├── VER 1 · fraction vol. · contraste · forme (oblate / sphère / prolate)
│   ├── VER 2 · fraction vol. · contraste · épaisseur interphase ε
│   └── VER 3 · fractions · contrastes C1–C4 · forme · couplage forme–ε
│
└── Conclusion générale
```

---

## 04 · Organisation des notebooks

Les trois notebooks sont **indépendants** — exécutables dans n'importe quel ordre.

---

### `ver_simple_spherique.ipynb` — VER 1 · Inclusions sphéroïdales simples

Matrice homogène + inclusions de module Ei. **Mori–Tanaka appliqué directement.**
Géométrie : sphère (ω = 1) ou sphéroïde de rapport d'aspect ω = a/c.

| Étude | Paramètre(s) varié(s) | Paramètre(s) fixe(s) |
|:---|:---|:---|
| Fraction volumique | fi ∈ [0, 0.6] · Ei ∈ {5, 10, 20, 50} GPa | ω = 1 (sphère) |
| Contraste de module | Ei/Em ∈ [0.1, 5] | fi ∈ {0.3, 0.4, 0.5, 0.6} |
| Forme — contrasté | ω ∈ [0.1, 10] (log) | Ei = 70 GPa |
| Forme — validation | ω ∈ [0.1, 10] (log) | Ei = Em = 10 GPa |

<details>
<summary>📁 Figures générées</summary>

```
module_young_effectif_mori_tanaka.png
compressibilite_effectif_mori_tanaka.png
cisaillement_effectif_mori_tanaka.png
effet_contraste_E.png / _K.png / _mu.png
effet_forme_E.png / _K.png / _mu.png
effet_forme_E_id.png / _K_id.png / _mu_id.png    ← validation (Ei = Em)
```
</details>

---

### `ver_composite.ipynb` — VER 2 · Inclusions composites bicouches

Inclusions sphériques composites : **cœur** E1 + **interphase** E2.
Pipeline : **Hervé–Zaoui** → C_inc_eff → **Mori–Tanaka**.

> **Géométrie de référence :** R1 = 1.8, R2 = 2.0
> → cœur ≈ **72.9 %** du volume · interphase ≈ **27.1 %**

| Étude | Paramètre(s) varié(s) | Paramètre(s) fixe(s) |
|:---|:---|:---|
| Fraction vol. — interphase rigide | fi ∈ [0, 0.6] · E1 ∈ {5, 10, 20, 50} GPa | E2 = 15 GPa |
| Fraction vol. — interphase neutre | fi ∈ [0, 0.6] · E1 ∈ {5, 10, 20, 50} GPa | E2 = 10 GPa |
| Fraction vol. — interphase souple | fi ∈ [0, 0.6] · E1 ∈ {5, 10, 20, 50} GPa | E2 = 5 GPa |
| Contraste E1/Em | E1/Em ∈ [0.1, 5] | E2 = 15 GPa |
| Contraste E2/Em | E2/Em ∈ [0, 10] | E1 = Em (cœur neutre) |
| Gradient interne E2/E1 | E2/E1 ∈ [0, 5] | E1 = 10 GPa |
| Épaisseur ε · fraction | ε/R2 ∈ [0, 1] · fi ∈ {0.3…0.6} | E1 = 50 GPa, E2 = 15 GPa |
| Épaisseur ε · contraste E1 | ε/R2 ∈ [0, 1] · E1 ∈ {5, 10, 20, 50} GPa | fi = 0.5, E2 = 15 GPa |
| Épaisseur ε · contraste E2 | ε/R2 ∈ [0, 1] · E2 ∈ {5, 10, 20, 50} GPa | fi = 0.5, E1 = 20 GPa |

<details>
<summary>📁 Figures générées</summary>

```
bicouche_E1.png / _K1.png / _mu1.png
bicouche_E2.png / _K2.png / _mu2.png
bicouche_E3.png / _K3.png / _mu3.png
cas1_E1_Em_E.png / _K.png / _mu.png
cas2_E2_Em_E.png / _K.png / _mu.png
cas3_E2_E1_E.png / _K.png / _mu.png
eps_fi_E.png / _K.png / _mu.png
eps_ctE1_E.png / _K.png / _mu.png
eps_ctE2_E.png / _K.png / _mu.png
```
</details>

---

### `ver_mixte.ipynb` — VER 3 · Inclusions mixtes (deux populations)

Deux populations coexistent dans la même matrice :
- **Inclusions simples** sphéroïdales : module Es, fraction fs, rapport d'aspect ω
- **Inclusions composites** bicouches : cœur Ec, interphase Esh, fraction fc

Pipeline : **Hervé–Zaoui** (par inclusion composite) → **Mori–Tanaka** (deux populations jointes).

| Étude | Description |
|:---|:---|
| Fractions 1 | fs = fc ∈ [0, 0.3] — les deux populations croissent ensemble |
| Fractions 2 | fs ∈ [0, 0.5], fc = 0.10 fixe |
| Fractions 3 | fc ∈ [0, 0.5], fs = 0.10 fixe |
| Contraste C1 | Es/Em varie · inclusions composites neutres |
| Contraste C2 | Ec/Em varie · inclusion simple et interphase neutres |
| Contraste C3 | Esh/Em varie · inclusion simple et cœur neutres |
| Contraste C4 | Esh/Ec varie (gradient interne) · inclusion simple neutre |
| Forme 1 | ω ∈ [0.1, 10] · Es = Ec = 50 GPa, Esh = 15 GPa |
| Forme 2 | ω ∈ [0.1, 10] · Es = 20, Ec = 50, Esh = 15 GPa |
| Forme 3 | ω ∈ [0.1, 10] · Es = 50, Ec = 20, Esh = 15 GPa |
| ε + forme 1 | ε/R2 ∈ [0, 1] · 5 valeurs ω · Es = Ec = 50 GPa |
| ε + forme 2 | ε/R2 ∈ [0, 1] · 5 valeurs ω · Es = 50, Ec = 20 GPa |
| ε + forme 3 | ε/R2 ∈ [0, 1] · 5 valeurs ω · Es = 30, Ec = 50 GPa |

> **Cas de validation :** chaque étude de forme et chaque étude ε inclut un cas Es = Em — les cinq courbes doivent se superposer parfaitement, confirmant l'absence de couplage parasite.

<details>
<summary>📁 Figures générées</summary>

```
et1_E.png / _K.png / _mu.png   ·   et2_...   ·   et3_...
C1_A_E.png / _K.png / _mu.png  ···  C4_B_...
forme_A_E.png / _K.png / _mu.png                 (3 jeux de contrastes)
eps_forme_E.png / _K.png / _mu.png               (3 jeux de contrastes)
eps_forme_neutre_E.png / _mu.png                 (3 jeux · cas validation)
```
</details>

---

## 05 · Bibliothèque echoes

> **`echoes`** — *Extended Calculator of HOmogEnization Schemes*
> Développée par **Jean-François Barthélémy** (Cerema – Université Gustave Eiffel), directeur de ce mémoire.
> Noyau **C++**, interface **Python**. Supporte : élasticité linéaire, conduction, viscoélasticité, homogénéisation non linéaire.

| Ressource | Lien |
|:---|:---|
| 📘 Documentation | [jfbarthelemy.github.io/echoes](https://jfbarthelemy.github.io/echoes) |
| 📦 DOI / Téléchargement | [10.5281/zenodo.14959866](https://doi.org/10.5281/zenodo.14959866) |

```bash
# 1. Télécharger le fichier .whl depuis le lien DOI ci-dessus
# 2. Installer :
pip install -U echoes-XYZ.whl
```

| Fonction | Rôle |
|:---|:---|
| `stiff_Enu(E, nu)` | Construit le tenseur de rigidité isotrope depuis E et ν |
| `sphere(C0)` | Tenseur de Hill — inclusion sphérique |
| `spheroidal(C0, omega)` | Tenseur de Hill — inclusion sphéroïdale de rapport ω |
| `sphere_nlayers(radii, stiffs)` | Modèle Hervé–Zaoui : inclusion sphérique à n couches concentriques |
| `rve(C0)` | Crée un VER avec matrice C0 |
| `ellipsoid(C_i, P, f)` | Ajoute une phase d'inclusion sphéroïdale au VER |
| `homogenize(MT)` | Calcule le tenseur effectif par le schéma Mori–Tanaka |

---

## 06 · Paramètres globaux

| Paramètre | Valeur |
|:---|:---|
| Module de la matrice | Em = 10 GPa |
| Coefficient de Poisson (VER 1 & 3) | ν = 0.2 |
| Coefficient de Poisson (VER 2) | ν = 0.1 |
| Fraction volumique maximale | fi ≤ 0.6 |
| Dimensions des figures | (9, 6) pouces |
| Couleurs | `blue` · `green` · `black` · `red` |
| Marqueurs | `o` · `s` · `^` · `D` |

```python
plt.rcParams.update({
    "axes.linewidth":     2,     "axes.labelsize":    16,    "axes.labelweight": "bold",
    "xtick.labelsize":   12,     "ytick.labelsize":   12,
    "xtick.major.width":  1.5,   "ytick.major.width":  1.5,
})
```

---

## 07 · Note sur les résultats

> ⚠️ **Dans le mémoire, seul le module de Young effectif Ẽ est commenté et analysé** dans le corps du texte.

Les notebooks calculent et tracent **trois modules** pour chaque étude paramétrique :

| Module | Commenté dans le rapport | Calculé + tracé |
|:---:|:---:|:---:|
| Ẽ — Young effectif | ✅ | ✅ |
| k̃ — Compressibilité effective | ❌ | ✅ |
| μ̃ — Cisaillement effectif | ❌ | ✅ |

Ce choix repose sur la relation : **Ẽ = 9 k̃ μ̃ / (3 k̃ + μ̃)**

Les tendances de k̃ et μ̃ étant cohérentes avec Ẽ, analyser ce dernier suffit à caractériser la réponse élastique globale. Les figures k̃ et μ̃ constituent des **données complémentaires** disponibles dans les notebooks.

---

## 08 · Résultats principaux

### 🔵 VER 1 — Inclusions sphéroïdales simples

- La **fraction volumique amplifie l'effet du contraste** de module de façon non linéaire : les interactions entre inclusions s'intensifient avec leur densité.
- La **sphère est la géométrie la moins efficace** parmi toutes les formes sphéroïdales — son tenseur d'Eshelby isotrope distribue la perturbation uniformément sans favoriser aucun mode de transfert de charge.
- **Sans contraste** (Ei = Em), la forme n'a aucun effet quelle que soit fi : ce cas sert de test de cohérence interne du modèle.

### 🟢 VER 2 — Inclusions composites bicouches

- L'**interphase périphérique** (~27 % du volume) exerce une influence sur Ẽ **supérieure à celle du cœur** (~73 %), car elle est en contact direct avec la matrice et conditionne tout transfert de charge.
- Le **signe du gradient interne** E1 − E2 détermine la monotonie de Ẽ avec l'épaisseur : croissante si E1 > E2, décroissante si E1 < E2.
- La **conception doit cibler la couche périphérique** pour optimiser l'efficacité mécanique.

### 🔴 VER 3 — Inclusions mixtes

- À **fraction volumique égale**, l'inclusion simple est *toujours* plus efficace mécaniquement que l'inclusion composite — l'interphase filtre le signal du cœur avant qu'il atteigne la matrice.
- La **hiérarchie interphase > cœur** est structurelle et se retrouve intacte dans le contexte mixte.
- La **forme** de l'inclusion simple et l'**épaisseur** de l'interphase composite sont des leviers **additifs et indépendants** : ils peuvent être optimisés séparément.

---

## 09 · Références

| # | Référence |
|:-:|:---|
| [1] | **Eshelby, J.D. (1957)** — The determination of the elastic field of an ellipsoidal inclusion. *Proc. R. Soc. London A*, 241, 376–396 |
| [2] | **Mori, T. & Tanaka, K. (1973)** — Average stress in matrix and average elastic energy of materials with misfitting inclusions. *Acta Metallurgica*, 21(5), 571–574 |
| [3] | **Hervé, E. & Zaoui, A. (1993)** — n-layered inclusion-based micromechanical modelling. *Int. J. Eng. Sci.*, 31(1), 1–10 |
| [4] | **Barthélémy, J.-F. (2022)** — *echoes*. Zenodo. [doi:10.5281/zenodo.14959866](https://doi.org/10.5281/zenodo.14959866) · [Documentation](https://jfbarthelemy.github.io/echoes) |

---

<br>

---

# 🇬🇧 English Version

---

## Table of Contents

- [01 · Project Description](#01--project-description)
- [02 · Thesis Objective](#02--thesis-objective)
- [03 · Thesis Structure](#03--thesis-structure)
- [04 · Notebook Organization](#04--notebook-organization)
- [05 · The echoes Library](#05--the-echoes-library)
- [06 · Global Parameters](#06--global-parameters)
- [07 · Note on Results](#07--note-on-results)
- [08 · Key Results](#08--key-results)
- [09 · References](#09--references)

---

## 01 · Project Description

This project is the numerical support for a Master's thesis in **Theoretical Physics**.
It contains **3 Jupyter notebooks** implementing analytical homogenization of composite materials via the Python library `echoes`, using the **Mori–Tanaka** scheme.

Simulations cover **three RVE configurations** (Representative Volume Element) of increasing complexity, enabling systematic parametric studies linking microstructure to effective elastic properties.

```
.
├── ver_simple_spherique.ipynb   ← RVE 1 : simple spheroidal inclusions
├── ver_composite.ipynb          ← RVE 2 : two-layer composite inclusions
├── ver_mixte.ipynb              ← RVE 3 : mixed inclusions (2 populations)
├── 1-RAPPORT_ROLAND.tex         ← Full thesis (LaTeX)
└── README.md
```

---

## 02 · Thesis Objective

> *The aim is not to reproduce known results, but to derive **actionable design rules** from a rigorous parametric analysis.*

| # | Axis | Description |
|:-:|:---|:---|
| **01** | **Formalism** | Master the micromechanical framework in isotropic linear elasticity — Eshelby's solution (1957), localization tensors, Mori–Tanaka scheme, Hervé–Zaoui model for multi-layer inclusions |
| **02** | **Parametric** | Quantify the influence of each microstructural parameter (volume fraction, modulus contrast, shape, interphase thickness and stiffness) on the effective elastic properties |

---

## 03 · Thesis Structure

> Written in LaTeX — file `1-RAPPORT_ROLAND.tex`

```
1-RAPPORT_ROLAND.tex
│
├── General Introduction
│
├── Chapter 1 ── Literature Review
│   ├── Composite materials        (history · constituents · industrial applications)
│   ├── Modelling methods          (analytical · FEM · FFT · experimental)
│   ├── Micromechanics             (RVE · Voigt · Reuss · Hill–Mandel lemma)
│   ├── Linear elasticity          (isotropy · Kelvin–Mandel notation)
│   ├── Eshelby problem            (inclusion + inhomogeneity · Hill polarization tensor P)
│   └── Homogenization schemes     (dilute · self-consistent · Mori–Tanaka)
│
├── Chapter 2 ── Modelling of Effective Properties
│   ├── RVE with simple spherical inclusions
│   ├── RVE with two-layer composite inclusions
│   ├── RVE with mixed inclusions
│   └── Hervé–Zaoui n-layer model
│       ├── Hydrostatic loading ──→ k_eff   (transfer matrices)
│       └── Deviatoric loading  ──→ mu_eff  (quadratic equation)
│
├── Chapter 3 ── Results & Discussion
│   ├── RVE 1 · vol. fraction · contrast · shape (oblate / sphere / prolate)
│   ├── RVE 2 · vol. fraction · contrast · interphase thickness ε
│   └── RVE 3 · fractions · contrasts C1–C4 · shape · shape–ε coupling
│
└── General Conclusion
```

---

## 04 · Notebook Organization

The three notebooks are **independent** — they can be run in any order.

---

### `ver_simple_spherique.ipynb` — RVE 1 · Simple Spheroidal Inclusions

Homogeneous matrix + inclusions of modulus Ei. **Mori–Tanaka applied directly.**
Geometry: sphere (ω = 1) or spheroid with aspect ratio ω = a/c.

| Study | Varied parameter(s) | Fixed parameter(s) |
|:---|:---|:---|
| Volume fraction | fi ∈ [0, 0.6] · Ei ∈ {5, 10, 20, 50} GPa | ω = 1 (sphere) |
| Modulus contrast | Ei/Em ∈ [0.1, 5] | fi ∈ {0.3, 0.4, 0.5, 0.6} |
| Shape — contrasted | ω ∈ [0.1, 10] (log scale) | Ei = 70 GPa |
| Shape — validation | ω ∈ [0.1, 10] (log scale) | Ei = Em = 10 GPa |

<details>
<summary>📁 Generated figures</summary>

```
module_young_effectif_mori_tanaka.png
compressibilite_effectif_mori_tanaka.png
cisaillement_effectif_mori_tanaka.png
effet_contraste_E.png / _K.png / _mu.png
effet_forme_E.png / _K.png / _mu.png
effet_forme_E_id.png / _K_id.png / _mu_id.png    ← validation (Ei = Em)
```
</details>

---

### `ver_composite.ipynb` — RVE 2 · Two-Layer Composite Inclusions

Composite spherical inclusions: **core** E1 + **interphase** E2.
Pipeline: **Hervé–Zaoui** → C_inc_eff → **Mori–Tanaka**.

> **Reference geometry:** R1 = 1.8, R2 = 2.0
> → core ≈ **72.9 %** of volume · interphase ≈ **27.1 %**

| Study | Varied parameter(s) | Fixed parameter(s) |
|:---|:---|:---|
| Vol. frac. — stiff interphase | fi ∈ [0, 0.6] · E1 ∈ {5, 10, 20, 50} GPa | E2 = 15 GPa |
| Vol. frac. — neutral interphase | fi ∈ [0, 0.6] · E1 ∈ {5, 10, 20, 50} GPa | E2 = 10 GPa |
| Vol. frac. — soft interphase | fi ∈ [0, 0.6] · E1 ∈ {5, 10, 20, 50} GPa | E2 = 5 GPa |
| Contrast E1/Em | E1/Em ∈ [0.1, 5] | E2 = 15 GPa |
| Contrast E2/Em | E2/Em ∈ [0, 10] | E1 = Em (neutral core) |
| Internal gradient E2/E1 | E2/E1 ∈ [0, 5] | E1 = 10 GPa |
| Thickness ε · fraction | ε/R2 ∈ [0, 1] · fi ∈ {0.3…0.6} | E1 = 50 GPa, E2 = 15 GPa |
| Thickness ε · contrast E1 | ε/R2 ∈ [0, 1] · E1 ∈ {5, 10, 20, 50} GPa | fi = 0.5, E2 = 15 GPa |
| Thickness ε · contrast E2 | ε/R2 ∈ [0, 1] · E2 ∈ {5, 10, 20, 50} GPa | fi = 0.5, E1 = 20 GPa |

<details>
<summary>📁 Generated figures</summary>

```
bicouche_E1.png / _K1.png / _mu1.png
bicouche_E2.png / _K2.png / _mu2.png
bicouche_E3.png / _K3.png / _mu3.png
cas1_E1_Em_E.png / _K.png / _mu.png
cas2_E2_Em_E.png / _K.png / _mu.png
cas3_E2_E1_E.png / _K.png / _mu.png
eps_fi_E.png / _K.png / _mu.png
eps_ctE1_E.png / _K.png / _mu.png
eps_ctE2_E.png / _K.png / _mu.png
```
</details>

---

### `ver_mixte.ipynb` — RVE 3 · Mixed Inclusions (Two Populations)

Two populations coexist in the same matrix:
- **Simple** spheroidal inclusions: modulus Es, fraction fs, aspect ratio ω
- **Composite** two-layer inclusions: core Ec, interphase Esh, fraction fc

Pipeline: **Hervé–Zaoui** (per composite inclusion) → **Mori–Tanaka** (both populations jointly).

| Study | Description |
|:---|:---|
| Fractions 1 | fs = fc ∈ [0, 0.3] — both populations grow together |
| Fractions 2 | fs ∈ [0, 0.5], fc = 0.10 fixed |
| Fractions 3 | fc ∈ [0, 0.5], fs = 0.10 fixed |
| Contrast C1 | Es/Em varies · neutral composite inclusions |
| Contrast C2 | Ec/Em varies · neutral simple inclusion and interphase |
| Contrast C3 | Esh/Em varies · neutral simple inclusion and core |
| Contrast C4 | Esh/Ec varies (internal gradient) · neutral simple inclusion |
| Shape 1 | ω ∈ [0.1, 10] · Es = Ec = 50 GPa, Esh = 15 GPa |
| Shape 2 | ω ∈ [0.1, 10] · Es = 20, Ec = 50, Esh = 15 GPa |
| Shape 3 | ω ∈ [0.1, 10] · Es = 50, Ec = 20, Esh = 15 GPa |
| ε + shape 1 | ε/R2 ∈ [0, 1] · 5 values of ω · Es = Ec = 50 GPa |
| ε + shape 2 | ε/R2 ∈ [0, 1] · 5 values of ω · Es = 50, Ec = 20 GPa |
| ε + shape 3 | ε/R2 ∈ [0, 1] · 5 values of ω · Es = 30, Ec = 50 GPa |

> **Validation case:** each shape and ε study includes a case with Es = Em — the five curves must perfectly overlap, confirming no spurious coupling between the two levers.

<details>
<summary>📁 Generated figures</summary>

```
et1_E.png / _K.png / _mu.png   ·   et2_...   ·   et3_...
C1_A_E.png / _K.png / _mu.png  ···  C4_B_...
forme_A_E.png / _K.png / _mu.png                 (3 contrast sets)
eps_forme_E.png / _K.png / _mu.png               (3 contrast sets)
eps_forme_neutre_E.png / _mu.png                 (3 sets · validation case)
```
</details>

---

## 05 · The echoes Library

> **`echoes`** — *Extended Calculator of HOmogEnization Schemes*
> Developed by **Jean-François Barthélémy** (Cerema – Université Gustave Eiffel), thesis supervisor.
> **C++ core**, **Python** interface. Supports: linear elasticity, conductivity, viscoelasticity, nonlinear homogenization.

| Resource | Link |
|:---|:---|
| 📘 Documentation | [jfbarthelemy.github.io/echoes](https://jfbarthelemy.github.io/echoes) |
| 📦 DOI / Download | [10.5281/zenodo.14959866](https://doi.org/10.5281/zenodo.14959866) |

```bash
# 1. Download the .whl file from the DOI link above
# 2. Install:
pip install -U echoes-XYZ.whl
```

| Function | Role |
|:---|:---|
| `stiff_Enu(E, nu)` | Build isotropic stiffness tensor from E and ν |
| `sphere(C0)` | Hill tensor — spherical inclusion |
| `spheroidal(C0, omega)` | Hill tensor — spheroidal inclusion with aspect ratio ω |
| `sphere_nlayers(radii, stiffs)` | Hervé–Zaoui: n-layer concentric spherical inclusion |
| `rve(C0)` | Create an RVE with matrix C0 |
| `ellipsoid(C_i, P, f)` | Add a spheroidal inclusion phase to the RVE |
| `homogenize(MT)` | Compute effective tensor via Mori–Tanaka scheme |

---

## 06 · Global Parameters

| Parameter | Value |
|:---|:---|
| Matrix modulus | Em = 10 GPa |
| Poisson's ratio (RVE 1 & 3) | ν = 0.2 |
| Poisson's ratio (RVE 2) | ν = 0.1 |
| Maximum volume fraction | fi ≤ 0.6 |
| Figure size | (9, 6) inches |
| Colors | `blue` · `green` · `black` · `red` |
| Markers | `o` · `s` · `^` · `D` |

```python
plt.rcParams.update({
    "axes.linewidth":     2,     "axes.labelsize":    16,    "axes.labelweight": "bold",
    "xtick.labelsize":   12,     "ytick.labelsize":   12,
    "xtick.major.width":  1.5,   "ytick.major.width":  1.5,
})
```

---

## 07 · Note on Results

> ⚠️ **In the thesis, only the effective Young's modulus Ẽ is commented and analysed** in the main text.

The notebooks compute and plot **three moduli** for every parametric study:

| Modulus | Commented in thesis | Computed + plotted |
|:---:|:---:|:---:|
| Ẽ — effective Young's | ✅ | ✅ |
| k̃ — effective bulk | ❌ | ✅ |
| μ̃ — effective shear | ❌ | ✅ |

This choice is justified by the relation: **Ẽ = 9 k̃ μ̃ / (3 k̃ + μ̃)**

Since the trends in k̃ and μ̃ are consistent with Ẽ, analysing the latter is sufficient to characterise the global elastic response. The k̃ and μ̃ figures serve as **supplementary data** available in the notebooks.

---

## 08 · Key Results

### 🔵 RVE 1 — Simple Spheroidal Inclusions

- **Volume fraction amplifies the contrast effect** in a non-linear manner: mechanical interactions between inclusions intensify with their density.
- The **sphere is the least efficient geometry** among all spheroidal shapes — its isotropic Eshelby tensor distributes the perturbation uniformly without favouring any load-transfer mode.
- **Without contrast** (Ei = Em), shape has no effect for any fi: this case serves as an internal consistency test of the model.

### 🟢 RVE 2 — Two-Layer Composite Inclusions

- The **peripheral interphase** (~27 % of volume) exerts an influence on Ẽ **greater than the core** (~73 %), because it is in direct contact with the matrix and governs all load transfer.
- The **sign of the internal gradient** E1 − E2 determines the monotonicity of Ẽ with thickness: increasing if E1 > E2, decreasing if E1 < E2.
- **Design should target the peripheral layer** to optimise mechanical efficiency.

### 🔴 RVE 3 — Mixed Inclusions

- At **equal volume fraction**, the simple inclusion is *always* more mechanically efficient than the composite inclusion — the interphase filters the core's signal before it reaches the matrix.
- The **interphase > core hierarchy** is structural and is found intact in the mixed context.
- The **shape** of the simple inclusion and the **interphase thickness** are **additive and independent** levers: they can be optimised separately.

---

## 09 · References

| # | Reference |
|:-:|:---|
| [1] | **Eshelby, J.D. (1957)** — The determination of the elastic field of an ellipsoidal inclusion. *Proc. R. Soc. London A*, 241, 376–396 |
| [2] | **Mori, T. & Tanaka, K. (1973)** — Average stress in matrix and average elastic energy of materials with misfitting inclusions. *Acta Metallurgica*, 21(5), 571–574 |
| [3] | **Hervé, E. & Zaoui, A. (1993)** — n-layered inclusion-based micromechanical modelling. *Int. J. Eng. Sci.*, 31(1), 1–10 |
| [4] | **Barthélémy, J.-F. (2022)** — *echoes*. Zenodo. [doi:10.5281/zenodo.14959866](https://doi.org/10.5281/zenodo.14959866) · [Documentation](https://jfbarthelemy.github.io/echoes) |

---

<div align="center">

**HOUNKPE Mawulikplimi Roland** · Master Physique Théorique · Université de Lomé · 2023–2025

*Supervisé par Dr. A. Adessina (Cerema – Univ. Gustave Eiffel) & Prof. K. N'Wuitcha (Université de Lomé)*

</div>