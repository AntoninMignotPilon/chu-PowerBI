# Charte graphique – Tableau de bord CHU (Groupe 3)

Ce fichier sert de référence commune pour que toutes les pages du rapport `Groupe3.pbip` aient le même aspect, même si chacun travaille sur son PC avec sa propre IA.

**Comment s'en servir :** donne ce fichier en entier à ton IA avant de lui demander de mettre ta page en forme. Le prompt prêt à copier se trouve à la fin.

Le fichier `CHU_theme.json`, à côté, reprend les mêmes couleurs sous forme de thème Power BI. Il est facultatif : **une seule personne** l'importe (*Affichage → Thèmes → Parcourir les thèmes*), vérifie le rendu de toutes les pages, puis commit. Les autres ne doivent pas l'importer chacun de leur côté.

Les valeurs ci-dessous reprennent le style **déjà présent** dans le rapport : bandeau bleu nuit, pages KPI 4 et 5. Ce n'est pas un nouveau style.

---

## 1. Règles absolues

1. **Front uniquement.** Ne rien modifier dans `Groupe3.SemanticModel` : pas de mesure, de colonne, de relation ni de requête Power Query. Ne pas changer les champs d'un visuel, ses filtres ni son type d'agrégation.
2. **Ne rien ajouter.** Pas de lien, de bouton, d'image, de signet, de nouvelle page ni de nouveau visuel. On met en forme ce qui existe.
3. **Aucun emoji**, ni dans les titres, ni dans les zones de texte.
4. **Le filtre de date reste un curseur** : segment en mode « Entre » (`Between`), avec la barre à glisser. Ne jamais le remplacer par une liste, une liste déroulante ou des boutons.
5. **Les chiffres clés se lisent d'un coup d'œil** : valeur en gros, couleur d'accent, intitulé court au-dessus ou en dessous.
6. **Ne toucher qu'à sa propre page.** Le bandeau de gauche (forme, texte « CHU - Tableau de bord », navigateur de pages) est identique sur toutes les pages : on ne le modifie pas.

---

## 2. Grille de la page (1920 × 1080)

```
x=0      300 324                                                    1896 1920
┌────────┬──┬─────────────────────────────────────────────────────────┬──┐
│BANDEAU │  │ Titre de page                         y=24   h=72       │  │
│ bleu   │  ├─────────────────────────────────────────────────────────┤  │
│ nuit   │  │ Filtres (curseur de date en premier)  y=104  h=72       │  │
│        │  ├──────────┬──────────┬──────────┬──────────┬────────────┤  │
│ navig. │  │ Carte    │ Carte    │ Carte    │ Carte    │ …          │  │
│        │  │ y=192 h=112                                            │  │
│        │  ├──────────────────────────┬─────────────────────────────┤  │
│        │  │ Graphique principal      │ Graphique secondaire        │  │
│        │  │ y=320 → 1064             │                             │  │
└────────┴──┴──────────────────────────┴─────────────────────────────┴──┘
```

