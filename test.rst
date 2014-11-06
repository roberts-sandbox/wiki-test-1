====================
jQuery-PluginCreator
====================

A jQuery add-on that makes creating plugins a little easier.


Contents
========

1. Introduction
2. Requirements
3. Usage
4. jQuery.addPlugin API
5. jQuery.fn.yourPlugin API
6. Tests


Introduction
============

jQuery PluginCreator is a small JavaScript library that can be used in conjunction with jQuery to easily
create jQuery plugins.

Creating a plugin with PluginCreator is pretty easy, you simply provide a name, an optional default values and
optional plugin instance members. PluginCreator uses these to create a new jQuery plugin function that be
executed against jQuery selections.

Plugins created using PluginCreator can also be extended with new members or cloned as entirely new plugins. Plugin
extension allows you to override plugin members while retaining access to the overriden members. Individual plugin
instances can also be extended in a similar fashion.


Requirements
============

jQuery PluginCreator can be used in any of the following JavaScript environments:

* CommonJS (Node.JS, etc)
* Browser + AMD (RequireJS, curl.js, etc)
* Browser

CommonJS
--------
* jsdom >= 1.0.0
* jQuery >= 2.0.0


Browser
-------
* jQuery >= 1.6.0

In order to make use of jQuery PluginCreator you will need jQuery. For a browser environment, any recent version should
do the trick. For a CommonJS environment any jQuery 2.x release should work.


Usage
=====

--------
CommonJS
--------
  ::

    var fs = require("fs"),
        jsdom = require("jsdom"),
        html = fs.readFileSync("/path/to/your/markup.html"),
        document = jsdom.jsdom(html),
        window = document.parentWindow,
        jQuery = require("jquery")(window),
        plugnCreator = require("jquery.plugincreator")(jQuery);

    jQuery.addPlugin(
      "myPlugin",
      {
        defaultSomething1: "a string",
        defaultSomething2: 10
      },
      {
        member1: function () {
          // Do something
        }
      }
    );

-------------
Browser + AMD
-------------
  ::

    <html>
        <head>
            <!-- Set up your AMD loader here --!>
            <script type="text/javascript">
                require(["jquery", "jquery.plugincreator"], function ($, pluginCreator) {
                    $.addPlugin(
                        "myPlugin",
                        {
                          defaultSomething1: "a string",
                          defaultSomething2: 10
                        },
                        {
                          member1: function () {
                            // Do something
                          }
                        });
                });
            </script>
        </head>
        <body>
        </body>
    </html>
