#jQuery PlugInMarkUp

##What does it do?

With jQuery PlugInMarkUp you can call several jQuery plugins to specific dom elements by using html data attributes.

### Example

Let's say we have jQuery-Plugin called <i>examplePlugIn</i>, that paints the background color of the assigned element to a
color that will be specified by a literal with the property _color_.

### _Without_ PlugInMarkUp

```html
    <div id="example1">
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna
        aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea
        takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy
        eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores
        et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    </div>
    <script type="text/javascript">
        $('#example1').examplePlugIn({
            color: 'blue';
        });
    </script>
```

### _With_ PlugInMarkUp

```html
    <div id="example1" data-enable-plugins="['examplePlugIn']" data-exampleplugin="[{color: 'pink'}]">
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna
        aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no
        sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam
        nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo
        duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
    </div>
    <script type="text/javascript">
        $('body').plugInMarkUp();
    </script>
```

### Why should I use this?

Let's say you have big website that is generated by a CMS. You can't say what kind of PlugIns will be enabled on the site or
you could insert content into dom via ajax not knowing what kind of plugins should be activated for the new dom element.
With this plugin you can just call the plugin to the new inserted dom element.
No further need of bootstrap helper classes and stuff.

### How do I use this?

Just add the data attribute <i>data-enable-plugins</i> to the dom node you usually would assign the jQuery-Plugin to. You can
assign as many plugins as you want. Just make sure that you wrap the list in brackets.
The corresponding configuration for the plugin will be placed in another data attribute. Each plugin gets its own and the name
of the attribute is determined by the lowercased plugin name. All arguments that you would usually add as arguments to the
function will be placed in that data-attribute, also surrounded by brackets.

Lets say you have two fancy plugins. One called _myPlugin1_ and _myOtherPlugIn2_. You would enable them by adding
the following data-attribute:

```data-enable-plugins="['myPlugin1', 'myOtherPlugIn2']"```

You add configuration by adding the following _two_ data attributes to the same tag.

```data-myplugin1="['argument1','argument']" data-myotherplugin2="[{myLiteralConfig1: 'foo'}, 'argument2']"```