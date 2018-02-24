---
path: "/le-phishing-20-le-tabjacking.html"
date: "2010-05-26T23:50Z"
title: "Le Phishing 2.0 = Le Tabjacking"
tags: ["Web"]
---

[![](https://4.bp.blogspot.com/_lEhuTvDBOnM/S_2VqJyA-qI/AAAAAAAAALQ/St-N2GXNttE/s200/phishing.png)](http://4.bp.blogspot.com/_lEhuTvDBOnM/S_2VqJyA-qI/AAAAAAAAALQ/St-N2GXNttE/s1600/phishing.png)

Une nouvelle inquiétante : une nouvelle technique de Phishing vient d'apparaitre, particulièrement efficace.

Dans les scénarios classiques de [Phishing](http://fr.wikipedia.org/wiki/Hame%C3%A7onnage), l'élément clé qui va déclencher l'échec de la manœuvre est le sentiment qu'on n'est pas sur le bon site. Ce qui est terriblement vicieux dans cette nouvelle technique est que vous arrivez tranquillement sur un site authentique, puis vous changez d'onglet et continuez de surfer, le script détecte que vous n'êtes pas en train de regarder le site infecté et change le contenu de la page. En revenant sur vos onglets ouverts, vous voyez que êtes déconnecté de Facebook par exemple, vous vous reconnectez machinalement et PAF ! Vous vous êtes fait avoir, on vous a piqué votre compte Facebook.

Cette technique est efficace car il nous viendrait pas à l'esprit qu'un onglet change brusquement de contenu derrière notre dos. La seule façon de ne pas se faire avoir, en dehors de redoubler de vigilance, est de désactiver le javascript. Moins radical, les prochaines versions de Firefox [esquissent l'idée](http://hacks.mozilla.org/2010/04/account-manager-coming-to-firefox/) que ce ne serait plus à l'utilisateur de s'authentifier mais directement le navigateur. Ainsi l'utilisateur n'a plus à se faire piéger, mais ça sous entend également que la connexion doit être particulièrement sécurisée puisqu'aucune intervention n'est nécessaire.

Si mes explications ne sont pas claires ou si vous voulez en savoir plus, lisez [les explications de Korben](http://www.korben.info/tabjacking-phishing.html), et si vous voullez essayer, cliquez [sur ce lien](http://www.azarask.in/blog/post/a-new-type-of-phishing-attack/) (allez dessus, puis changez d'onglet et attendez 5 secondes). J'ai pu le reproduire sur IE8, Firefox 3.6 mais pas toujours sur Chrome 4, ou sans la favicon. Ca vient d'un bug de Chrome, dans les dernières version c'est corrigé et donc vous pourrez bientôt pleinement vous faire arnaquer.

[A New Type of Phishing Attack](http://vimeo.com/12003099) from [Aza Raskin](http://vimeo.com/user532161) on [Vimeo](http://vimeo.com/).
