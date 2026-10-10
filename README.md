# Générateur de visuels partenaires

Une page web toute simple : le partenaire ajoute son logo (ou sa photo) et ses jeux, et télécharge son carrousel Instagram prêt à publier.

- **Un seul fichier** (`index.html`) + un dossier d'images (`visuels/`). Aucun serveur, aucune base de données, aucune dépendance.
- **Rien n'est envoyé ni stocké** : tout est calculé dans le navigateur du partenaire. Pas de cookie, pas de RGPD à gérer.
- **Pas d'IA** : le détourage se fait par « fond uni » (baguette magique) ou en cliquant les coins de la boîte.
- Hébergement gratuit sur **GitHub Pages**.

> Les visuels fournis dans `visuels/` sont des **visuels de démonstration**. Les graphistes doivent les remplacer (voir `GUIDE-GRAPHISTES.md`).

---

## Contenu du dossier

```
index.html               ← l'outil (ne pas toucher, sauf le dev)
README.md                ← ce fichier
GUIDE-GRAPHISTES.md      ← à donner aux graphistes
visuels/
  reglages.txt           ← textes, couleurs, police… en français
  polices/titres.ttf
  couverture/fond.png
  couverture/avant-plan-un-lot.png
  couverture/avant-plan-des-lots.png
  couverture/zones.png
  jeu/fond.png
  jeu/avant-plan.png
  jeu/zones.png
  pages-fixes/01-tombola.png
  pages-fixes/02-live.png
```

## Ce que fait l'outil

1. **Couverture** : « Je suis une marque » (logo) ou « Je suis une personne » (photo ronde, zoom + glisser).
   - Le logo est posé tel quel, sans bloc derrière.
   - Si le logo est transparent, l'outil mesure le contraste avec **les vrais pixels du fond**. S'il ressort mal, le téléchargement est bloqué jusqu'à ce que le partenaire ajoute le cartouche de secours ou envoie une autre version du logo.
   - Un logo non transparent (JPG) est affiché comme un cartouche aux coins arrondis.
   - L'avant-plan change selon le total : « un lot » (1 exemplaire en tout) ou « des lots ».
2. **Jeux** : une page par jeu (nom, nombre d'exemplaires, photo de la boîte).
   - Un PNG déjà détouré est accepté directement.
   - Sinon, le partenaire doit détourer la boîte dans l'outil avant de pouvoir télécharger.
   - Taille minimale vérifiée pour éviter le flou.
3. **Téléchargement** : un ZIP `blague-friday-2026-nom-du-partenaire.zip` (couverture + jeux + pages fixes, 20 pages max), ou bien les pages une par une (pratique sur iPhone).

---

## Mettre en ligne sur GitHub Pages (≈ 10 min, sans ligne de commande)

1. Créez un compte sur github.com (gratuit) si besoin.
2. Cliquez sur **New repository**, donnez-lui un nom (ex. `visuels-blague-friday`) et choisissez **Public**. La version gratuite de GitHub Pages demande un dépôt public : ce n'est pas un problème, car il ne contient que des visuels destinés à être publiés.
3. Dans le dépôt, cliquez sur **Add file → Upload files** et glissez-déposez **tout le contenu** du dossier (`index.html`, `visuels/`…). Validez avec **Commit changes**.
4. Ouvrez **Settings → Pages**. Dans « Branch », choisissez `main` et `/ (root)`, puis cliquez sur **Save**.
5. Après une minute ou deux, l'adresse s'affiche, par exemple `https://votre-compte.github.io/visuels-blague-friday/`. C'est le lien à envoyer aux partenaires.

**Adresse personnalisée (facultatif)** : dans **Settings → Pages → Custom domain**, indiquez par exemple `visuels.blaguefriday.fr`, puis ajoutez chez votre hébergeur de nom de domaine un enregistrement CNAME qui pointe vers `votre-compte.github.io`.

### Mettre à jour les visuels

Refaites **Add file → Upload files** avec les nouveaux fichiers, en gardant **les mêmes noms**. Ils remplacent les anciens. Le site est à jour en une ou deux minutes.

### Espace graphistes

Ajoutez `#gabarit` à la fin de l'adresse : `https://…/visuels-blague-friday/#gabarit`.
Les graphistes peuvent y choisir leur dossier **depuis leur ordinateur** (rien n'est envoyé), lire un rapport d'erreurs en français, afficher les zones et tester avec de faux logos et de faux jeux.

## Tester sur son ordinateur

Si vous ouvrez `index.html` par un double-clic, le navigateur bloque la lecture du dossier `visuels/`. Deux solutions :
- ouvrez `index.html#gabarit` et choisissez le dossier `visuels/` à la main ;
- ou lancez un petit serveur dans le dossier : `python3 -m http.server 8000`, puis ouvrez http://localhost:8000.

## Points de vigilance

- **Licence de la police** : la police est intégrée à une page web publique. Vérifiez que sa licence autorise l'usage « web / webfont » (c'est le cas des polices Google Fonts, par exemple).
- **Limites GitHub Pages** : 1 Go par site et environ 100 Go de trafic par mois. C'est très large pour quelques images.
- **Navigateurs** : Chrome, Edge, Firefox et Safari récents, sur ordinateur et sur mobile.

## Pour le développeur

- Tout se trouve dans `index.html` : HTML, CSS et environ 900 lignes de JavaScript sans framework, commentées et découpées en 12 sections.
- Les zones sont lues dans `zones.png` (aplats de couleurs pures, tolérance de 70 sur la distance RGB) et réduites à leur rectangle englobant.
- Le ZIP est écrit à la main, sans compression (le PNG est déjà compressé), avec le CRC32 et des noms de fichiers en UTF-8.
- Aucune requête réseau à part la lecture de `visuels/` sur le même site.
