# Twig

The Symfony Plugin has all kinds of awesome setup for Twig integration.
So let's render a template here, `movie/new.html.twig`:

[[[ code('8526e13420') ]]]

PHPStorm highlights this immediately because it's missing its template, how thoughtful!

Let's make that template, in `app/Resources/views` we'll create a directory
called `movie` and a file called `new.html.twig`. Like always, start by extending
the base template, but notice we get autocomplete on that `extends` tag which is
*fantastic*! And we even get autocomplete on the template name. Down here, we
get more autocomplete on `block` and `endblock` -- it's like Christmas morning!

[[[ code('55484954f4') ]]]

For our `h1` tag we'll say 'New Samuel L Jackson Movie'. And because the plugin
gives us intelligence on the Twig file names, you can hover over any template
name, hold command, and click it to go there. You can even do the same thing on
a block: holding command and clicking `block body` takes us to the `block body` in
`base.html.twig` because it knows where that's coming from.

I'll close these two templates and go back to our controller. When we refresh we've
got our functional page. Now, to the left of `newAction`, we have a cute little icon
that appeared. When you click it, it shows you related files to this controller.
So we see here we've got the controller itself and the template, and this list will
get longer as we start referencing more things like repositories and services.

Like most templates, we're going to want to use some variables. Let's start with a
quote variable that we'll display in the form for inspiration. Eventually we'll have
this generated randomly but for now we'll just hardcode it in:

[[[ code('4f37aa2d0f') ]]]

"If my answers frighten you then you should cease asking scary questions". Oh Sam
you're too much!

I could just go to my tree and double click `new.html.twig` to open it again, but instead 
I'm going to hold command and click the name in the controller to get us there. In the
template we'll use the normal ``{{ }}`` inside a p tag, but watch this: we get autocomplete
on our quote variable. That is huge!

[[[ code('c319851e91') ]]]

In my experience, it doesn't work 100% of the time, but it does work most of the time.
It will even look inside your controller to see what kind of object it is and give you
autocomplete on its methods.

And remember, anywhere that you get autocomplete, you can hit command+space to see
all of your  options. Here it shows us the variable and all of the function names
and filters that come  from everywhere inside of Symfony and Twig. For example, if
you start using the `upper` filter, you'll get that autocompleted. Same goes for
the `date` filter, and as you're typing `date` you'll see the arguments you'll need.
The first is the value to the left and the second here - `format` - is what we'll
use on the filter itself: it's a nice reminder we need to pass something like `Y-m-d`.
To make this a bit clearer I'll add 'Today is:' before the date is actually rendered
and we'll put our quote in an h3 tag.

[[[ code('5e2c9fa36e') ]]]

If you really can't remember how the `date` filter works, you can hold command now
and click  into it. That's going to take you to whatever class provides that filter.
In this case there's two. If you ever see something like this: where one is in the
`cache` directory, just ignore that and click the other option.

The Twig environment is passed first and after that you have the date, the format
and the timezone and you can just see how things work. This is wonderful for debugging. 

Eventually we're going to have a form so I'll go ahead and create a new template called
`_form.html.twig` and put my fake form tag stuff right there. Heck, go crazy and throw a
button in too:

[[[ code('38eed99193') ]]]

You're seeing another trick with PHPStorm, the mini-code generation comes from a
feature called live templates. I just type `form`, hit tab, and it builds the tag
for me. The same works with `button` then tab, `textarea` then tab and a lot of other
things. We'll create our own live templates in a bit.

Back in `new.html.twig`, you know how this works. We use the `include` function and
not only do you get autocomplete on that function name, but you also get it on the
template name. Don't worry about the "movie" part of the name, just start typing
`_form.html.twig` and you're all set. And there are two formats here: both valid,
but I like the first one, it's cleaner.

[[[ code('a28036e2c8') ]]]

Go back and refresh, beautiful! Everything looks awesome, except I guess my button
is ugly. So I'll throw in some twitter bootstrap classes to make this a bit prettier. 

Ahh there we go! And that's some of what you can expect now with Twig!
