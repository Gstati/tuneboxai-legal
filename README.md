# TuneBoxAI Legal Pages — Deploy Guide

Privacy Policy + Terms of Service hébergés sur GitHub Pages.

URLs finales (après déploiement) :
- **Privacy Policy** : `https://gnalita.github.io/tuneboxai-legal/privacy.html`
- **Terms of Service** : `https://gnalita.github.io/tuneboxai-legal/terms.html`
- Landing : `https://gnalita.github.io/tuneboxai-legal/`

Ces URLs iront dans le formulaire de soumission Play Console.

---

## Étape 1 — Créer le repo GitHub (5 min)

1. Va sur https://github.com/new
2. **Repository name** : `tuneboxai-legal`
3. **Public** (obligatoire pour GitHub Pages gratuit)
4. **NE coche pas** "Add README" / "Add .gitignore" → on push depuis ce dossier
5. Clique **Create repository**

## Étape 2 — Push les fichiers

Dans un terminal, depuis le dossier `TuneBoxAI/legal/` :

```bash
cd legal
git init
git add .
git commit -m "Initial: privacy policy + terms of service"
git branch -M main
git remote add origin https://github.com/gnalita/tuneboxai-legal.git
git push -u origin main
```

## Étape 3 — Activer GitHub Pages

1. Sur le repo GitHub : **Settings** (en haut à droite)
2. Sidebar gauche → **Pages**
3. **Source** : Deploy from a branch
4. **Branch** : `main` / `/ (root)` → **Save**
5. Attends 1-2 min, GitHub te donne l'URL : `https://gnalita.github.io/tuneboxai-legal/`

## Étape 4 — Vérifier

Ouvre les 3 URLs dans ton navigateur :
- https://gnalita.github.io/tuneboxai-legal/
- https://gnalita.github.io/tuneboxai-legal/privacy.html
- https://gnalita.github.io/tuneboxai-legal/terms.html

Tu dois voir les pages en thème sombre violet/rose avec EN + FR, sommaire cliquable.

## Étape 5 — Envoyer les URLs à Claude

Quand c'est en ligne, dis-moi et on passe au **#2 GDPR account deletion** dans l'app.

---

## Maintenir à jour

Pour modifier une page : édite le HTML, commit, push. GitHub Pages se met à jour automatiquement en ~1 min.

```bash
# après modif locale
git add .
git commit -m "Update privacy policy: add Sentry processor"
git push
```

## Custom domain (plus tard)

Quand tu auras configuré `tuneboxai.com`, tu pourras pointer les pages vers ton domaine :
- Repo GitHub → Settings → Pages → Custom domain : `legal.tuneboxai.com`
- Côté DNS : ajouter un CNAME `legal` → `gnalita.github.io`

Les URLs deviennent `https://legal.tuneboxai.com/privacy.html` (plus pro).

---

## Contenu inclus

### Privacy Policy (`privacy.html`)
- 13 sections RGPD + CCPA
- EN + FR sur la même page
- Couvre : data collected, purposes, legal basis, sharing (Supabase/Stripe/Jamendo), retention, droits utilisateur, CNIL, cookies, sécurité

### Terms of Service (`terms.html`)
- 14 sections
- EN + FR
- Couvre : acceptation, éligibilité, account, IP, abonnements, dons, usages interdits, contenu tiers, résiliation, disclaimers, limitation responsabilité (€100 max), droit français + ODR EU

### Design
- Style sombre cohérent avec l'app (violet/rose gradient)
- Responsive mobile + desktop
- Sommaire cliquable
- Pas de tracking / analytics tiers

---

## Points à valider plus tard

⚠️ Ces pages mentionnent des éléments qui dépendent de l'évolution du produit. À updater quand :
- **Sentry est branché** → ajouter Sentry dans la liste des sous-traitants (Privacy §5)
- **Mubert/Suno branchés** → ajouter dans Privacy §5 + Terms §4
- **Push notifs branchées** → ajouter token push dans Privacy §2
- **Custom domain** → mettre à jour les URLs partout
- **Forme juridique créée** (auto-entrepreneur / SAS) → mettre à jour "Data controller" Privacy §1 avec le numéro SIREN
