---
path: "/developement-sur-android-debuts-avec.html"
date: "2010-11-07T02:16Z"
title: "Dévelopement sur Android - débuts avec Java et PhoneGap"
tags: ["Android", "Web"]
---

[![img_199912_android-lab](http://lh4.ggpht.com/_lEhuTvDBOnM/TNX9_we3cUI/AAAAAAAAANs/eeLW0onHKx8/img_199912_android-lab_thumb.jpg?imgmax=800 "img_199912_android-lab")](http://lh6.ggpht.com/_lEhuTvDBOnM/TNX9_pJuUkI/AAAAAAAAANo/Xt8RjCH4YrE/s1600-h/img_199912_android-lab2.jpg)

Une des raisons qui m’ont fait acheter un téléphone Android est la liberté d’utilisation qui va avec. En tant que développeur il y a énormément de façon de s’éclater, le développement sur Mobile en faisant partie.

Autant développer directement en Java (langage de prédilection sur Android) a été très simple grace à Motodev et les tutos intégrés, mais l’utilisation de PhoneGap (pour développer en HTML/CSS/Javascript) a été plus compliqué, surtout sur Windows.

#### Pour commencer : Java et Motodev

Comme je viens de le dire, le langage de prédilection sur Android est Java. C’est un Java un peu particulier, un ensemble de classes propres à Android a été ajouté et le code est précompilé grace à la machine Dalvik. Je ne suis pas rentré dans les détails, tout ce que je sais c’est que ça améliore les performances et l’utilisation mémoire.

Le site officiel fournit un Toolkit [à intégrer dans l’IDE Eclipse](http://developer.android.com/guide/developing/eclipse-adt.html), mais c’est à vous de l’installer et de le configurer. Partant de ce constat, Motorola a créé une solution toute prête : [Motodev](http://developer.motorola.com/docstools/motodevstudio/). Cette solution est tout simplement Eclipse avec tous les outils déjà intégré. En dehors de quelques liens vers les technos Motorola, cet IDE n’est pas limité aux seuls téléphone de la marque. De plus, on peut même l’installer en plugin Eclipse plutôt qu’en bundle, encore une bonne raison de l’utiliser !

Pour l’installation c’est très simple : installer le [Java Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/index.html) (JDK), se créer un compte sur Motodev (nécessaire pour télécharger les kits Android), installer [Motodev](http://developer.motorola.com/docstools/motodevstudio/). Au premier lancement, il demandera le répertoire de travail, sauf si vous l’avez installé en plugin. Je choisi alors un dossier séparé d’Eclipse. Après il vous demandera votre compte Motodev et la version du kit Android que vous souhaitez installer. Choisissez celle de votre téléphone, ou une version inférieure. Une fois installé, vous arriverez sur votre espace de travail, et vous pourrez consulter le tuto HelloAndroid ! Il faudra également configurer un périphérique virtuel pour tester vos applications sur l’émulateur, ou installer le pilote USB pour tester directement sur votre téléphone.

Voici un aperçu de l’interface de Motodev lorsque je teste mon HelloAndroid :[![motodev_screen](http://lh5.ggpht.com/_lEhuTvDBOnM/TNX-BOlnsZI/AAAAAAAAAN0/tRCWj_m0Cec/motodev_screen_thumb%5B12%5D.jpg?imgmax=800 "motodev_screen")](http://lh3.ggpht.com/_lEhuTvDBOnM/TNX-ApbDdkI/AAAAAAAAANw/E_LENZ1UFng/s1600-h/motodev_screen%5B16%5D.jpg)

#### Installer PhoneGap

Je suis développeur Web. L’idéal pour moi est donc de retomber sur mes pieds et coder mes applications avec des langages que je connais bien. C’est pour ça que je me suis tourné vers [PhoneGap](http://www.phonegap.com/start), un soft qui fait l’interface entre le système et vos pages Web (qui constituent l’appli). En dehors du coté pratique de ne pas faire de Java quand on n’est pas expert, PhoneGap est compatible avec de nombreux téléphones (iPhone, Android, Windows Mobile, Blackberry, …) et gère lui meme la compatibilité avec les anciennes versions d’Android. A travers des objet Javascript, vous aurez accès aux éléments du téléphones tels que le GPS, l’accéléromètre, la barre de notification …

##### Installer Apache Ant

Pour utiliser PhoneGap, il va falloir compiler le fichier .jar, et pour cela il va falloir utiliser Apache Ant. Sur Linux, c’est presque trop facile : “sudo apt-get install ant”. Sur Windows, il faut passer par [WinAnt](http://code.google.com/p/winant/).

##### Configurer les variables d’environnement

Sur Windows encore une fois (je sais pas comment c’est géré sur Linux) il faut également changer des variables d’environnement.
Tout d’abord, créer la variable ANDROID\_HOME avec comme valeur “C:\\Program Files\\Motorola Mobility\\MOTODEV Studio for Android 2.0\\android\_sdk” (sauf si vous l’avez installé ailleurs bien sûr). Ensuite, ajoutez à la fin de PATH “C:\\Program Files\\Motorola Mobility\\MOTODEV Studio for Android 2.0\\android_sdk\\tools” pour avoir les outils Android à portée de ligne de commande.

##### Compiler PhoneGap

[Téléchargez PhoneGap](http://www.phonegap.com/download), dézippez le dans le dossier de MOTODEV, puis ouvrez la ligne de commande dans “C:\\Program Files\\Motorola Mobility\\MOTODEV Studio for Android 2.0\\phonegap\\phonegap-android\\framework” (nécessite d'etre admin, car on est dans "Program Files"). Exécutez :

```bash
android update project -p .
ant jar
```

Normalement vous aurez un beau “BUILD SUCCESS”

##### Tutoriel HelloPhoneGap

A partir de maintenant, vous pouvez [suivre le tuto](http://wiki.phonegap.com/w/page/30862722/phonegap-android-eclipse-quickstart#CreatingANewProject) sur le site de PhoneGap. Juste 2 petites coquilles :

* J’ai du renommer js/phonegap.js.base en js/phonegap.js car la compilation ne l’avait pas fait,
* J’ai changé l'inclusion dans index.html (il manque le dossier js), d’ailleurs je conseille de les mettre dans /js/phonegap/ plutôt, car ces fichiers Javascript sont particuliers, ce sont ceux qui permettent d’accéder au périphérique.

#### Conclusion

Nous avons vu comment configurer un IDE basique, et y intégrer la technologie PhoneGap. Néanmoins pour aller plus loin, on pourrait peut-être mixer des éléments d’interface en Java et du contenu en HTML (pour faire une barre de navigation par exemple), ou utiliser un framework JS pour l’interface, tel que [jQuery Mobile](http://jquerymobile.com/) (en cours de dévelopement).

Mon expérience là dessus m’a montré que les performances ne sont pas là. Peut-être à cause de la jeunesse du projet jQuery Mobile, mais je pense que le simple fait de tout faire passer par du Javascript est loin d’être optimisé. Une bonne raison pour préférer Adobe Air à PhoneGap, ou pour réapprendre le Java ?
