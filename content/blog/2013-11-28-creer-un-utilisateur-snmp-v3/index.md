---
path: "/creer-un-utilisateur-snmp-v3.html"
date: "2013-11-28T00:31Z"
title: "Créer un utilisateur SNMP v3"
tags: ["Linux", "Web"]
---

[![](https://1.bp.blogspot.com/-3QhS7jiDr5E/UpZ-Jc_nPRI/AAAAAAAACiQ/6586nMAwOJU/s200/rj45.jpg)](http://1.bp.blogspot.com/-3QhS7jiDr5E/UpZ-Jc_nPRI/AAAAAAAACiQ/6586nMAwOJU/s1600/rj45.jpg)

La configuration d'un service SNMP est assez compliquée. J'ai mis pas mal de temps pour trouver une source intéressante (et surtout simple à suivre) alors je vous la file : [http://www.bortzmeyer.org/snmp-v3-inciga-cacti.html](http://www.bortzmeyer.org/snmp-v3-inciga-cacti.html). Le gars est un passionné de l'analyse des RFC (entre autres) !

Voici en résumé ce qu'il y a à retenir :

```bash
sudo apt-get install snmpd snmp
```

Seul snmpd est nécessaire pour le serveur, mais le client snmp permet de créer des utilisateurs facilement et de les tester.

Pour ajouter un utilisateur il faut couper le daemon avant :

```bash
sudo service snmpd stop

sudo net-snmp-config --create-snmpv3-user -a SHA -x AES
```

On choisit un login, un password, et une clé d'encryptage (qui peut être la même que le mot de passe). Dans l'exemple l'utilisateur "clinique" a été créé, avec le mot de passe "cahuzac" et la clé d'encryptage identique.

Pour ma part, j'ai modifié le type d'utilisateur de rwuser vers rouser. La commande précédente indique clairement quels fichiers ont été modifiés, il est donc facile de revenir dessus. Ensuite on relance le daemon :

```bash
sudo service snmpd start
```

Enfin, on vérifie que tout est bon

```bash
snmpwalk -v3 -u clinique -a SHA -A cahuzac -x AES -X cahuzac -l authPriv localhost
```

Si vous voyez une sortie qui fait 3km, c'est que ça fonctionne !
