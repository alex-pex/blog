---
path: "/remplacer-sed-i.html"
date: "2010-04-29T17:33Z"
title: "Remplacer sed -i"
tags: ["Général", "Linux"]
---

Une petite astuce, si un jour vous avez besoin de rechercher / remplacer en masse, sur plusieurs fichiers, sur un serveur Linux vieillissant... Normalement, vous pourriez faire quelque chose comme ca :

```bash
find ./test -type f -name '*.TXT' -not -path '*/.svn*' -exec sed -i "s/Bonjour/Hello/g" {} \;
```

Sauf que "sed -i" n'est pas disponible partout.

Voici une commande équivalente :

```bash
bleh=`find ./test -type f -name '*.TXT' -not -path '*/.svn*'`; for f in $bleh; do sed -e "s/Bonjour/Hello/g" $f > $f.tmp; mv -f $f.tmp $f; done
```

C'est tout simplement la version compacte de ce code

```bash
bleh=`find ./test -type f -name '*.TXT' -not -path '*/.svn*'`;
for f in $bleh; do
sed -e "s/Bonjour/Hello/g" $f > $f.tmp;
mv -f $f.tmp $f;
done
```
