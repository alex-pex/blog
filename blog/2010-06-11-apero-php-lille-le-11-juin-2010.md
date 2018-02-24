---
path: "/apero-php-lille-le-11-juin-2010.html"
date: "2010-06-11T23:30Z"
title: "Apéro PHP - à Lille, le 11 juin 2010"
tags: ["Web"]
---

[![](https://1.bp.blogspot.com/_lEhuTvDBOnM/TBKb63QV1xI/AAAAAAAAALg/A7qcC6dCdRg/s200/biere.jpg)](http://1.bp.blogspot.com/_lEhuTvDBOnM/TBKb63QV1xI/AAAAAAAAALg/A7qcC6dCdRg/s1600/biere.jpg)

Ce soir s'est déroulé un [apéro PHP](http://aperophp.net/apero.php?id=742) sur Lille, au café citoyen. Je suis pas resté très longtemps, mais j'ai trouvé ça bien sympa. Et puis ça a été l'occasion de comprendre pourquoi PHP 6 (tel qu'il a été imaginé) ne sortira pas, et ce que nous réserve le "Core Group" pour l'évolution à venir du langage.

Je ne vais pas entrer dans les détails, ce que je retiendrai c'est l'introduction des [traits](http://wiki.php.net/rfc/traits), et l'utilisation directe des tableaux en sortie de fonction.

Pour les traits, au départ je voyais pas l'intérêt comparé à l'héritage multiple, mais j'avais oublié que PHP ne le gérai pas. J'ai également pensé aux interfaces, sauf que c'est complètement hors-sujet puisque l'intérêt de l'interface est de laisser la classe qui l'utilise la tâche d'implémenter les méthodes. Les traits sont comme une collection de méthodes qui viennent se greffer dans une classe. Il est également possible de définir des méthodes abstraites, ce qui permet (à mon sens) de créer de véritables petits plugins.

En ce qui concerne l'utilisation directe des tableaux en sortie de fonctions, c'est tout simplement une évidence. Avant, il était impossible de faire :

> $this->getArticles( )\[0\] = 'premier';

On devait faire :

> $articles = $this->getArticles( );
> $articles\[0\] = 'premier';

Enfin, on a parlé du dilemne du typage dans les paramètres de fonction. En gros :

> function fois_dix(int $num) { return $num * 10; }
> $nombre = "123";
> echo fois_dix( $nombre );

La question est : doit-on envoyer une erreur (ou une exception ! ;-) ), ou convertir silencieusement puisqu'au final ça change rien. Avant de venir, j'étais favorable au typage dur, et donc à l'envoi d'une erreur. Mais à y réfléchir, ce qui m'intéresse le plus c'est qu'on m'envoie un nombre et pas "hello", je me fiche un peu qu'il soit stocké sous forme de chaine ou de nombre. La discussion est ouverte, pour ma part j'ai déjà mon avis sur la question.
