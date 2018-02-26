---
path: "/symfony-day-1-parlons-en-encore.html"
date: "2010-05-08T00:37Z"
title: "Symfony - Day 1 - Parlons-en ... encore !"
tags: ["Web"]
---

[![](https://2.bp.blogspot.com/_lEhuTvDBOnM/S5_U9TOn4lI/AAAAAAAAAJQ/nXrevsBOWAM/s200/9782918390169-3d.jpg)](http://2.bp.blogspot.com/_lEhuTvDBOnM/S5_U9TOn4lI/AAAAAAAAAJQ/nXrevsBOWAM/s1600-h/9782918390169-3d.jpg)

J'ai décidé de faire un 2e billet sur le jour 1 de [Symfony](http://www.symfony-project.org/), car dans [le premier](2010-03-16-symfony-day-1-parlons-en.md) je proposait l'installation de trucs qui s'avèrent inutiles. Voici donc en résumé ce qu'il faut savoir.

Le premier jour est consacré à la configuration du serveur, et le tuto est largement orienté serveur Linux. Je vais vous donner des astuces pour commencer le projet sur Windows.

**Installation d'Apache, Mysql et PHP grâce à WAMP**

Récupérez et installez [WampServer](http://www.wampserver.com/download.php) sur le site officiel. Je vous recommande de ne pas choisir Firefox comme navigateur et laisser explorer.exe, et bien paramétrer le serveur smtp pour la fonction mail().

**Activation de l'url_rewriting**

Cliquez sur l'icône Wamp dans la barre des tâches, Apache, Apache Modules, rewrite_module.

**Pratical Symfony - Day 1**

Je vous laisse découvrir [le tuto](http://www.symfony-project.org/jobeet/1_4/Doctrine/fr/01). Sachez deux choses :

- votre configuration locale ne vous permet pas d'avoir APC et POSIX, c'est pas grave. APC permet à votre code d'être plus rapidement traité (en gérant un cache des fichiers php précompilés) et POSIX d'afficher des couleurs dans l'invite de commande, rien de bien méchant. Quand au module XSL, il est utilisé par Propel, mais Propel étant délaissé au profit de Doctrine, vous pouvez l'oublier également. En gros : check_configuration vous indiquera des erreurs bénignes que vous pourrez ignorer.

- on vous tapera sur les doigts si vous choisissez de mettre vos fichiers dans C:\\wamp\\www\\jobeet\\, donc mettez les dans C:\\wamp\\home\\jobeet\ . Et ne configurez pas votre domaine test en local sur le port 8080, mais définissez un sous domaine de localhost.

Pour ce faire, editez C:\\Windows\\System32\\drivers\\etc\\hosts. Ajoutez :

```
127.0.0.1        jobeet.localhost
```

Ensuite allez dans C:\\wamp\\bin\\apache\\Apache2.2.11\\conf
Editez httpd.conf, enlevez le dièse devant "Include conf/extra/httpd-vhosts.conf".
Enfin editez extra\\httpd-vhosts.conf et collez y ce contenu :

```
<VirtualHost *:80>
    DocumentRoot "C:/wamp/www/"
</VirtualHost>

<VirtualHost *:80>
  ServerName jobeet.localhost
  DocumentRoot "c:\\wamp\\home\\jobeet\\web"
  DirectoryIndex index.php
  <Directory "c:\\wamp\\home\\jobeet\\web">
    AllowOverride All
    Allow from All
  </Directory>

  Alias /sf "c:\\wamp\\home\\jobeet\\lib\\vendor\\symfony\\data\\web\\sf"
  <Directory "c:\\wamp\\home\\jobeet\\lib\\vendor\\symfony\\data\\web\\sf">
    AllowOverride All
    Allow from All
  </Directory>
</VirtualHost>
```

C'est très important de laisser le premier virtualhost, sinon vous perdrez l'accès à la belle page d'accueil de localhost.

Voilà. Normalement c'est tout !
