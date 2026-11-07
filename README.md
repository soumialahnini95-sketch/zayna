# Maison Zayna — version HTML/CSS/JS pour GitHub Pages

Ce dossier est une version statique autonome du site Maison Zayna. Il peut être ouvert dans Visual Studio Code et hébergé gratuitement avec GitHub Pages.

Il contient :

- `index.html` : la structure complète du site ;
- `style.css` : le design responsive ;
- `script.js` : changement français/anglais, recherche, filtres, FAQ et interactions ;
- `images/` : les images locales des logements et des destinations.

## 1. Préparer le dossier sur votre ordinateur

Téléchargez `dar-and-stay-static.zip`, puis décompressez-le. Le dossier obtenu doit contenir directement ces fichiers :

```text
index.html
style.css
script.js
README.md
images/
```

Important : `index.html` doit être à la racine du dossier publié. Il ne faut pas publier le dossier parent qui contient `static-site`, sinon GitHub Pages risque de ne pas trouver la page d’accueil.

## 2. Ouvrir le site dans Visual Studio Code

1. Installez [Visual Studio Code](https://code.visualstudio.com/) si nécessaire.
2. Ouvrez VS Code.
3. Cliquez sur **File → Open Folder**.
4. Sélectionnez le dossier qui contient `index.html`.
5. Installez l’extension **Live Server** de Ritwick Dey.
6. Faites un clic droit sur `index.html` puis choisissez **Open with Live Server**.

Le site s’ouvrira généralement à une adresse similaire à :

```text
http://127.0.0.1:5500
```

Vous pouvez aussi le tester sans extension avec Python :

```bash
cd chemin/vers/le/dossier
python3 -m http.server 5500
```

Puis ouvrez [http://localhost:5500](http://localhost:5500).

## 3. Installer Git

Si Git n’est pas encore installé :

- Windows : téléchargez [Git for Windows](https://git-scm.com/download/win) ;
- macOS : installez Git avec Xcode Command Line Tools ou [Homebrew](https://brew.sh/) ;
- Ubuntu / Debian :

```bash
sudo apt update
sudo apt install git
```

Vérifiez l’installation :

```bash
git --version
```

## 4. Créer le dépôt GitHub gratuitement

1. Connectez-vous à [github.com](https://github.com/).
2. Cliquez sur **New repository**.
3. Donnez-lui un nom, par exemple `dar-and-stay`.
4. Choisissez **Public** si vous souhaitez utiliser GitHub Pages gratuitement sans offre payante.
5. Ne cochez pas l’option de création automatique d’un README si vous allez envoyer ce dossier existant.
6. Cliquez sur **Create repository**.

GitHub affichera ensuite l’adresse de votre dépôt, par exemple :

```text
https://github.com/VOTRE-COMPTE/dar-and-stay.git
```

## 5. Envoyer le site avec VS Code ou le terminal

Ouvrez un terminal dans le dossier où se trouvent `index.html`, `style.css`, `script.js` et `images/`.

Exécutez les commandes suivantes en remplaçant l’URL par celle de votre dépôt :

```bash
git init
git add .
git commit -m "Add Maison Zayna website"
git branch -M main
git remote add origin https://github.com/VOTRE-COMPTE/dar-and-stay.git
git push -u origin main
```

Si Git demande votre identité lors du premier commit :

```bash
git config --global user.name "Votre nom"
git config --global user.email "vous@example.com"
```

GitHub peut demander une authentification. Pour une connexion HTTPS, utilisez votre compte GitHub et un **Personal Access Token** à la place de votre mot de passe. Vous pouvez aussi utiliser GitHub Desktop si vous préférez une interface graphique.

## 6. Activer GitHub Pages

Dans votre dépôt GitHub :

1. Ouvrez l’onglet **Settings**.
2. Dans la colonne de gauche, cliquez sur **Pages**.
3. Dans **Build and deployment**, choisissez **Deploy from a branch**.
4. Sélectionnez la branche `main`.
5. Sélectionnez le dossier `/ (root)`.
6. Cliquez sur **Save**.

Après quelques instants, GitHub affichera l’adresse publique du site. Elle ressemble généralement à :

```text
https://VOTRE-COMPTE.github.io/dar-and-stay/
```

Si votre dépôt s’appelle exactement `VOTRE-COMPTE.github.io`, l’adresse sera plus courte :

```text
https://VOTRE-COMPTE.github.io/
```

Le premier déploiement peut prendre quelques minutes. Actualisez la page **Settings → Pages** jusqu’à voir le lien **Visit site**.

## 7. Mettre le site à jour

Après avoir modifié un fichier dans VS Code :

```bash
git add .
git commit -m "Update Maison Zayna website"
git push
```

GitHub Pages republiera automatiquement la dernière version de la branche `main`. Si l’ancienne version reste visible, faites un rechargement forcé :

- Windows / Linux : `Ctrl + F5` ;
- macOS : `Cmd + Shift + R`.

## 8. Ajouter un domaine personnalisé gratuitement côté hébergement

GitHub Pages permet d’associer un domaine que vous possédez déjà, mais l’achat du nom de domaine n’est pas gratuit.

Dans **Settings → Pages → Custom domain** :

1. saisissez votre domaine, par exemple `www.darandstay.com` ;
2. cliquez sur **Save** ;
3. chez votre fournisseur de domaine, ajoutez un enregistrement `CNAME` vers `VOTRE-COMPTE.github.io` pour le sous-domaine `www` ;
4. attendez la propagation DNS ;
5. activez **Enforce HTTPS** une fois le certificat disponible.

Ne mettez pas les identifiants CMI, mots de passe ou clés secrètes dans ce dépôt public.

## 9. Problèmes fréquents

### La page affiche une erreur 404

Vérifiez que `index.html` est directement à la racine du dossier publié et que GitHub Pages utilise bien la branche `main` avec le dossier `/root`.

### Les images ne s’affichent pas

Les chemins doivent rester relatifs :

```html
<img src="images/hero.jpg" alt="...">
```

Ne remplacez pas ces chemins par `/images/hero.jpg` pour un dépôt GitHub Pages qui n’est pas un domaine racine.

### Le site affiche une ancienne version

Videz le cache du navigateur, vérifiez le dernier commit dans GitHub et attendez quelques minutes la fin du déploiement.

### Le bouton de réservation ne sauvegarde rien

Cette archive est un frontend statique. Elle peut afficher les logements, filtrer les résultats et recueillir une interaction côté navigateur, mais GitHub Pages ne fournit ni base de données ni serveur sécurisé.

## 10. Limites de cette version statique

L’export GitHub Pages ne peut pas exécuter :

- l’espace propriétaire sécurisé ;
- l’enregistrement réel des réservations ;
- l’authentification des propriétaires ;
- le paiement CMI ;
- les webhooks et la validation serveur.

Pour ces fonctions, utilisez la version serveur du projet Maison Zayna et connectez un hébergement avec backend et variables secrètes. Les identifiants CMI ne doivent jamais être placés dans `index.html`, `style.css`, `script.js` ou dans un dépôt GitHub public.
