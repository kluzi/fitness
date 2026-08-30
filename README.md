# Muscu Plan — 16 semaines

Programme de renforcement musculaire au poids du corps (3 séances/semaine, 20 min max),
pensé pour s'intégrer autour de 3 sorties running/semaine, sur 4 blocs de 4 semaines
alignés sur le calendrier de courses (Paris-Versailles 16K, 20K Paris, 10K Hoka).

Application 100% statique : une seule page `index.html` (HTML/CSS/JS inline),
sans backend, sans dépendance externe. Les données de progression sont stockées
en local dans le navigateur (`localStorage`).

## Tester en local

```bash
cd muscu-plan
python3 -m http.server 8080
```

Puis ouvrir http://localhost:8080 dans le navigateur (idéalement en vue mobile).

> Ouvrir directement le fichier `index.html` via `file://` fonctionne aussi dans la
> plupart des navigateurs, mais certains bloquent `localStorage` sur ce protocole —
> préférer un petit serveur local (comme ci-dessus) pour tester la persistance.

## Déployer sur Netlify

**Option A — Drag & drop (le plus simple, sans repo GitHub)**
1. Aller sur https://app.netlify.com/drop
2. Glisser-déposer le dossier du projet (contenant `index.html`)
3. Le site est en ligne immédiatement, avec une URL `*.netlify.app`

**Option B — Déploiement continu via GitHub (recommandé sur la durée)**
1. Créer un repo GitHub dédié (ex. `muscu-plan`)
2. Pousser ce dossier dessus :
   ```bash
   git init
   git add index.html netlify.toml README.md
   git commit -m "Programme muscu bodyweight 16 semaines"
   git remote add origin https://github.com/<user>/muscu-plan.git
   git push -u origin main
   ```
3. Sur Netlify : **Add new site → Import an existing project → GitHub** → sélectionner
   le repo. Build command : vide. Publish directory : `.`
4. Chaque `git push` redéploie automatiquement le site.

## Réinitialiser les données

Dans l'app, onglet **Progression → Réinitialiser toutes les données**
(ou vider le `localStorage` du site depuis les outils dev du navigateur).
