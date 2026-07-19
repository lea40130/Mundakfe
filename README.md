# Site Munda Kfé — projet test

## Structure

```
index.html                 → le site (une seule page)
images/                    → logo + photos du restaurant
data/menu-du-jour.json     → le menu du jour (modifié via /patrons)
patrons/                   → back-office pour changer le menu du jour
  index.html                 (interface Decap CMS)
  config.yml                 (champs éditables)
```

## Déploiement (voir le guide complet donné dans la conversation)

1. Créer un repo GitHub et y pousser tout ce dossier.
2. Créer un compte Netlify → "Add new site" → "Import an existing project" → choisir le repo.
   Build command : laisser vide. Publish directory : `.` (racine).
3. Dans Netlify : **Site configuration → Identity → Enable Identity**.
   - Registration preference : **Invite only**.
   - Services → Git Gateway → **Enable Git Gateway**.
4. **Identity → Invite users** → inviter l'email du restaurant. Ils reçoivent un lien pour choisir leur mot de passe.
5. Aller sur `https://VOTRESITE.netlify.app/patrons/`, se connecter, modifier le menu du jour, cliquer "Publier".
   → `data/menu-du-jour.json` est mis à jour sur GitHub, Netlify republie automatiquement (~30-60 secondes).
6. Une fois validé, brancher un nom de domaine dans **Domain settings**.

## Test en local

Le site utilise `fetch()` pour charger le menu du jour, ce qui ne fonctionne pas en ouvrant
juste le fichier `index.html` (protocole `file://`). Pour tester en local :

```bash
cd munda-kfe-site
python3 -m http.server 8000
# puis ouvrir http://localhost:8000
```

## À vérifier avant mise en ligne définitive

- Adresse : 38 Boulevard François Mitterrand, 40130 Capbreton (corrigé depuis la carte PDF qui indiquait 40230)
- Horaires (section Infos) — à confirmer avec l'équipe
- Avis clients (section Avis) — actuellement des exemples fictifs à remplacer
- Formats des vins (verre / demi / bouteille) — reconstruits depuis le PDF, à vérifier
- Photos actuelles en basse résolution (240-320px) — fonctionnent pour ce test, mais pour le
  site définitif, des photos en plus haute résolution rendraient beaucoup mieux
