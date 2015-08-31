# Refactoring

Ok back to work, let's finish up this `MovieController`. `Command+O`, `MovieController`,
and now we've got that file open.

We need to save the POST'ed movie to the database. Start with getting our entity manager
with `$em = $this->getDoctrine()->getManager();`. Then `$em->persist($movie);`, and
`$em->flush();`:

[[[ code('adbf826319') ]]]

Nice and simple!

While we're here, I'll copy the `getDoctrine()` line and paste it into `listAction()`
so we can make that work. Here we'll query for the movies with `$em ->getRepository()`
and the first cool thing here is that... you guessed it! We get autocomplete on
this. Type the entity name, select the right one and hit tab:

[[[ code('79aa3046e5') ]]]

The second cool thing is that it autocompletes the methods on the
repository, and this includes any custom methods you have inside of
there. We'll use the normal `findAll();`. Down below, we'll `return $this->render('movies/list.html.twig');`
which doesn't exist yet, with an array and we'll pass it movies:

[[[ code('bc404bb2c3') ]]]

Awesome!

Let's go create that file: `list.html.twig`. And to save some time,
I'll just paste in some code for this template: it's really straight
forward:

[[[ code('2acb4245de') ]]]

The only interesting thing here is that you do get autocomplete on the different
properties for `movie`, Which really is pretty amazing. The reason that works is
because PHPStorm knows that the `MovieRepository` returns `Movie` objects, so that
cascades all the way down into Twig.

So as long as you have good PHPDoc that says what types of objects functions return,
that should connect down to how things auto-complete in Twig.

Let's try this whole thing out. But before we do that we need to setup our database.
Head over to `parameters.yml` by using our shortcut `command+shift+O` to open it up.
Everything seems to be in order here, so let's just change our database to be `phpstorm`.

And just when you thought I couldn't get any lazier with my shortcuts
I'm going to use the built in terminal from PHPStorm. This drops me right into the
correct directory so I can run:

```bash
./app/console doctrine:database:create
./app/console doctrine:schema:create
```

Hide this little terminal, head back and refresh our browser. And we see... oops
we have a small rendering problem, which is probably in our form template.

Back to PHPstorm, `command+shift+O` and search `_form.html.twig`. And yep there it is, change
`form-control` to `form-group` - that's the *correct* Bootstrap class. Refresh again. That
looks way better.

Now we can fill out the form. Let's see, which one of our favorite Samuel L Jackson movies
should we choose first - so many choices. Let's just go with the obvious best: "Snakes on a Plane",
with our character, Neville Flynn. Neville *is* the main character, and clearly this film was
a 10 out of 10. I mean come on, this is Sam at his best! And I think everyone remembers
the fateful day this film was released: August 18, 2006. Let's save this small piece of history. 

## Refactoring to a Method

Beautiful! Now for a little refactoring. First, we have `$em = $this->getDoctrine()->getManager();`
in a couple of places. So I'm going to refactor that: select that line and we'll see
another important shortcut, `control+t`. This is the refactor shortcut. If you ever
forget it, just go to the Refactor menu at the top and select "Refactor This" from
the list. 

We've got our line selected, press `control+t`. There's a lot of options in here,
but we want the one called method. In the "Extract Method" form, add `getEm` as the name,
make sure that the private radio button is selected and refactor!

[[[ code('d0f65c345c') ]]]

Boom! It puts this on the bottom and it changes the original code to `$this->getEm();`.
Copy this line, pressing `control+c` will select the whole line and we'll paste it
right up here:

[[[ code('df66b2a3dc') ]]]

## Refactoring to a BaseController

This shortcut is going to be useful in more than just this controller, so this is
the perfect time to create a `BaseController` for my whole project. Click the `Controller`
directory at the top of your IDE, and from there press `command+n`, select `Controller`
from the menu and name it `BaseController`. To start, remove that public function
and add `abstract` before the class:

[[[ code('0a0de1ac81') ]]]

This is now the spot for our own shortcuts. In `MovieController` update it to extend
`BaseController`. This `use` statement is showing up in a darker gray to indicate
that it isn't being used any more and the same for the `Response` `use` statement.
Delete both of those:

[[[ code('71e97bcc49') ]]]

With the `BaseController` in action, let's refactor `getEm()` into the `BaseController`.
Select the method, one cool way to do that is hit `option+up` which will select larger
and larger contexts. Now hit `control+t`. Select "Pull Members Up" from the menu,
which will pull them up to the parent class. It already recognizes that `BaseController`
is the destination, and at the bottom it's warning us that the access will be changed
from private to protected, which is awesome! Hit refactor and we can see it's gone
from this file, because now it lives inside of `BaseController`:

[[[ code('6e6943bc0b') ]]]

That there is a really fast way to refactor things!

## Refactoring to Rename a Method

Now that I have this here I'm realizing that `getEm()` is not that great of a name choice.
So back to `command+t`, select rename from the menu and change it to `getEntityManager`
to make my code a little clearer. When we do that I get a summary down here of all the
spots in our project where PHPStorm sees `getEm()`. Click the "Do Refactor" button to
rename this and all the other spots in the code that need updating:

[[[ code('569a43adb9') ]]]

[[[ code('86f417b783') ]]]

Sah-weet!

There are a lot of other things you can do with the refactor feature in PHPStorm.
For example, we can extract this out to a variable. This could add a level of clarity
to what things are.

Or, say you get into a spot where you messed up your formatting in some terrible way.
Oof that looks just awful. Make it stop! At any point, you can go up to the code menu 
at the top and select reformat code, which is also `command+option+L` and it will tidy
that back up for you.

So let's hit `command+A` to select all the code I want to reformat, then `command+option+L`
and now everything is back into place based on our coding standards, which you can of course
control. 
