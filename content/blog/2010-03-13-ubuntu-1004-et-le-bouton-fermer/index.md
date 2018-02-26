---
path: "/ubuntu-1004-et-le-bouton-fermer.html"
date: "2010-03-13T14:51Z"
title: "Ubuntu 10.04 et le bouton fermer"
tags: ["Design", "Général", "Linux"]
---

[![](http://2.bp.blogspot.com/_lEhuTvDBOnM/S5uPbBx46dI/AAAAAAAAAI8/Mv7IS3RoX3s/s200/80959-ubuntu.jpg)](http://2.bp.blogspot.com/_lEhuTvDBOnM/S5uPbBx46dI/AAAAAAAAAI8/Mv7IS3RoX3s/s1600-h/80959-ubuntu.jpg)

Comme tout bon informaticien qui se respecte, je suis l'évolution des technologies et notamment celle de Linux et Ubuntu (bien que je sois utilisateur de Windows 7). La prochaine version d'Ubuntu avec support étendu (LTS) sortira en avril, et sera l'occasion pour Canonical de renouveler l'aspect graphique de ses produits et sa marque. Ubuntu n'y manque pas et a le droit à un lifting.

Pour vous faire une idée, voici [le design actuel](http://www.ubuntu.com/) et [celui qui va le remplacer](http://www.pcinpact.com/actu/news/55688-ubuntu-1004-lightware-renouvellement-graphique-nouveau-theme.htm).

Je trouve (comme beaucoup de monde) que ce changement est très positif, par contre (comme beaucoup de monde) je n'adhère pas au placement des boutons minimiser, agrandir et fermer. Je ne discuterai pas du fait qu'ils soient placé à gauche, ça ne me gène pas trop et ca plaira aux utilisateurs de Mac, par contre le bouton fermer qui n'est pas dans le coin de la fenêtre mais proche du titre ne me plait pas du tout, c'est anti-ergonomique, quoi qu'en dise les experts d'ergonomie de chez Canonical.

Pourquoi je vous parle de ça ? Parce que j'ai trouvé une solution ! Comme le placement des boutons est le même quel que soit le thème, je me suis dit que c'était un paramètre général. Après un peu de recherche, je suis tombé sur [cet article](http://linux.leunen.com/?p=828) qui explique la marche à suivre :

> Faites ALT + F2, ou lancez un terminal
> Tappez gconf-editor
> Rendez vous à la clé : /apps/metacity/general/button_layout
> Modifiez la valeur en : menu:minimize,maximize,close

Normalement les boutons sont de retour à droite, dans le même ordre, ce qui redonnera au bouton fermer sa place d'origine. Il reste un point gênant mais on y peut rien : les boutons agrandir et minimiser sont inversés du coup, mais si vous modifiez l'ordre le thème par défaut ne ressemblera plus à rien. Il va falloir faire avec.

Ubuntu 10.04 ne sortira que fin avril, d'ici là Canonical aura peut-être revu sa position mais j'en doute fortement.
