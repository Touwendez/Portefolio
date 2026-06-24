# Portfolio  Touwende Ouedraogo

Portfolio personnel d'un **ingénieur automaticien** spécialisé en robotique, perception
multi-capteurs (GNSS/INS, Lidar, Radar, Caméra), vision embarquée et systèmes industriels.

🔗 **Site en ligne** : https://touwendez.github.io/Portfolio/

## Aperçu

Site statique d'une seule page (`index.html`), sans dépendance ni build : HTML/CSS
autonomes, polices chargées depuis Google Fonts, diagrammes d'architecture en SVG inline.

Sections : profil, compétences techniques, expériences, projets phares (avec schémas
d'architecture), travaux complémentaires, formation et contact.

## Développement local

Aucune installation requise. Pour prévisualiser :

```bash
# ouvrir directement
open index.html

# ou servir en local
python3 -m http.server 8000
# puis http://localhost:8000
```

## Déploiement (GitHub Pages)

Le déploiement est automatisé via GitHub Actions
([.github/workflows/deploy.yml](.github/workflows/deploy.yml)) : chaque push sur `main`
publie le site.

Activation (une seule fois) :

1. Pousser le dépôt sur GitHub.
2. **Settings → Pages → Build and deployment → Source : GitHub Actions**.
3. Le site est publié à l'adresse ci-dessus à chaque push sur `main`.

## Contact

- ✉️ boulanger02t@gmail.com
- 💼 [linkedin.com/in/touw-ouedraogo](https://linkedin.com/in/touw-ouedraogo)
- 🐙 [github.com/Touwendez](https://github.com/Touwendez)
