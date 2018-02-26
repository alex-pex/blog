---
path: "/jquery-structure-de-plugin-classe.html"
date: "2011-04-23T19:44Z"
title: "jQuery - Structure de plugin - Classe interne"
tags: ["Web"]
---

[![jquery-logo](http://lh6.ggpht.com/_lEhuTvDBOnM/TbMP-r6UPZI/AAAAAAAAAO0/cfigCuPku8o/jquery-logo_thumb.png?imgmax=800 "jquery-logo")](http://lh5.ggpht.com/_lEhuTvDBOnM/TbMP-OY5GMI/AAAAAAAAAOw/3bXCulnwghg/s1600-h/jquery-logo%5B2%5D.png)

De retour sur ce blog, j’aimerais partager une structure de plugin jQuery que j’ai mis au point. Je me suis inspiré [du site officiel](http://docs.jquery.com/Plugins/Authoring), et [d’un autre site](http://fuelyourcoding.com/jquery-plugin-design-patterns-part-i/) qui définit des design patterns de plugins.

L’idée est d’avoir une classe pour définir les méthodes (publiques ou privées) et pour sauvegarder l’état de l’instance. Dans mon exemple, la méthode “next” se souvient de la variable “i”. Egalement, l’appel des méthodes se fait à la mode jQueryUI (tel que conseillé par le site officiel).

Sans plus tarder, voici la structure que j’ai retenu :

```js
/**
 * Slider jQuery plugin
 */
(function($){
  $.fn.slider = function(method) {
    /**
     * Internal Class
     */
    var SliderClass = function($obj, options){
      var data = {};
      var i = 0;
      /* PUBLIC */
      this.type = 'SliderClass';
      this.dump = function() {
        console.group('SliderClass Dump');
        console.log($obj);
        console.log(options);
        console.log(data);
        console.groupEnd();
      }
      this.print = function(txt) {
        console.group('SliderClass Print');
        console.log(options.print_prefix+txt);
        console.groupEnd();
      }
      this.next = function() {
        console.group('SliderClass Next');
        doNext();
        console.log(i);
        console.groupEnd();
      }
      /* PRIVATE */
      function doNext() {
        i++;
      }
    }
    /**
     * Call mechanism
     */
    var args = arguments;
    // init
    if (typeof method === 'object' || !method) {
      var options = $.extend({}, $.fn.slider.defaults, args[0]);
      return this.each(function() {
        var $this = $(this);
        if (!$this.data('slider')) {
          $this.data('slider', new SliderClass($this, options));
        }
      });
    }
    // methods
    else {
      return this.each(function() {
        var data = $(this).data('slider');
        if (data[method]) {
          data[method].apply( data, Array.prototype.slice.call( args, 1 ));
        }
        else {
          $.error( 'Method ' +  method + ' does not exist on jQuery.slider' );
        }
      });
    }
  };
  /**
   * default configuration properties
   */
  $.fn.slider.defaults = {
    print_prefix: 'Hello, I say : '
  };
})( jQuery );
```

Ce que j’apprécie dans cette structure, c’est qu’il est très simple d’ajouter des fonctionnalités, tout se passe sur la classe, et toutes les données sont préservées entre chaque appel.

Un exemple zippé prêt à l’emploi sur [CE LIEN](http://alexandre.paixao.free.fr/blog_files/jquery_design_pattern/jquery-design-pattern.zip). Comme c’est du debug, ouvrez votre console Firebug pour voir le fonctionnement. N’hésitez pas à me faire des retours, j’ai essayé de mélanger ce qui me plaisait sur le net tout en simplifiant le code mais c’est sûrement perfectible.
