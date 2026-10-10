# Guide graphistes : préparer les visuels du générateur

Vous n'avez pas de code à écrire. Vous livrez **un dossier d'images aux noms précis** et un petit fichier texte de réglages.

## 1. Format

- Toutes les images font **exactement la même taille**, la même que `couverture/fond.png`.
- Taille conseillée : **1080 × 1350 px** (format portrait 4:5 d'Instagram).
- Format **PNG**. Les avant-plans doivent être **transparents** partout sauf sur leurs éléments.

## 2. Les fichiers à livrer (noms à respecter exactement)

| Fichier | Rôle |
|---|---|
| `couverture/fond.png` | Fond de la couverture (sous le logo ou la photo) |
| `couverture/avant-plan-un-lot.png` | Éléments au-dessus du logo (titre, bulle « vous fait gagner **un lot** »…), utilisé si le partenaire offre 1 exemplaire en tout |
| `couverture/avant-plan-des-lots.png` | Même chose, version « vous fait gagner **des lots** » |
| `couverture/zones.png` | Emplacement du logo et/ou de la photo (voir point 3) |
| `jeu/fond.png` | Fond d'une page jeu |
| `jeu/avant-plan.png` | *(facultatif)* Éléments posés au-dessus de la boîte |
| `jeu/zones.png` | Emplacements du nom du jeu, de la boîte et du nombre d'exemplaires |
| `pages-fixes/01-tombola.png`… | Pages identiques pour tous les partenaires, ajoutées à la fin du carrousel |
| `polices/titres.ttf` (ou `.otf`) | Police du nom du jeu et du nombre d'exemplaires |
| `reglages.txt` | Textes, couleurs et réglages (voir point 4) |

Ordre d'empilement : **fond → logo, photo ou boîte → textes → avant-plan**.

## 3. Dessiner les zones (`zones.png`)

Sur un calque transparent au format du visuel, dessinez des **aplats de couleur pure** à l'endroit où l'outil doit placer chaque élément :

| Couleur | Code | Ce que l'outil y place |
|---|---|---|
| 🟥 Rouge | `#FF0000` | Le **logo** (agrandi au maximum sans être déformé, centré) |
| 🟦 Bleu | `#0000FF` | La **photo** (dessinez un cercle : l'outil reprend son diamètre) |
| 🟩 Vert | `#00FF00` | Le **nom du jeu** (taille ajustée automatiquement, 2 lignes au maximum) |
| 🟪 Violet | `#8000FF` | La **boîte du jeu** |
| 🟨 Jaune | `#FFFF00` | Le texte « **10 exemplaires à gagner !** » |

- Rouge et bleu vont dans `couverture/zones.png`. Si vous n'en dessinez qu'un, seul le mode correspondant (marque ou personne) sera proposé.
- Vert, violet et jaune vont dans `jeu/zones.png`.
- Un seul aplat par couleur. Seul le rectangle qui l'englobe compte.
- Pas de dégradé, pas d'ombre, pas d'anti-crénelage gênant : ce sont de simples aplats.

## 4. Le fichier `reglages.txt`

Ouvrez-le avec un simple éditeur de texte (Bloc-notes, TextEdit). Écrivez une ligne par réglage, sous la forme `NOM : valeur`. Les lignes qui commencent par `#` sont des commentaires. Si vous supprimez une ligne, l'outil utilise la valeur par défaut.

| Réglage | Exemple | À quoi ça sert |
|---|---|---|
| NOM DE L'ÉVÉNEMENT | Blague Friday | En-tête de la page et nom des fichiers |
| ANNÉE | 2026 | Idem |
| POLICE | titres.ttf | Nom du fichier de police, placé dans `polices/` |
| PAGES FIXES | 01-tombola.png, 02-live.png | Pages ajoutées à la fin, dans cet ordre |
| COULEUR DU NOM DU JEU | #FFFFFF | |
| NOM DU JEU EN MAJUSCULES | oui | oui / non |
| COULEUR DU NOMBRE D'EXEMPLAIRES | #FFE58A | |
| TEXTE POUR 1 EXEMPLAIRE | 1 exemplaire à gagner ! | |
| TEXTE POUR PLUSIEURS | [n] exemplaires à gagner ! | `[n]` est remplacé par le nombre |
| NOMBRE MAXIMUM DE JEUX | 17 | Un carrousel compte 20 pages au maximum |
| COULEUR DU CONTOUR PHOTO | #FFFFFF | Contour de la photo ronde |
| ÉPAISSEUR DU CONTOUR PHOTO | 12 | en px, 0 = pas de contour |
| COULEUR DU CARTOUCHE DE SECOURS | #FFFFFF | Fond ajouté derrière un logo illisible |
| ARRONDI DU CARTOUCHE | 24 | en px |
| MARGE DU CARTOUCHE | 30 | en px |
| SEUIL DE LISIBILITÉ | 2.5 | Contraste minimal entre le logo et le fond (3 = plus exigeant) |
| TAILLE MINIMALE DU LOGO | 800 | en px |
| TAILLE MINIMALE DE LA PHOTO | 800 | en px |
| TAILLE MINIMALE DE LA BOÎTE | 1000 | en px, sur le côté le plus grand |
| COULEUR DE L'INTERFACE | #2783DE | Couleur des boutons de l'outil |

## 5. Vérifier votre dossier avant de le livrer

1. Ouvrez l'outil en ajoutant **`#gabarit`** à la fin de son adresse.
2. Cliquez sur **« Choisir mon dossier de visuels »** et sélectionnez votre dossier. Il reste sur votre ordinateur : rien n'est envoyé.
3. Lisez le rapport. Corrigez tout ce qui est en rouge. Les messages en orange sont des conseils.
4. Cliquez sur **« Remplir avec des exemples »** et cochez **« Afficher les zones »** pour vérifier le rendu avec un faux logo, une boîte et un nom de jeu très long.
5. Quand tout est vert, livrez le dossier à l'association.

## 6. Police

Vérifiez que la licence de la police autorise l'usage **web / webfont**, car le fichier est mis en ligne avec l'outil.
