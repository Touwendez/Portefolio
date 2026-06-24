# Médias du portfolio

Dossier des photos / vidéos de démonstration intégrées dans `index.html`.

## Vidéos de démo (section « Démos vidéo »)

Chaque démo de `index.html` s'appuie sur deux fichiers : la vidéo `.mp4` (compressée)
et un poster `.jpg` (image d'aperçu avant lecture).

| Fichier | Rôle | Statut |
|---|---|---|
| `robot-articule-demo.mp4` | démo robot articulé (portrait, 720p, ~6 Mo) | **en place** |
| `robot-articule-poster.jpg` | poster du robot | **en place** |
| `carla_ekf.mp4` | démo localisation ROS2/CARLA (paysage, 720p, ~3 Mo) | **en place** |
| `carla_ekf-poster.jpg` | poster CARLA/EKF | **en place** |
| `carla_ekf_2.mp4` | localisation ROS2/CARLA — séquence complémentaire (paysage, 720p, ~1 Mo) | **en place** |
| `carla_ekf_2-poster.jpg` | poster CARLA/EKF (séquence 2) | **en place** |
| `camera_demo.mp4` | vision Raspberry Pi — détection de personnes (carré, 720p, ~0,9 Mo) | **en place** |
| `camera_demo-poster.jpg` | poster vision Raspberry Pi | **en place** |
| `percepflow.mp4` | DriveSense : perception multi-capteurs (paysage, 720p, ~9 Mo) | **en place** |
| `percepflow-poster.jpg` | poster DriveSense | **en place** |

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