| Élément | x | y | Largeur | Hauteur |
|---|---|---|---|---|
| Forme du bandeau (ne pas toucher) | 0 | 0 | 300 | 1080 |
| Texte « CHU - Tableau de bord » (ne pas toucher) | 16 | 24 | 268 | 64 |
| Navigateur de pages (ne pas toucher) | 16 | 112 | 268 | 512 |
| Titre de page (zone de texte) | 324 | 24 | 1572 | 72 |
| Ligne des filtres | à partir de 324 | 104 | selon le filtre | 72 |
| Ligne des cartes | à partir de 324 | 192 | 302 (jusqu'à 5 cartes) | 112 |
| Zone des graphiques | 324 → 1896 | 320 | selon la page | jusqu'à y=1064 |

- **Espacement entre deux visuels : 16 px**, horizontalement et verticalement.
- **Marge droite et marge basse : 16 à 24 px.** Aucun visuel ne doit dépasser x=1896 ni y=1064.
- **Aucun chevauchement.** En particulier, le curseur de date ne doit pas recouvrir le titre.
- Si ta page n'a pas de ligne de cartes, les graphiques remontent à y=192.

---

## 3. Couleurs

| Rôle | Couleur |
|---|---|
| Bandeau gauche, titres, texte principal | `#0F172A` (bleu nuit) |
| Accent : valeurs des cartes, barres, lignes principales | `#1F5FAD` (bleu) |
| Page sélectionnée dans le navigateur | `#0E7C86` (bleu canard) |
| Femmes (toutes les pages) | `#C4610F` (orange) |
| Hommes (toutes les pages) | `#1F5FAD` (bleu) |
| Série de comparaison (moyenne, ensemble) | `#A19F9D` (gris moyen) |
| Texte secondaire (intitulés, sous-titres, axes) | `#605E5C` (gris) |
| Bordure des visuels | `#E1DFDD` (gris clair) |
| Fond des visuels | `#FFFFFF` |
| Fond de la page | `#FFFFFF` (par défaut, ne pas changer) |

- **Graphiques à une seule série :** toutes les barres en `#1F5FAD`.
- **Graphiques Femmes / Hommes :** garder les mêmes deux couleurs sur toutes les pages, Femmes `#C4610F` et Hommes `#1F5FAD`, comme sur la page KPI 5.
- Pas de dégradé, pas de couleur vive en plus.

---

## 4. Textes

Police : celle par défaut de Power BI (Segoe UI). Ne pas en changer.

| Texte | Taille | Style | Couleur |
|---|---|---|---|
| Titre de page (zone de texte) | 22 pt | gras | `#0F172A` |
| Sous-titre de page (facultatif, 2e ligne) | 12 pt | normal | `#605E5C` |
| Titre d'un visuel | 14 pt | gras | `#0F172A` |
| Sous-titre d'un visuel (facultatif) | 10 pt | normal | `#605E5C` |
| Titre d'un segment (filtre) | 11 pt | gras | `#0F172A` |
| Axes, étiquettes de catégories | 10 à 11 pt | normal | `#605E5C` |
| Étiquettes de données sur les barres | 10 à 11 pt | normal | `#0F172A` |

**Formulation des titres :** une phrase courte en français qui dit ce que montre le visuel, par exemple « Hospitalisations par établissement ».
- Jamais le titre automatique de Power BI (« Somme de … par … »).
- Jamais d'emoji.
- Majuscule seulement au premier mot.

---

## 5. Réglages par type de visuel

### Commun à tous les visuels (sauf bandeau, zones de texte et navigateur)
Dans *Format → Général* :
- **Arrière-plan :** activé, `#FFFFFF`, transparence 0 %.
- **Bordure :** activée, `#E1DFDD`, coins arrondis 8 px.
- **Ombre :** désactivée.
- **Titre :** activé, 14 pt, gras, `#0F172A`.

### Cartes (chiffres clés)
- **Valeur :** 28 à 32 pt, gras, `#1F5FAD`. Pour une carte qui affiche un texte long, comme un nom de diagnostic : 16 pt, avec le retour à la ligne activé.
- **Intitulé :** affiché, 11 pt, `#605E5C`. Il dit ce que mesure le chiffre, par exemple « Séjours hospitaliers ».
- **Unités d'affichage :** « Aucune » pour les nombres (pas de « K »), et 1 ou 2 décimales pour les pourcentages.
- Toutes les cartes d'une même ligne ont la même taille et sont alignées.

### Graphiques en barres ou colonnes
- **Étiquettes de données :** activées, pour que la valeur se lise directement sur la barre.
- **Axe des valeurs :** masqué quand les étiquettes de données sont affichées.
- **Légende :** masquée s'il n'y a qu'une série, sinon en haut.
- **Tri :** du plus grand au plus petit, sauf pour un axe de temps, qui reste chronologique.

### Courbes
- **Ligne principale :** `#1F5FAD`, épaisseur 3 px.
- **Ligne de comparaison** (moyenne, ensemble) : gris `#A19F9D`.
- **Axe X :** chronologique.

### Segments (filtres)
- **Date :** curseur « Entre », toujours en premier sur la ligne des filtres. Ne jamais changer son mode.
- **Autres segments :** liste déroulante, ou boutons s'il y a peu de valeurs (sexe, tranche d'âge).
- **En-tête du segment :** masqué. On utilise le titre du visuel (11 pt, gras) à la place.

### Tableaux
- **En-têtes :** 11 pt, gras, `#0F172A`, fond `#F3F2F1`.
- **Valeurs :** 11 pt. Pour un petit tableau de chiffres clés : 14 à 16 pt.
- **Quadrillage :** horizontal seulement, en `#E1DFDD`.

### Cartes géographiques, jauges, anneaux
- **Jauge :** valeur centrale à 28 pt ou plus, en `#1F5FAD`.
- **Anneau :** étiquettes affichées en pourcentage. Pas plus de 6 parts.

---

## 6. Vérification avant de commit

- [ ] Aucun fichier modifié dans `Groupe3.SemanticModel/` (vérifier avec `git status`).
- [ ] Aucun emoji sur la page.
- [ ] Le filtre de date est un curseur « Entre ».
- [ ] Les chiffres clés se lisent à 2 mètres de l'écran.
- [ ] Tous les visuels ont un titre clair, et aucun ne garde un titre automatique.
- [ ] Rien ne dépasse de la grille, rien ne se chevauche, l'espacement est de 16 px.
- [ ] Le bandeau de gauche n'a pas bougé.
- [ ] Aucun lien, bouton ni visuel ajouté.
- [ ] Commit seulement des fichiers de **ta** page (`Groupe3.Report/definition/pages/<id de ta page>/`). Ne pas commit `pages.json` s'il ne change que la page active.

---

## 7. Prompt à donner à ton IA

> Je travaille sur un rapport Power BI au format PBIP (dossier `Groupe3.Report`, format PBIR, un `visual.json` par visuel). Voici la charte graphique de l'équipe (fichier `CHARTE_GRAPHIQUE.md`, copié ci-dessous). Mets en forme **uniquement** la page « <nom de ma page> » en respectant cette charte à la lettre.
> Contraintes : ne modifie que l'apparence (`visualContainerObjects`, `objects` de mise en forme, `position`). Ne touche pas à `query`, `filterConfig`, `objects.data`, `objects.general.filter` ni à `Groupe3.SemanticModel`. N'ajoute aucun visuel, lien ni bouton. Retire les emojis. Garde le curseur de date en mode « Entre ». Power BI doit être fermé pendant la modification des fichiers.
> Avant d'appliquer, montre-moi la liste des changements visuel par visuel.
