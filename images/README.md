# Images — Polytexa

## Fichiers présents

| Fichier | Usage | Dimensions | Origine |
|---|---|---|---|
| `hero.jpg` / `.webp` | Bloc photographique du hero (colonne droite) | 800×450 | Site actuel, `/galerie/zoom/calque-35` |
| `expertise.jpg` / `.webp` | Accent de la section Expertise | 705×396 | Site actuel, `/uploads/aside4` |
| `garanties.jpg` / `.webp` | Texture de fond de la bande Garanties | 800×284 | Site actuel, `/galerie/zoom/calque-35` (détail) |

Toutes sont livrées **en niveaux de gris** (`garanties` est en plus teintée sur la
rampe anthracite). Le duotone final — ombres `--nuit`, hautes lumières `--lin` —
est appliqué au rendu par le filtre SVG `#duotone` défini dans `index.html`.
Si ce filtre venait à ne pas s'appliquer, le repli est une image en gris neutre :
jamais de dominante hors palette.

> **Ces trois images proviennent de banques d'images génériques** reprises du site
> actuel. Elles sont utilisées ici comme **illustration d'ambiance** uniquement,
> jamais comme preuve d'une réalisation. Vérifier que les licences couvrent bien
> le nouveau site avant mise en ligne.

## Section Réalisations — remplacer les planches par les vraies photos

La galerie affiche pour l'instant cinq **dessins d'architecte en SVG**
(élévation, plan, coupe, plan de masse, charpente). Ce sont des emplacements
assumés, pas des projets : aucune photo de banque n'y est présentée comme un
chantier Polytexa.

Pour insérer une vraie photographie, ajouter une `<img>` dans la `<figure>`
concernée — elle recouvre automatiquement le dessin, aucune autre modification
n'est nécessaire :

```html
<figure class="gal-item" tabindex="0">
  <img src="images/realisation-annecy.jpg"
       alt="Maison individuelle livrée à Annecy" width="800" height="600"
       loading="lazy" decoding="async">
  <svg class="gal-dessin" ...>...</svg>
  <figcaption class="gal-legende">Construction — Annecy</figcaption>
  <span class="gal-voile" aria-hidden="true">Construction — Annecy</span>
</figure>
```

Une fois toutes les photos en place, les `<svg class="gal-dessin">` peuvent être
supprimés.

### Formats conseillés
- **Grande tuile** (première) : 900×960 px environ
- **Petites tuiles** : 800×640 px environ
- Poids visé : moins de 120 Ko par image en JPEG qualité 75-80
- Fournir aussi une variante `.webp` et l'appeler via `<picture>`, comme pour
  `hero` et `expertise`

### Traitement
Pour rester dans la direction artistique, passer les photos en niveaux de gris
et leur ajouter `class="duotone"` :

```html
<img class="duotone" src="images/realisation-annecy.jpg" ...>
```
