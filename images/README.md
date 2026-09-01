# Images — Polytexa

Toutes les images sont livrées **en niveaux de gris**, en WebP + JPEG appelés
via `<picture>`. Le duotone final — ombres `--nuit`, hautes lumières `--lin` —
est appliqué au rendu par le filtre SVG `#duotone` défini dans `index.html`.
Si ce filtre ne s'applique pas, le repli est un gris neutre : jamais de
dominante hors palette.

## Photographies d'architecture — Wikimedia Commons

Domaine public ou CC0 : **aucune attribution n'est juridiquement exigée**,
usage commercial libre. Les crédits ci-dessous sont donnés par correction.

| Fichier | Emplacement | Sujet réel | Licence | Source |
|---|---|---|---|---|
| `hero` | Fond du hero | Chalets et sommets, Samoëns | Domaine public | [Commons](https://commons.wikimedia.org/wiki/File:Chalets_in_Samoens_with_some_summits.jpg) |
| `real-1` | Galerie — grande tuile | Chalet Biord, Samoëns | Domaine public | [Commons](https://commons.wikimedia.org/wiki/File:Chalet_Biord_in_Samoens.jpg) |
| `real-2` | Galerie | Chalet de Grenoble, Le Bettex, Saint-Gervais-les-Bains | CC0 | [Commons](https://commons.wikimedia.org/wiki/File:Chalet_de_Grenoble,_Le_Bettex,_Saint-Gervais-les-Bains,_2025.jpg) |
| `real-3` | Galerie | Maison à lauburu, Savoie | Domaine public | [Commons](https://commons.wikimedia.org/wiki/File:House_with_lauburu_in_Savoie.jpg) |
| `real-4` | Galerie | Maison du docteur, Samoëns | Domaine public | [Commons](https://commons.wikimedia.org/wiki/File:Maison_du_docteur_(Samoens)_2.jpg) |
| `real-5` | Galerie | Chalet ancien, Samoëns | Domaine public | [Commons](https://commons.wikimedia.org/wiki/File:Ancient_wooden_house_in_Samoens.jpg) |

> ### À remplacer avant mise en ligne
>
> Ces six photographies montrent de l'architecture savoyarde **réelle mais
> située à Samoëns et Saint-Gervais**, alors que les légendes de la galerie
> annoncent Annecy, Annecy-le-Vieux, Aix-les-Bains et Annemasse — et les
> présentent comme des réalisations Polytexa.
>
> Ce sont donc des **images d'attente pour la maquette**. Avant mise en ligne,
> il faut soit substituer les photos de chantiers réellement réalisés par
> Christian Francioli, soit ajuster les légendes pour qu'elles n'affirment
> plus une réalisation ni une commune.

## Photographies d'ambiance — reprises du site actuel

| Fichier | Emplacement | Origine |
|---|---|---|
| `expertise` | Accent de la section Expertise | `/uploads/aside4` |
| `garanties` | Texture de fond de la bande Garanties | `/galerie/zoom/calque-35` (détail) |

Ce sont des **images de banque génériques** issues du site existant, utilisées
en ambiance uniquement, jamais comme preuve d'une réalisation. `garanties` est
en plus teintée sur la rampe anthracite pour ne pas délaver la bande sombre.
Vérifier que leurs licences couvrent bien le nouveau site.

## Remplacer une photo de galerie

Une `<img>` par `<figure class="gal-item">`, le CSS fait le reste :

```html
<figure class="gal-item" tabindex="0">
  <picture>
    <source srcset="images/real-1.webp" type="image/webp">
    <img class="duotone" src="images/real-1.jpg"
         alt="Description de la réalisation" width="900" height="957"
         loading="lazy" decoding="async">
  </picture>
  <figcaption class="gal-legende">Construction — Annecy</figcaption>
  <span class="gal-voile" aria-hidden="true">Construction — Annecy</span>
</figure>
```

### Formats
- **Grande tuile** (première) : ~900×960 px
- **Petites tuiles** : ~800×640 px
- **Fond de hero** : ~2000×1000 px
- Passer les photos en niveaux de gris et garder `class="duotone"` pour rester
  dans la direction artistique
- Un voile dégradé (`.gal-item::after`) garantit la lisibilité de la légende
  quelle que soit la photo : contraste mesuré entre 6,7:1 et 15,9:1
