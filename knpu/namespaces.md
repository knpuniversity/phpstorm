# Namespaces

Since we have this new movie form, we're going to want to save the data to the database. 
To do this let's create a `Movie` entity. I'm not going to generate it, let's just do this
by creating a good ole fashioned PHP Class called `Movie`. But when I do this, notice the
namespace box is empty. I could type `AppBundle\Entity` here, but I'm trying to do as
little work as possible people!

Let's make the robots do this for you. Go into preferences, search for 'directories' and
here you can see the three directories that we excluded earlier. Click on `src` and click
the blue sources button above. Now we can see this on the right and clicking the little
'p' allows us to edit the properties. So, if we were using PSR-4 inside of this directory
we could actually put our namespace prefix in this box - like `KnpU`. But all we needed to
do was mark it as a source route, so we're done!

When we head back, oh look the `Entity` directory disappeared! Where did we misplace that to?
Well, sometimes PHPStorm does that to empty directories. Temporarily I'll switch back to project
view and now create a new PHP Class. Because of the sources change, it guesses the namespace
part perfect. Call the class `Movie`:

[[[ code('dd70b7a518') ]]]

Okay switch back to Project Files and there it is. Excellent! In a second we'll set this up
with some annotations, but right now I want to use it inside of my `MovieController`. We'll
add a form here soon, and when we do, we'll need a new `Movie` object. So we'll say
`$movie = new`... and I could end this with `AppBundle\Entity\Movie` -- but you really
don't want to do that. Always go directly to the last part: in our case `Movie`, and let
that autocomplete:

[[[ code('9ebd0e81ec') ]]]

Because, when you do that, it adds the `use` statement on line 5 which is HUGE. If
you are not using the autocomplete functionality for `use` statements, then you're
doing it wrong.

Now, if something went wrong and you didn't autocomplete or you end up with `Movie`
here but no `use` statement, you can import it if you want. Just hit `alt + enter`.
`Alt enter` is one of the most important shortcut we are going to see. It's called
the "actions" shortcut. Often when you're inside some code. you can `alt + enter`
and get a list of actions to do. I'll select 'import class' from this list and it
will add that `use` statement for us.

To take this a bit further let's add a `public function listAction()` that will list
those movies from the database. I don't want to build this out now, I just want it
to return a simple `Response` that says "todo". So let's add `return new Response`
and select the Response we want, which is the one from HttpFoundation. Hit tab and
the `use` statement politely puts itself on top of our file. Finish with 'TODO'.
Now let's add a route above this, `@Route("/movies", name="movies_list")`:

[[[ code('c3f5ddcd6a') ]]]

Oh and now that we have this second endpoint, back in `new.html.twig`, if we want
to create a link to this page, we can. And we can use another live template. Type
`a`, hit tab, and use `{{ path() }}` and - amazingly - we even get auto-complete
on the route name. For the link text, say "back to list':

[[[ code('755364fc24') ]]]

Refresh that, and there's our link right back to our list. Awesome!

So, don't. write. `use` statements. ever.
