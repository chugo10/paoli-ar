# Paoli 300 anni — prototype WebAR

## Contenu
- `index.html` : prototype MindAR + A-Frame + GSAP.
- `assets/banniere-paoli.png` : bannière de référence fournie.
- `assets/paoli.mind` : fichier cible à générer (non inclus).

## Étape 1 — Générer la cible image
1. Ouvrir le compilateur officiel MindAR : https://hiukim.github.io/mind-ar-js-doc/tools/compile/
2. Importer `assets/banniere-paoli.png`.
3. Lancer la compilation, vérifier la répartition des points caractéristiques.
4. Télécharger le fichier `.mind` et le renommer `paoli.mind`.
5. Le placer dans `assets/`.

Attention : la bannière est très panoramique (environ 7,8:1). Si le compilateur indique trop peu de points ou si le suivi est instable, tester une zone plus riche en détails (portrait + décor) comme image cible, sans modifier l'impression originale. Dans ce cas, il faudra aussi ajuster l'ancrage et les positions 3D.

## Étape 2 — Héberger en HTTPS
La caméra du téléphone exige généralement un contexte sécurisé HTTPS (ou localhost).
Déployer le dossier sur GitHub Pages, Netlify ou un autre hébergement HTTPS.
Ouvrir le lien sur :
- Android : Chrome
- iPhone : Safari

Autoriser l'accès à la caméra, puis viser la bannière imprimée ou affichée sur un autre écran.

## Étape 3 — Comprendre le prototype
Le personnage est pour l'instant une sculpture géométrique stylisée construite avec des primitives 3D. Ce n'est PAS un modèle historique fidèle de Pasquale Paoli.
Pour un rendu final convaincant, remplacer le groupe `#bust` par un modèle 3D `.glb` créé ou obtenu avec les droits nécessaires. Le scénario GSAP est déjà séparé de cette géométrie.

## Réglages importants
- `targetIndex: 0` : première image compilée.
- `#bust` : position de la sculpture (coordonnées relatives à la bannière).
- `#halo`, `#particles`, `#anniversary` : éléments de l'animation.
- `playSequence()` : séquence de 5 secondes.
- `targetFound` / `targetLost` : déclenchement et arrêt visuel au suivi de la bannière.

## Dépannage
- Écran noir : vérifier HTTPS, autorisation caméra et navigateur.
- Cible non reconnue : vérifier le fichier `paoli.mind`, la lumière, la netteté et la taille de la bannière dans le champ.
- Suivi instable : la bannière étant très panoramique et relativement peu haute, tester une cible plus détaillée centrée sur le portrait. Il est possible de garder la bannière complète comme visuel physique tout en utilisant un crop de référence, mais il faudra que ce crop soit visible dans la zone scannée.


## Cible MindAR intégrée
Le fichier `assets/paoli.mind` fourni a été ajouté au projet. L'application référence déjà ce chemin dans `index.html`.
