# Portfolio Oumar Diakité

Site vitrine statique (une seule page `index.html` + médias). Aucune étape de build :
le rendu React/JSX est compilé côté navigateur du visiteur.

## Structure

```
index.html          → la page
support.js          → runtime (charge React/Babel depuis unpkg.com)
assets/             → images (.jpg / .png)
uploads/            → vidéos (.mp4)
.github/workflows/  → déploiement automatique GitHub Pages
```

## Déploiement

L'hébergement est géré par **GitHub Pages**, en automatique.

- À chaque `push` (ou merge d'une PR) sur la branche **`main`**, le workflow
  `.github/workflows/deploy-pages.yml` publie le site.
- Aucune commande à lancer : il suffit de mettre à jour les fichiers sur `main`.

**URL du site :** https://bratpreneur.github.io/portfoliooumar/

> Premier déploiement : le workflow tente d'activer GitHub Pages tout seul
> (`enablement: true`). Si jamais il échoue, activer manuellement une seule fois :
> **Settings → Pages → Build and deployment → Source : GitHub Actions**, puis
> relancer le workflow (onglet **Actions**).

## Ajouter un nom de domaine perso (plus tard)

C'est possible et gratuit (hors prix du domaine lui-même). Étapes :

1. **Settings → Pages → Custom domain** : saisir le domaine (ex. `www.oumardiakite.com`),
   puis **Save**. Cela crée un fichier `CNAME` à la racine du dépôt.
2. Chez le registrar (OVH, Gandi, Namecheap…), configurer le DNS :

   - **Sous-domaine `www`** → un enregistrement **CNAME** vers `bratpreneur.github.io`
   - **Domaine racine `oumardiakite.com`** → quatre enregistrements **A** :
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
     (et, pour l'IPv6, quatre enregistrements **AAAA** :
     `2606:50c0:8000::153`, `2606:50c0:8001::153`,
     `2606:50c0:8002::153`, `2606:50c0:8003::153`)
3. Attendre la propagation DNS (quelques minutes à quelques heures), puis cocher
   **Enforce HTTPS** dans Settings → Pages.

Les chemins des médias étant **relatifs**, le site fonctionne aussi bien sur
l'URL GitHub (`/portfoliooumar/`) que sur un domaine perso servi à la racine.
