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
So we see here we've got the controller itself and the template, and this list will
get longer as we start referencing more things like repositories from inside of here.

Like most templates we're going to want to apply some variables. Let's start with a
quote variable that we'll display in the form for inspiration. Eventually we'll have
this generated randomly but for now we'll just hardcode it in. "If my answers frighten
you then you should cease asking scary questions". Oh Sam you're too much!

I could just go here and double click `new.html.twig` to open it again, but instead 
I'm going to hold command and click the name to get us there. In the template we'll 
use the normal {{}} inside a p tag, but watch this we get autocomplete on our quote
variable. That is huge!

In my experience it doesn't work 100% of the time, but it does work most of the time.
It will even look inside your controller to see what kind of object that is. 

Remember anywhere that you get autocomplete you can hit control space to see all of your 
options. Here it shows us the variable and all of the function names and filters that come 
from everywhere inside of Symfony and Twig. For example, if you upper filter this you will
get that autocomplete. Same goes for the date filter, as you're typing date you'll see the
arguments you'll need. The first is the value to the left which is a nice reminder that format
will be the first argument that we pass over here, like year-month-day. To make this a bit
clearer I'll add 'Today is:' before the date is actually rendered and we'll put our quote
in an h3 tag. 

If you really can't remember how the date function works you can hold command now and click 
into that and that's going to take you to whatever class provides that filter. In this case
there's two. If you ever see something like this where one is in the classes directory, just
ignore that one and click the other option. 

The Twig environment is passed first and after that you have the date, the format and the timezone
and you can just see how things work. This is wonderful for debugging. 

Eventually we're going to have a form so I'll go ahead and create a new template called
`_form.html.twig` and put my fake form tag stuff right there. Let's throw in a button too.
You're seeing another trick with PHPStorm, those are called live templates and we're going
to look at those later. It allows you to type form, button, text area tab and then have it
expand that. We'll go ahead and create our own live templates.

Back in new.html.twig, you know how this works. We use the include and not only do you get
autocomplete on that function name, but you also get it on the template name. Don't worry about
the movie part, just go straight to the _form.html.twig and you can there are two formats here.
Those are both valid in Symfony but I like the first one, it's a bit cleaner. So there we go!

Go back and refresh, beautiful! Everything looks awesome, except I guess my button is ugly. 
So I'll throw in some twitter bootstrap classes to make this a bit prettier. 

Ahh there we go! And that's some of what you can expect now with Twig!
