---
title: Developper un skill pour Alexa
layout: post
categories: [python, cloud]
image: /assets/img/posts/alexaskill.png
description: "Creer son skill Alexa"
customexcerpt: "Découverte et création d'une application pour l'environnement Alexa, le tout hébergé dans AWS."
---

![Alexa skill](https://raw.githubusercontent.com/ArnaudLhutereau/arnaudlhutereau.github.io/main/assets/img/posts/alexaskill.png)

Depuis l'achat d'un appareil Amazon Echo Dot, je me suis toujours dit que je me pencherai sur le fonctionnement d'une application et la création d'une application pour tester mais c'est toujours resté dans ma TODO liste.

J'en ai essayé quelques-uns et comme dans n'importe quelle boutique d'applications en ligne (Play Store, App Store...), il y a de tout. Alexa dispose donc de sa propre boutique *([Lien](https://www.amazon.fr/b?ie=UTF8&node=13944548031))*, qui correspond à la catégorie "Alexa Skill". L'intallation es très simple. Il suffit de se rendre sur la page du skill et de cliquer sur le bouton "**Activer**". Il suffit ensuite de dire "Alexa, lance *{Nom du skill}*".

C'est en compagnie d'Etienne que j'ai découvert le fonctionnement d'un skill. L'objectif était de réaliser une application simple, mais fonctionnelle!

Cet article retrace donc la création du skill avec quelques commentaires sur des éléments que nous avons appris.

  
* hello
{:toc}


#### Les étapes dans l'utilisation d'un skill

Pour commencer, il faut partir du début et comprendre comment fonctionne un skill Alexa. Il faut savoir qu'aucune application ne tourne sur l'appareil Alexa. Tout est géré au niveau du Cloud, et l'appareil sert simplement d'interface audio pour interagir avec le Cloud.

Notre skill est donc stocké en dehors de l'appareil.

Un schéma explicatif tiré de la [documentation](https://developer.amazon.com/en-US/alexa/alexa-skills-kit/start#how-an-alexa-skill-works) d'Amazon illustre les étapes :

![enter image description here](https://d3ogm7ac91k97u.cloudfront.net/content/dam/alexa/alexa-skills-kit/diagram_all-skills-954x245-1.png)

La partie 2 "Skill Interaction Model" correspond au traitement de la voix qui est envoyé par l'appareil.
Ce qui est détecté est alors envoyé au skill qui correspond à la partie 3 "Skill Application Logic".
Cette partie contient le code de l'application.

Si on s'intéresse à cette partie, on distingue deux concepts :

![Alexa skill architecture](https://raw.githubusercontent.com/ArnaudLhutereau/arnaudlhutereau.github.io/main/assets/img/posts/alexaskillarchitecture.png)

Il est possible de stocker le code de l'application au sein du service Lambda d'AWS, ou bien de le stocker ailleurs, sur son propre serveur.
Dans cet article, nous utiliserons le serveur Lambda pour simplifier le test.


#### Création du skill
C'est très simple et très rapide. Il suffit d'un compte Amazon.
Rendez-vous dans l'interface "Alexa Developper Console" à ce lien : https://developer.amazon.com/alexa/console/ask.

Ensuite, il faut cliquer sur le bouton bleu "**Créer une skill**". Des informations sont demandées principalement au niveau architecure.
Il faut lui donner un **nom**, le **pays principal** puis le **modèle**. Des modèles prédéfinis sont proposés. Nous avons choisi "**Custom**" pour notre application de test.
Pour finir, l'hébergement du skill est évoqué. Il faut choisir où l'heberger :

 - Alexa-hosted (Lambda, Node.JS)
 - Alexa-hosted (Lambda, Python)
 - Provision your own

Pour simplifier la création, nous sommes partis sur "**Alexa-hosted**" en **Python** (<3).

#### L'interface

Article en cours de construction!

#### Le code

Article en cours de construction!

#### Les intents, slots...

Article en cours de construction!

#### Tester!

Article en cours de construction!

#### Annexes

- [Documentation Alexe](https://developer.amazon.com/en-US/alexa/alexa-skills-kit)
- [Tutoriel Amazon : Créer un skill](https://developer.amazon.com/en-US/alexa/alexa-skills-kit/get-deeper/tutorials-code-samples/build-an-engaging-alexa-skill)
- [Alexa Developer Consol](https://developer.amazon.com/alexa/console/ask)
