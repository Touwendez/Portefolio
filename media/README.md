# Médias du portfolio

Dossier des photos / vidéos de démonstration intégrées dans `index.html`.

## Vidéo — Robot articulé (ESP32)

La carte projet « Robot articulé » attend **deux fichiers** ici :

| Fichier | Rôle | Statut |
|---|---|---|
| `robot-articule-demo.mp4` | la vidéo de démo (720p, compressée, ~6 Mo) | **en place** |
| `robot-articule-poster.jpg` | l'image d'aperçu avant lecture (extraite de la vidéo) | **en place** |

Pour **remplacer** la vidéo plus tard, dépose une nouvelle source et recompresse-la
avec la commande ci-dessous (en gardant le même nom de sortie), puis régénère le poster.

### Préparer la vidéo (compression)

Une vidéo de téléphone fait souvent 50–150 Mo. Pour GitHub Pages, vise **2–6 Mo**.
Installe ffmpeg si besoin (`brew install ffmpeg`), puis depuis la racine du dépôt :

```bash
# Remplace "VIDEO_SOURCE.mov" par le chemin de ta vidéo.
# Recompresse en 720p, sans le son, optimisé pour le web :
ffmpeg -i VIDEO_SOURCE.mov \
  -vf "scale=-2:720" -c:v libx264 -crf 28 -preset slow \
  -movflags +faststart -an \
  media/robot-articule-demo.mp4
```

- `-crf 28` : qualité/poids (↑ le nombre = plus léger, ~23 à 30 selon le rendu voulu).
- `-an` : supprime l'audio. Retire-le si tu veux garder le son.
- `+faststart` : permet la lecture sans attendre le téléchargement complet.

### (Optionnel) Générer un vrai poster à partir d'une image de la vidéo

```bash
ffmpeg -i media/robot-articule-demo.mp4 -ss 00:00:01 -vframes 1 media/robot-articule-poster.jpg
```

Puis dans `index.html`, remplace `poster="media/robot-articule-poster.svg"`
par `poster="media/robot-articule-poster.jpg"`.

### Publier

```bash
git add media/
git commit -m "Ajout de la vidéo de démo du robot articulé"
git push
```

Le site se redéploie automatiquement (~1 min).
