# Héberger l'application de présence (gratuit)

**Architecture :** page web sur GitHub Pages + données dans votre Google Sheet (Apps Script).
Coût : 0 €. Aucun serveur à gérer.

## Étape 1 – Le backend (Google Sheet + Apps Script) – 10 min
1. Importez `Publipostage_QR.xlsx` dans Google Drive → ouvrez avec Google Sheets
   (si vous l'avez déjà fait pour l'envoi des mails, utilisez la même feuille).
2. Extensions → Apps Script. Créez un fichier `Code.gs` et collez le contenu de `Code.gs`
   (il peut cohabiter avec le script d'envoi des mails).
3. Modifiez `PIN_AGENT` (pour les agents) et `PIN_ADMIN` (pour vous).
4. Sélectionnez la fonction `installer` → Exécuter → autorisez l'accès.
   Une feuille « Presences » et un dossier Drive « Signatures_NVIDIA_ISITCom » sont créés.
5. Déployer → Nouveau déploiement → ⚙ « Application Web »
   - Exécuter en tant que : **Moi**
   - Qui a accès : **Tout le monde**
   → Déployer, puis copiez l'URL qui finit par `/exec`.

## Étape 2 – La page web (GitHub Pages) – 5 min
1. Ouvrez `index.html` avec un éditeur de texte, remplacez
   `COLLEZ_ICI_L_URL_DE_VOTRE_APPS_SCRIPT/exec` par l'URL copiée.
2. Créez un compte gratuit sur github.com → New repository (ex. `presence-nvidia`), **Public**.
3. « uploading an existing file » → déposez `index.html` → Commit.
4. Settings → Pages → Source : `Deploy from a branch`, branche `main`, dossier `/ (root)` → Save.
5. Après 1–2 minutes, l'adresse s'affiche : `https://VOTRE-NOM.github.io/presence-nvidia/`

Alternative encore plus simple : app.netlify.com/drop → glissez le dossier contenant `index.html`.

## Étape 3 – Le jour J
- Envoyez l'adresse + le PIN agent aux agents. Sur le téléphone : ouvrir le lien, prénom + PIN,
  autoriser la caméra. Astuce : « Ajouter à l'écran d'accueil ».
- Scan en direct → fiche de l'étudiant → signature → « Valider ». « Étudiant suivant » relance la caméra.
- Toutes les présences arrivent en direct dans la feuille « Presences » (heure, agent, lien vers la signature).

## Bon à savoir
- La page est publique mais **sans le PIN, aucune donnée n'est visible** : ne diffusez le PIN qu'aux agents.
- Si vous modifiez `Code.gs` plus tard : Déployer → Gérer les déploiements → ✏ → Version : Nouvelle version
  (l'URL reste la même).
- Faites un test complet la veille avec 2 téléphones (un QR de test : le vôtre ou celui d'un étudiant,
  puis annulez la présence avec le PIN admin).
- Les présences déjà saisies dans la version Claude ne sont pas transférées : utilisez une seule version le jour J.
