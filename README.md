# Carte des poseurs de confiance Homemat

Carte interactive des poseurs de confiance, hébergée gratuitement sur GitHub Pages.

**Adresse publique :** https://hexamedia-43.github.io/carte-homemat/

## Fonctionnement

| Élément | Service | Coût |
|---|---|---|
| Fond de carte | Plan IGN (Géoplateforme) | Gratuit, sans clé |
| Recherche d'adresse, ville | API de géocodage IGN | Gratuit, sans clé |
| Recherche par code postal | geo.api.gouv.fr | Gratuit, sans clé |
| Liste des poseurs | Google Sheet publié en CSV | Gratuit |
| Hébergement | GitHub Pages | Gratuit |
| Bibliothèques | Leaflet, PapaParse (cdnjs) | Gratuit |

## Mettre à jour la liste

Modifier le Google Sheet « Poseurs_Homemat », onglet **Poseurs**. Les changements apparaissent sur la carte quelques minutes après l'enregistrement.

- `actif` : `non` masque le poseur, toute autre valeur (ou vide) l'affiche.
- `latitude` / `longitude` : facultatives. Si elles sont vides, la carte les calcule à partir de l'adresse.
- `specialite` (colonne K, facultative) : métier affiché sous le nom, ex. Menuiserie.
- Ne pas renommer les intitulés de colonnes ni l'onglet.

Le lien du CSV est défini dans `index.html`, constante `CONFIG.csvUrl`.

## Intégration dans Odoo

Bloc **Code intégré** (Embed Code), coller :

```html
<iframe src="https://hexamedia-43.github.io/carte-homemat/"
        style="width:100%;height:760px;border:0;border-radius:12px;"
        loading="lazy" allow="geolocation"
        title="Carte des poseurs de confiance Homemat"></iframe>
```

`allow="geolocation"` est nécessaire pour que le bouton « Me localiser » fonctionne dans l'iframe.

## Réutilisation sur le futur site (Lovable / Claude Code)

Deux options :

1. Garder la même iframe (aucun travail).
2. Porter `index.html` en composant React (`react-leaflet`) en conservant la même source de données (`CONFIG.csvUrl`).
