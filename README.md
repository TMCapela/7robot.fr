# Code du site 7Robot avec gohugo

Ici se trouve la substantifique moelle du site 7robot.fr réalisé à partir du générateur de site statique [gohugo](https://gohugo.io/).
Je vais vous expliquer comment mettre à jour le site (ajouter des actualités, des articles).

## Installer Hugo sur votre ordinateur

Sur Debian et Ubuntu c'est plutôt simple et classique :
```
sudo apt-get hugo
```

Sur d'autres distributions, aller sur [la page dédiée](https://gohugo.io/getting-started/installing/#readout).

## Télécharger le repository sur votre machine

```
git clone https://github.com/ZeddRahl/7robot.fr.git
```

## Faire des modifications

Allez dans le dossier créé.
```
cd 7robot.fr
```

### ajouter un post

Allez dans le dossier content/actualites
```
cd content/actualites
```
Créez un fichier d'extention .md ayant pour nom l'adresse que vous désirez. Par exemple : nom_post.md deviendra https://www.bde.enseeiht.fr/clubs/robot/actualites/nom_post/. N'utilisez pas d'espaces ou de caractères exotiques.

Modifiez ce fichier à votre convenance en respectant la syntaxe des autres posts :
```
+++
title = "Titre du post"
dater = "1 Janvier 2019"
author = "Auteur"
weight = 112 *il suffit d'incrémenter de 1 par rapport au post précédent, je recommande de repartir de nX100 pour la nième année*
image = "/clubs/robot/img/articles/image_en_preview.jpg"
+++

<p>Texte du post soit en html, soit en Markdown (.md).
N'hésitez pas à ajouter des images et incruster des vidéos youtube.</p>

<p>Pour insérer une image en html : <img src="/clubs/robot/img/articles/image.jpg"/>.</p>

<p>Pour insérer une image en Markdown : ![Nom de l'image](/clubs/robot/img/nom_de_l_image.png).</p>

```

Ajoutez les images dans le dossier /static/img/articles

### Ajouter un article

Allez dans le dossier content/articles
```
cd content/articles
```
Créez un fichier d'extention .md ayant pour nom l'adresse que vous désirez. Par exemple : nom_article.md deviendra https://www.bde.enseeiht.fr/clubs/robot/articles/nom_article/. N'utilisez pas d'espaces ou de caractères exotiques.

Modifiez ce fichier à votre convenance en respectant la syntaxe des autres articles :
```
+++
title = "Titre de l'article"
dater = "1 Janvier 2019"
author = "Auteur"
+++

<p>Texte du post soit en html, soit en Markdown (.md).
N'hésitez pas à ajouter des images et incruster des vidéos youtube.</p>

<p>Pour insérer une image en html : <img src="/clubs/robot/img/articles/image.jpg"/>.</p>

<p>Pour insérer une image en Markdown : ![Nom de l'image](/clubs/robot/img/nom_de_l_image.png).</p>

```

Allez dans /data/work.yml
Créez un nouveau point :
```
- category: Mécanique, Electronique ou Informatique
  url: "/articles/nom_article"
  image: "/img/articles/image.jpg"
  name: Le nom de l'article
  description: > Une éventuelle description (pas très utile)
```

Ajoutez les images dans le dossier /static/img/articles

### Ajouter un meme

Allez dans /data/meme7.yml
Suivez le template, ajoutez les nouveautés en haut de la liste.

Ajoutez les images dans le dossier /static/img/memes

## Mettre à jour le site

### Générer le site statique

Allez dans le dossier 7Robotique
```
cd path/7Robot
```
Lancez la génération
```
hugo
```
Le dossier public sera mis à jour.
C'est ce dossier qu'on transferera sur le serveur FTP.

### Accéder au serveur FTP

Je vous renvoie à la [documentation](https://www.bde.enseeiht.fr/doc/ftp) très quali faite par net7.

### Transférer les fichiers

Un fois connectés, allez dans le dossier à distance /robot/www_public/ là vous verrez les fichiers tels que index.html, index.xml, les dossiers activites, actualités... que vous retrouvez aussi dans le dossier local /public.

Il suffit alors de transférer tout le contenu du dossier /public vers le dossier distant /robot/www_public/
Choisissez l'option "Overwrite" ou "Overwrite if different size or source newer" et cochez "Always use this action".

Vérifiez que tout se passe bien sur le vrai site [7robot.fr](7robot.fr).

Si vous avez des problèmes ou des questions, n'hésitez pas à me demander : tonymiguel.pintocapela@etu.enseeiht.fr
