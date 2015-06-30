# Gemini Javascript

These docs have been specifically targeted for the use of [Gemini Boilerplate](https://github.com/carpages/gemini-boilerplate). Before continuing, ensure that you've setup your environment to start using Gemini.

## Including Gemini Javascript in your Page

Gemini is included using a ``<script>`` tag at the end of your HTML. You'll need different calls depending if you're developing or in production. When using the development include, you'll be loading unminified and unconcatenated javascript which is helpful for debuging errors. When using the production include, you'll be loading minified and concatenated javascript to ensure the best performance. Both includes will functionally do that same thing on the page.

#### Development
```
<html>
  <!-- Notice the page specified in data-page -->
  <script data-page="index" data-main="src/js/build/development" src="src/bower_components/requirejs/require.js"></script>
</html>
```

#### Production
```
<html>
  <script src="dist/js/build/production.js"></script>
  <script>
    // This is relative to your distribution location
    require(['js/pages/index']);
  </script>
</html>
```

## File Structure
There are 2 important places to look within the boilerplate in regards to file editing: ``gemini.json`` and ``src/js/``

### gemini.json
This is the settings file for Gemini where you can specify all of your custom configurations. You can read more about the different settings under [Settings](#settings).

### ``src/js/``

#### pages/

This is where you'll find the javascript that runs on the different pages of your website. The only required file here is ``main.js`` which will run on every page. You can add more files here as you please, just ensure that you add the page location in ``gemini.json`` for the sake of your build.

Note: You'll need to specify the page's file name in your ``<script>`` include.

#### modules/

This is where you store your custom [AMD modules](http://requirejs.org/docs/whyamd.html#amd). To use these modules on your page, you need to add it as a path in ``gemini.json`` using the syntax ``"{module_name}": "{module_path}"``.

#### templates/

Gemini uses [Handlebars templating](http://handlebarsjs.com/). You can use this engine to build your own HTML templating, or replace the templates that various plugins are using.

#### build/

These are magical files that help configure requirejs to work with your source files. You shouldn't edit these unless you know what you're doing :).

## Using Modules

Out of the box you have access to a number of useful javascript modules with gemini. You can include these modules using the require function in your page specific .js files. ``require()`` accepts a list of modules, and a callback function when those modules have loaded.

```
require(['gemini', 'gemini.accordian'], function($){
  // Do your thing home slice
});
```

### Gemini: jQuery + Some

``G === $``

When you load gemini, you're loading the goodness of jQuery. That's because Gemini acts as a wrapper to jQuery, so you have access to all of jQuery's features.

Here are some other features:
- [Underscore.js](http://underscorejs.org/) - Gemini gives you access to underscore using ``G._`` or ``$._``
- Extendability - Gemini uses [jQuery.boiler](https://github.com/mattdrose/jquery-boiler) to build all of the extended modules

## [Note: To-Doc]
- Managing Modules
- Building Templates
- Doing Builds
- ``gemini.json`` settings
