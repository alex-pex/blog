---
path: "/symfony-day-1-parlons-en.html"
date: "2010-03-16T22:49Z"
title: "Symfony - Day 1 - Parlons-en ..."
tags: ["Web"]
---

[![](https://2.bp.blogspot.com/_lEhuTvDBOnM/S5_U9TOn4lI/AAAAAAAAAJQ/nXrevsBOWAM/s200/9782918390169-3d.jpg)](http://2.bp.blogspot.com/_lEhuTvDBOnM/S5_U9TOn4lI/AAAAAAAAAJQ/nXrevsBOWAM/s1600-h/9782918390169-3d.jpg)

**EDIT : J'ai créé** [**un deuxième post**](2010-05-08-symfony-day-1-parlons-en-encore.md) **qui résume mieux le jour 1 de Symfony. Il faut dire que depuis ce post la formation a commencé chez Proweb.**

Ca y est, je m'y suis mis ! J'ai commencé l'apprentissage de [Symfony](http://www.symfony-project.org/) (par moi même, c'est pas encore le moment pour moi chez Proweb ...).

J'ai commencé le très bon [guide du développeur débutant sur Symfony](http://www.symfony-project.org/jobeet/1_4/Doctrine/fr/) (à réserver aux connaisseurs de PHP5 et de la programmation orientée objet tout de même). Ce guide est découpé en cours journaliers, qui durent environ 2-3 heures chacun ... si on ne reste pas coincé dès le premier cours !

En effet, le premier jour est consacré à la configuration du serveur, et le tuto est largement orienté serveur Linux. Je vais vous donner des astuces pour commencer le projet sur Windows.

**Installation d'Apache, Mysql et PHP grâce à WAMP**

Récupérez et installez [WampServer](http://www.wampserver.com/download.php) sur le site officiel. Je vous recommande de ne pas choisir Firefox comme navigateur et laisser explorer.exe, et bien paramétrer le serveur smtp pour la fonction mail().

**Installation de PEAR et configuration de PHP**

Si l'idée vous en dit d'installer Pear c'est là que la première blague se glisse. Allez dans C:\\wamp\\bin\\php\\php5.3.0, editez go-pear.bat et modifiez :
%PHP\_BIN% -d output\_buffering=0 PEAR\\go-pear.phar
en :
%PHP\_BIN% -d output\_buffering=0 -d phar.require_hash=0 PEAR\\go-pear.phar
puis lancez le, faites "entrée" tout du long pour installer PEAR automatiquement. Il faut modifier la ligne de commande car la signature de l'installeur inclus dans Wamp n'est pas correct, il faut passer outre.

Aussi, si vous choisissez d'utiliser Propel plutôt que Doctrine (je vous le déconseille), lancez wamp, faitez un clic simple sur l'icone pour faire apparaitre le menu, puis PHP -> PHP extensions -> php\_xsl pour activer l'extension. Modifiez également C:\\wamp\\bin\\php\\php5.3.0\\php.ini et décommentez la ligne de php\_xsl pour activer l'extension en ligne de commande. PHP XSL est nécessaire à Propel, mais Propel est amené à disparaitre, Symfony ne l'utilisera plus à partir de la version 2.

**Pratical Symfony - Day 1**

Je vous laisse découvrir [le tuto](http://www.symfony-project.org/jobeet/1_4/Doctrine/fr/01). Sachez deux choses :

- si votre configuration locale ne vous permet pas d'avoir APC et POSIX, c'est pas grave. APC permet à votre code d'être plus rapidement traité (en gérant un cache des fichiers php précompilés) et POSIX d'afficher des couleurs dans l'invite de commande, rien de bien méchant.

- on vous tapera sur les doigts si vous choisissez de mettre vos fichiers dans C:\\wamp\\www\\jobeet\\, donc mettez les dans C:\\wamp\\home\\jobeet\ . Et ne configurez pas votre domaine test en local sur le port 8080, mais définissez un sous domaine de localhost.

Pour ce faire, editez C:\\Windows\\System32\\drivers\\etc\\hosts. Ajoutez :
> 127.0.0.1        jobeet.localhost

Ensuite allez dans C:\\wamp\\bin\\apache\\Apache2.2.11\\conf
Editez httpd.conf, enlevez le dièse devant "Include conf/extra/httpd-vhosts.conf".
Enfin editez extra\\httpd-vhosts.conf et collez y ce contenu :

> <VirtualHost *:80>
>     DocumentRoot "C:/wamp/www/"
> </VirtualHost>
>
> <VirtualHost *:80>
>   ServerName jobeet.localhost
>   DocumentRoot "c:\\wamp\\home\\jobeet\\web"
>   DirectoryIndex index.php
>   <Directory "c:\\wamp\\home\\jobeet\\web">
>     AllowOverride All
>     Allow from All
>   </Directory>
>
>   Alias /sf "c:\\wamp\\home\\jobeet\\lib\\vendor\\symfony\\data\\web\\sf"
>   <Directory "c:\\wamp\\home\\jobeet\\lib\\vendor\\symfony\\data\\web\\sf">
>     AllowOverride All
>     Allow from All
>   </Directory>
> </VirtualHost>

C'est très important de laisser le premier virtualhost, sinon vous perdrez l'accès à la belle page d'accueil de localhost.

Voilà. Normalement c'est tout. Pour un premier jour de Symfony il était assez chargé, j'ai bien passé 3 jours en conf, et je vous ai épargné mes mésaventures notamment avec APC que j'ai essayé sur Windows pour l'abandonner ensuite (trop de soucis).

Une question : avez-vous choisi d'utiliser Cygwin ? J'ai préféré utiliser [GnuWin32](http://gnuwin32.sourceforge.net/), votre avis m'intéresse !
