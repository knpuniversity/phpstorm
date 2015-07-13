# Annotations

We've got a big project today, a site about movies. But only movies that 
have Samuel L. Jackson.

We'll start by creating a `MovieController`. We could right click on the
`Controller` directory, go to new, and select file from the menu. But we can
be faster! For mac users use `⌘+n` to get the "new" menu open. And because
we have the Symfony Plugin, by typing 'controller' you'll find an option to create 
one directly. Let's keep things simple and obvious and call it `MovieController`.

[[[ code('b022377819') ]]]

Ah, and when you use Git, PHPStorm asks you whether you want to add new files to
git. I prefer to just do this myself so I'll click 'no'. Beautiful!

## Auto-complete Annotations

We'll need a route to this `MovieController`, so add some annotations above `indexAction()`.
Let's change these to `@Route` and let autocomplete do its thing. The one we want is
`Sensio\Bundle\FrameworkExtraBundle\Configuration\Route`, select that option and hit
tab and notice that it added a `use` statement on line 5:

[[[ code('0962cf83fc') ]]]

That's really important because when you use annotations you need to have a `use` statement
for them. Now instead of spending your time looking it up in the documentation, autocomplete
will take care of it for you. Robots FTW!

Let's have our path be `/movies/new` and change `indexAction()` to `newAction()` because
this controller will render a "new movie" form. And we'll fix up our render call in
a second:

[[[ code('a01f86820c') ]]]

Head over to the browser and check if our new route is hitting our endpoint. Perfect!
It can't find the template but that's fine because, there isn't one :)

## Annotation Options

Annotations have a lot of options and one of them here is called `name`, which auto-completes
for us. Hey thanks. Fill that in with `movies_new`:

[[[ code('491b89965a') ]]]

If you're the curious sort and are wondering what other options you have, just hold
the control key and hit the space bar: that will bring up all the options that you
have in that spot. In fact, "control+space" can be used pretty much anywhere to show
you your auto-complete option - really handy.

This autocomplete works for two reasons. First, an annotation represents a real class.
Hold command, or control if you're in windows, and click `@Route` to open up the
class that fuels it.

[[[ code('7c09b953dc') ]]]

If you hold command again and go into its base class, you'll see that all of those
options are represented as properties inside of that class:

[[[ code('123a5429af') ]]]

To take this further if you go back to `MovieController` you can hold command and
click on the `name` option and have it take you right to that property. You may not
need this very often, but sometimes it's useful to see how an annotation option is
used to figure out what value you want to set for it.

Now thanks to the annotations plugin, annotations act a lot more like normal code,
with fancy auto-completion and other goodies.
