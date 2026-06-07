# Stride

App fitness perso : défis quotidiens **kettlebell + poids du corps** calibrés (pecs, haut, bas, core) + rituels (eau, sommeil, marche, protéines) + suivi poids, photos, succès.

Mode kettlebell : tout le programme tourne autour d'une kettlebell (poids réglable, 16 kg par défaut) et du poids du corps. Le nombre de reps est calibré selon le profil (âge, taille, poids, sexe, objectif, niveau de départ) **et** la charge de la cloche (plus lourd = moins de reps).

Système de niveau / XP : on gagne de l'XP en faisant ses séries (reps), ses rituels et ses pesées, et on en **perd un peu** pour chaque journée passée où les objectifs ne sont pas remplis (~35 XP pour un jour entièrement manqué, proportionnel sinon, et toujours plus lent que le gain). Le **niveau** (affiché en grand sur l'accueil, avec barre qui monte et célébration à chaque palier) **pilote la difficulté** des défis : démarrage doux à 30 % des capacités au niveau 0, puis +5 % par niveau (plafond 160 %) — donc redescendre de niveau **allège** les défis à refaire. L'XP est recalculée jour après jour dans l'ordre chronologique : la pénalité d'un jour n'impacte que les jours suivants (pas de boucle, pas de rétroactivité). La perte démarre à la création du compte (`decayStart`), fixée au jour d'adoption pour les comptes existants afin de ne pas pénaliser les anciennes séances.

**Live** : https://alcegobe.github.io/Stride/

## Stack

- Un seul fichier `index.html` self-contained (~900 KB)
- Vanilla JS, pas de framework
- Persistance en `localStorage` (clé `pa_*`)
- Hébergé sur GitHub Pages depuis la branche `main`

## Dev local

```bash
cd /path/to/Stride
python -m http.server 8765   # ou n'importe quel serveur statique
# → http://localhost:8765
```

L'app est mobile-first. Sur desktop (≥ 768px), le contenu est cadré dans une colonne de 480px pour conserver le feel "app".

## Reset

Pour repartir de zéro (efface tout l'historique local) : DevTools → Application → Local Storage → supprimer toutes les clés `pa_*`.
Ou dans la console : `Object.keys(localStorage).filter(k => k.startsWith('pa_')).forEach(k => localStorage.removeItem(k))`.

## Backup / restore

Export JSON via l'onglet Profil → "Exporter mes données". Import via le même onglet.

## Licence

Privé, usage perso.
