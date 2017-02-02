# learning-jquery
Repository for myself for JQuery learning

## Notes
# What is JQuery
Just a single Javascript file.
Cross-Browser (don't have to worry about platform)
'Selectors' feature (like CSS)
Events Feature
Ajax (Async Javascript and XML)
Json (JavaScript Object Notation)
Plugins

# Why use JQuery
Locating elements in a specific class
Apply styles or classes to multiple elements in the DOM
Handling events without having to worry about browsers

# To use JQuery
Support IE 6 - 8
	Use jQuery 1.x
Don't need to support IE 6 - 8
	Use jQuery 2.x
Download the appropriate script and include it like so:
<head>
	<script type="text/javascript" src="jquery.js"></script>
</head>

Compressed (minified) version of it can be used to save space / make smaller footprint.
Uncompressed is more readable and should be used for development for debugging.

# Using a Content Delivery Network (CDN)
Why use CDN?
	- Can get benefits of caching between sites instead of having to download the reference if it's a relative path
	Microsoft "http://ajax.microsoft.com/ajax/jquery/jquery-[version].js"
	Google "http://ajax.googleapis.com/ajax/libs/jquery/[version]/jquery.min.js"
	- They have data-centers around the world, so the user can be redirected to a server closer to them for quicker downloads
	- Can get the benefit of parallelism. (Browsers limit ACDP calls to a given domain.  If this is directed to a different domain, it will load in addition to the local objects loading.)
Why NOT use CDN?
	- If you can't connect to the CDN, you can't load. (But you can supply a fallback)
		<script>
			window.jQuery || document.write('<script src="jquery.js"><\/script>')
		</script>
		
# Detecting when a page is loaded.
<script type="text/javascript">
	$(document).ready(function () {
		//Perform action here - DOM hierarchy is loaded, but not all images are loaded
	});
</script>

Alternative to using the jQuery ready function is to put the script tag at the bottom of the body, because then you know everything else in the DOM is loaded at that point.  If you want it in the <Head> tag, use $(document).ready().

$('#idSelector') returns objects with the specified 'Id'.
The jQuery objects that are returned have helper functions/methods on them to manipulate the DOM, such as ().html('Hello World'), to manipulate the HTML to include that string.


# [API Documentation](http://api.jquery.com/)

# jQuery Selectors
## What are selectors?
Selectors are strings that identify an HTML element/tag that you wish to manipulate with jQuery code.

###Selecting nodes by Tag Names
$('a') selects all <a> elements
$('p') selects all <p> elements
$('p,a,span') selects all paragraph, anchor, and span tags
$('table tr') selects all tr elements that are (any) decendants of the table element.

###Selecting nodes by ID
HTML: 	<div id="testDiv">This is a test div</div>
jQuery:	$('#testDiv')

###Selecting by class name
HTML: <p class="MyClass">
jQuery: $('.MyClass')

HTML: <div class="blueDiv"></div> <div class="redDiv"></div>
jQuery: $('.blueDiv, .redDiv')

Can combine this with Tag Names (elements) as well
HTML: <div class="myClass"></div>
jQuery: $('div.myClass')
This allows us to not have to scan the whole DOM, only the elements we want/need.

Be wary of performance when using selectors.  Try to be as specific as you can be so you don't have to scan the whole DOM.

###Selecting by Attribute
Use brackets [attribute] to select based on attribute name and/or value.