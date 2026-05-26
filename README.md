# Stride

App fitness perso : 7 semaines de défis quotidiens calibrés (pompes, haut, bas, core) + rituels (eau, sommeil, marche, protéines) + suivi poids, photos, succès.

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
