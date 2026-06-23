# Stride

App fitness perso : **défis du jour** kettlebell + poids du corps, calibrés sur un profil figé, avec **niveau / XP** (gamification) et une explication + image pour chaque exercice.

L'app est mono-utilisateur : pas d'onboarding, pas de formulaire. Le profil est codé en dur (homme, 38 ans, 183 cm, 87 kg, tour de taille 100 cm, kettlebell 16 kg par défaut). Seuls le poids, le tour de taille et la charge de la kettlebell restent ajustables (onglet Profil).

## Défis du jour

- **4 défis par jour, affichés un par un** : le suivant n'apparaît que quand le précédent est validé.
- **Pompes toujours en premier** (les pectoraux à la kettlebell, c'est galère), puis un exercice Haut, un Bas, un Core, tirés au sort par date avec anti-répétition de la veille.
- Comptage **+1 à chaque rep** (plus gratifiant que +5/+10). Les exercices chronométrés (gainage, hollow) ont un bouton **Tenir** qui lance un chrono.
- **Nombre de répétitions précis** : pour les mouvements unilatéraux/alternés, la cible est un *total* et l'app indique « X au total · Y de chaque côté ».
- Chaque exercice a une **fiche** (image, description, version plus facile / plus dure, lien démo vidéo). Images servies via [free-exercise-db](https://github.com/yuhonas/free-exercise-db) (CDN jsDelivr), avec repli sur le texte si hors-ligne.
- Une fois les 4 défis bouclés : **un mot d'encouragement spécifique au niveau** + confettis.
- Pas d'échauffement imposé : c'est à toi d'y penser.

## Niveau / XP

On gagne **1 XP par rep** (ou seconde d'effort) + un bonus à chaque pesée, et on **perd un peu d'XP** pour chaque journée passée (depuis la création du compte) où les défis ne sont pas remplis (~30 XP pour un jour entièrement manqué, proportionnel sinon, et toujours plus lent que le gain). Le **niveau** pilote la difficulté : 35 % des capacités au niveau 0, +5 % par niveau (plafond 160 %). Redescendre de niveau **allège** les défis. L'XP est recalculée jour après jour dans l'ordre chronologique (pas de récursion, pas de rétroactivité).

## Onglets

- **Défis** : niveau/XP en haut, puis le défi du jour en cours.
- **Poids** : pesées + courbe + volume total.
- **Succès** : trophées débloqués.
- **Profil** : mesures, niveau, capacités estimées, export/import JSON, reset.

**Live** : https://alcegobe.github.io/Stride/

## Stack

- Un seul fichier `index.html` self-contained
- Vanilla JS, pas de framework
- Persistance en `localStorage` (clés `pa_*`)
- PWA installable + offline (service worker `sw.js`)
- Hébergé sur GitHub Pages

## Dev local

```bash
cd /path/to/Stride
python -m http.server 8765   # ou n'importe quel serveur statique
# → http://localhost:8765
```

Mobile-first. Sur desktop (≥ 768px), le contenu est cadré dans une colonne de 480px.

## Reset / backup

- Reset : onglet Profil → « Tout réinitialiser », ou en console `Object.keys(localStorage).filter(k => k.startsWith('pa_')).forEach(k => localStorage.removeItem(k))`.
- Backup : onglet Profil → « Exporter » / « Importer » (JSON).

## Licence

Privé, usage perso.
