# Chef d'Entrepôt — application Android

Le jeu tourne dans une WebView Android, en plein écran et hors ligne. La partie est sauvegardée sur le téléphone.

## Obtenir l'APK avec GitHub

1. Crée un dépôt sur GitHub (privé ou public).
2. Envoie tout le contenu de ce dossier dans le dépôt, y compris le dossier caché `.github`.
   - Depuis le site : « Add file » → « Upload files », puis glisse le contenu du dossier (pas le dossier lui-même).
   - En ligne de commande :
     ```
     git init
     git add .
     git commit -m "Chef d'Entrepôt"
     git branch -M main
     git remote add origin https://github.com/TON-COMPTE/chef-entrepot.git
     git push -u origin main
     ```
3. L'onglet **Actions** du dépôt lance « Construire l'APK » (3 à 5 minutes).
4. Une fois terminé, l'APK est dans **Releases** (colonne de droite du dépôt) : `chef-entrepot.apk`.
   Ouvre ce lien depuis ton téléphone pour le télécharger directement.

## Installer sur le téléphone

Ouvre `chef-entrepot.apk` ; Android demande d'autoriser l'installation depuis le navigateur ou le gestionnaire de fichiers : accepte, puis installe.

## Mettre à jour le jeu

Remplace `app/src/main/assets/index.html`, `bg.png` et `sprites.png` par la nouvelle version, augmente `versionCode` dans `app/build.gradle`, puis pousse sur GitHub : un nouvel APK est construit automatiquement. Sans changement de clé de signature, la mise à jour conserve la sauvegarde.

## À savoir

- L'APK est signé avec la clé `app/chef-entrepot.jks` incluse dans le projet : chaque nouvelle version s'installe par-dessus l'ancienne et garde la sauvegarde. Garde ce fichier tel quel.
- Cette clé et son mot de passe sont visibles dans le projet : très bien pour un usage perso ou entre amis. Pour le Google Play Store, crée une clé privée (non publiée) et un fichier `.aab` (`gradle bundleRelease`).
