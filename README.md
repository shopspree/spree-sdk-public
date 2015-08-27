# Spree Widget

## User guide

The Spree widget contains video content and product page links that can be embedded onto your site. It is adaptive to site space requirements, responsive, and controlled through plain CSS definition. You can control the type of content the widget displays by setting a tag parameter on the widget.


### Geting started

To embed the widget on your website:

- Include a script tag with reference to the spree-sdk.js script in the web page `head` element. The script is hosted in the URL - `http://widgets.shopspree.co/wow/latest/spree-sdk.js` (https is also good).
 The tag should look like this:

````javascript
    <script src="http://widgets.shopspree.co/wow/latest/spree-sdk.js"></script>
````

- Create a `div` element in the web page body and provide it the class name `spree-root`, like this:

````javascript
    <div class="spree-root"></div>
````

This `div` element will contain the widget once the page loads.

- To determine the widget dimensions, and how they change in response to screen dimensions changes include the `spree-wow.css` and `spree-wow-ie8.css` files as stylesheets in the  web page. The files are provided with this SDK, to get them:

1. Download this SDK from  [here](https://github.com/shopspree/spree-wow-public/archive/master.zip).
2. Extract the downloaded archive file to a folder. 
3. The `spree-wow.css` and `spree-wow-ie8.css` will be in the `Sample-wow` subfolder of the SDK folder.
4. Copy them to your website, where you hold stylesheet files

Now they are ready for reference from within the web page. To support IE8 you will have to include a condition to choose between them. The end result should look like this:

````javascript
    <!--[if lte IE 8]>
    <link rel="stylesheet" type="text/css" href="spree-wow-ie8.css" media="all">
    <![endif]-->
    <!--[if gt IE 8]><!-->
    <link rel="stylesheet" type="text/css" href="spree-wow.css" media="all">
    <!--<![endif]-->
````

*(note that the css references exact location is dependent on where you placed them in relation to the web page)*

**The widget is now ready for operation!**   

You can review the examples to see how the end result should look like:   
In [Sample-wow](https://github.com/shopspree/spree-wow-public/tree/master/Sample-wow) you can find an example of how to introduce the tags into the WOW index web page. Review `index.html` to see how it adds the `div` element, spree SDK javascript reference and the stylesheets.
In [Sample-generic](https://github.com/shopspree/spree-wow-public/tree/master/Sample-generic) you can find a generic example of how to include the widget, with a minimal web page. You will note that this webpage embeds the relevant stylesheets instead of referring to them.

The next passages explain more about the behavior and options of the widget.

### Controlling the widget dimensions

The best method to control the widget dimensions is through CSS. simply set the `div` element dimensions.
You can use media queries for responsiveness support.

**Note:** By default the widget takes up 100% of the width up to 900 pixels (maximum width).
The banner view of the widget takes 91 pixels of height, and The expanded view takes 463 pixels of height.
You can control these dimensions by overriding them in your CSS stylesheet.
To properly view the widget its the width should be no less than 281 pixels.


#### Note on controlling dimensions in IE8
If used in IE8 note that IE8 does not support media queries. You should provide an alternative style definition for it.
To implement this use IE conditions. For example consider the following HTML declaration:

````javascript
    <!--[if lte IE 8]>
    <link rel="stylesheet" type="text/css" href="spree-wow-ie8.css" media="all">
    <![endif]-->
    <!--[if gt IE 8]><!-->
    <link rel="stylesheet" type="text/css" href="spree-wow.css" media="all">
    <!--<![endif]-->
````

The definition will use `spree-wow-ie8.css` in case of IE8 and `spree-wow.css` in case of anything else. The css for IE8 will probably be according to the largest media in `spree-wow.css`.

### Widget Attributes

The widget provides control over it through attributes that can be placed on the `spree-root` `div` element:

1. `data-spree-tag` - control the content that the widget shows. Available values are:
    1. `autos`
    2. `books`
    3. `events`
    4. `fashion`
    5. `food`
    6. `lifestyle`
    7. `sports`
    8. `tech-gadgets`

    The default is `fashion`
2. `data-spree-skip-watched-posts` - when `true` will choose as the first video one that the recipient didn't see yet, based on cookies registration of watched videos
3. `data-spree-open` - when `true` will start with the player open
4. `data-spree-autoplay` - when `true` and `data-spree-open` also `true` will begin playing the first movie immediately on load
5. `data-spree-loop` -  when `true` then when done playing the last video will go back to playing the first one, instead of stopping
6. `data-spree-mute` - when `true` player will be initially muted
