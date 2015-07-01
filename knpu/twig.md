#Twig

The Symfony Plugin has all kinds of awesome setup for Twig integration.
So let's render a template here, `movies/new.html.twig`. PHPStorm highlights
this immediately because it's missing its template, how thoughtful!

Let's make that template, in app/resources/views we'll create a directory
called movie and a file called new.html.twig. Like always start by extending
the base template, but notice we get autocomplete on that extends tag which is
*fantastic*! And we even get autocomplete on the template name. Down here we
get autocomplete on block and endblock as well -- it's like Christmas morning!

For our h1 tag we'll say 'New Samuel L Jackson Movie' and because the plugin
gives us intelligence on these file names it means that you can hover over
any template name and click it to go into that template. You can even do the
same thing on block, hovering over block body clicking it takes us to the block
body because it knows where that's coming from.

I'll close these two templates and go back to our controller. When we refresh we've
got our functional page. Notice to the left of `newAction` here we have a little icon
that appeared. When you click it it shows you related files to this controller. 
