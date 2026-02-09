---
layout: page
title: Pièges
permalink: pieges.html
---

Attention, le travail avec Bricks peut comporter quelques pièges.

## Template des pages

En créant un Template simple pour les Pages, il est facile de commettre l'erreur suivante:

- Représenter le contenu avec un bloc **Post Content** (contenu de la publication) ayant **WordPress** comme Data source (source de donnés) uniquement.

Ce réglage pose problème dès que l'on édite le contenu de certaines pages avec Bricks. Le résultat:

![Erreur "Aucun contenu WordPress ajouté trouvé"](img/erreur-aucun-contenu.png)

**La solution:** ajouter un deuxième bloc **Post Content** ayant pour source de données **Bricks**.

Une explication en vidéo: 
[Bricks and Gutenberg content in the SAME Template](https://www.youtube.com/watch?v=5uAd9UOzXqk)

Pour mieux comprendre les principes des Templates, voir aussi l'article [An Intro To Templates](https://academy.bricksbuilder.io/article/an-intro-to-templates/) 