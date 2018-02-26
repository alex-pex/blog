---
path: "/nautilus-elementary.html"
date: "2010-05-22T00:33Z"
title: "Nautilus Elementary"
tags: ["Linux"]
---

[![](https://3.bp.blogspot.com/_lEhuTvDBOnM/S_b_S-w_XdI/AAAAAAAAAKw/LUN1N8VmBek/s200/Capture-alexandre%C2%A0-%C2%A0Navigateur+de+fichiers-3.png)](http://3.bp.blogspot.com/_lEhuTvDBOnM/S_b_S-w_XdI/AAAAAAAAAKw/LUN1N8VmBek/s1600/Capture-alexandre%C2%A0-%C2%A0Navigateur+de+fichiers-3.png)

Pour ceux qui comme moi apprécient Gnome et Nautilus, mais n'apprécient pas la place perdue de base avec toutes les barres d'outils, j'ai la solution !

En installant le PPA de [Nautilus Elementary](https://launchpad.net/nautilus-elementary) vous aurez accès à de nouvelles options et une présentation plus compacte. Rien de plus simple :

```bash
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade
```

A la prochaine mise à jour, le patch de Nautilus sera appliqué. Le mieux est de redémarrer après pour voir les changements. Et ne pas oublier que de nouvelles options sont disponibles.
Si ça ne vous plait pas, pour le désinstaller il faudra utiliser [PPA Purge](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html).

Ca vous plait ? Il est possible d'aller plus loin en utilisant les "[breadcrumbs](http://translate.google.fr/translate_t?hl=fr&q=breadcrumbs)". Le mieux est d'utiliser ces commandes :

```bash
cd ~
wget http://gnaag.k2city.eu/nautilus-breadcrumbs-hack.tar.gz
tar -xvf nautilus-breadcrumbs-hack.tar.gz
```

Ensuite recharger le thème et activer l'option dans Nautilus.

Que dire de plus ? Ah si, j'ai une série d'image à vous montrer :

* [Nautilus de base](http://2.bp.blogspot.com/_lEhuTvDBOnM/S_cGuNKIkpI/AAAAAAAAAK4/R3jBGTqBH_0/s1600/Capture-alexandre%C2%A0-%C2%A0Navigateur+de+fichiers-1.png)
* [Nautilus Elementary](http://1.bp.blogspot.com/_lEhuTvDBOnM/S_cG-zA4PlI/AAAAAAAAALA/Bvfixrrzopk/s1600/Capture-alexandre%C2%A0-%C2%A0Navigateur+de+fichiers-2.png)
* [Nautilus Elementary + Breadcrumbs + Tweaks](http://3.bp.blogspot.com/_lEhuTvDBOnM/S_b_S-w_XdI/AAAAAAAAAKw/LUN1N8VmBek/s1600/Capture-alexandre%C2%A0-%C2%A0Navigateur+de+fichiers-3.png)

Et pour finir : si ça vous intrigue pour la dernière image j'ai utilisé le thème "[Ambiance Soft](http://gnome-look.org/content/show.php/Ambiance+Soft+-+normal+and+windowapplets?content=124623)" qui est plus sympa que l'original je trouve.
