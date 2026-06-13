# 🚀 Déployer l'app Richard sur le web (GitHub Pages)

Ce dossier `deploy/` est **prêt à publier**. Il contient :
- `index.html` — l'application (copie de `richard.html`, renommée pour une URL propre)
- `.nojekyll` — évite que GitHub bidouille le fichier

Objectif : avoir une **URL fixe** (ex : `https://lucas.github.io/richard/`) que Richard ouvre sur son téléphone et **ajoute à l'écran d'accueil**. Avantage : on peut **mettre à jour l'app sans jamais perdre ses données** (voir plus bas).

---

## 1. Publier (une seule fois) — ~5 minutes

1. Crée un compte sur **https://github.com** (gratuit) si tu n'en as pas.
2. Clique **New repository** (bouton vert).
   - **Repository name** : `richard` (par exemple)
   - Coche **Public** · ne coche rien d'autre · **Create repository**
3. Sur la page du repo vide : **« uploading an existing file »**.
   - Glisse-dépose **le contenu de ce dossier `deploy/`** : `index.html` **et** `.nojekyll`.
   - (Si `.nojekyll` est invisible, ce n'est pas grave, il est optionnel.)
   - **Commit changes**.
4. Onglet **Settings** → menu de gauche **Pages**.
   - **Source** : `Deploy from a branch`
   - **Branch** : `main` · dossier `/ (root)` · **Save**.
5. Attends ~1 minute, recharge la page **Pages** : l'URL apparaît en haut
   → `https://<ton-pseudo>.github.io/richard/`

C'est en ligne. 🎉

---

## 2. Installer sur le téléphone de Richard

1. Ouvre l'URL dans **Safari (iPhone)** ou **Chrome (Android)**.
2. **Partager → « Ajouter à l'écran d'accueil »**.
3. L'app s'ouvre en plein écran, avec l'icône PULSO et le nom **Richard**.

Les données sont stockées **dans le navigateur du téléphone** (hors-ligne, aucun compte).

---

## 3. ⭐ Mettre à jour l'app SANS perdre les données de Richard

Les données vivent dans le `localStorage` du navigateur, **rattachées à l'URL** (pas au fichier).
Tant que l'**URL ne change pas** et que la clé interne reste `richard_personal_v1` (c'est garanti), **les données restent** à chaque mise à jour.

**Procédure de mise à jour :**
1. On modifie `richard.html` (le fichier de travail).
2. On recopie la nouvelle version dans `deploy/index.html`.
3. Sur GitHub : repo → `index.html` → ✏️ (edit) → coller le nouveau contenu → **Commit**.
   *(ou réuploader le fichier).*
4. Richard **rafraîchit** la page (ou rouvre l'app) → nouvelle version, **données intactes**.
   La fonction `migrate()` ajoute automatiquement les nouveaux champs aux anciennes données.

> 🔒 **Filet de sécurité** : avant une grosse mise à jour, demande à Richard de faire
> **⋯ → Dados & backup → « 📤 Salvar cópia »** (envoi vers Drive/iCloud). En cas de pépin,
> **« 📂 Restaurar »** remet tout, et la migration le met à niveau.

**À ne JAMAIS changer** (sinon les données seraient « perdues » car rattachées ailleurs) :
- l'**URL** du site,
- la clé `localStorage` `richard_personal_v1`.

---

## 4. Sauvegarde des données (rappel)

- ⋯ → **Dados & backup** :
  - **📤 Salvar cópia** → partage le backup JSON (Drive / iCloud / WhatsApp / mail)
  - **📂 Restaurar** → réimporte un backup (mis à niveau automatiquement)
  - **💾 Baixar JSON** / **📊 CSV**
- La date de dernière copie est affichée et passe en **orange après 7 jours**.
- Un bandeau de rappel apparaît après 25 modifications sans sauvegarde.

La version installée est indiquée dans **Configurações** (actuellement **v1.2**).
