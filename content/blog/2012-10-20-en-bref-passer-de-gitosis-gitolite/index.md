---
path: "/en-bref-passer-de-gitosis-gitolite.html"
date: "2012-10-20T19:57Z"
title: "En Bref : passer de gitosis à gitolite"
tags: ["Linux", "Web"]
---

[![273px-Git-logo.svg](http://lh3.ggpht.com/-CPwwhzq6fz0/UILv9SiDzfI/AAAAAAAAARM/wkWIJWT7gwk/273px-Git-logo.svg_thumb%25255B3%25255D.png?imgmax=800 "273px-Git-logo.svg")](http://lh6.ggpht.com/-5bw8v6gOxqg/UILv8YeGPuI/AAAAAAAAARI/H19G98dSoDY/s1600-h/273px-Git-logo.svg%25255B5%25255D.png)

Je fais le ménage dans mes favoris de Firefox, et je vois que je n'ai jamais publié d'article pour passer du système de dépot Gitosis à Gitolite.

Comme ça fait un bail que je l'ai fait, je n'ai plus le détail de la procédure en tête. Ce dont je me rappelle c'est qu'à la mise à jour du Ubuntu Server Gitosis a été supprimé des dépôt et le paquet s'est désinstallé tout seul. [Gitolite](http://doc.ubuntu-fr.org/gitolite) est son remplaçant.

Pour l'installation, j'ai procédé comme suit (cf bloc-note que j'avais conservé)

```bash
sudo adduser git
scp ~/.ssh/id_rsa.pub git@localhost:~/admin.pub

su - git
git clone git://github.com/sitaramc/gitolite
mkdir bin
gitolite/install -ln
bin/gitolite setup -pk admin.pub
logout
sudo passwd git -l

git clone git@localhost:gitolite-admin.git
```

Ensuite pour convertir le fichier de configuration :

```bash
gitolite/convert-gitosis-conf gitosis/gitosis.conf > gitolite.conf
```

Il reste enfin à vérifier le fichiers de configuration (je me souviens avoir corrigé les groupes utilisateurs) et déplacer le stockage des fichiers du dépôt sur le serveur.
