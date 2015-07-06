#Refactoring

Ok back to work, let's finish up this MovieController. Command O, movie controller and now we've got that
file open.

Let's save our form now. Start with getting our entity manager with `$em = $this->getDoctrine()->getManager();`.
`$em = persist($movie);`, and `$em = flush();`. Nice and simple!

While we're here, I'll copy the getDoctrine line and paste it into listAction so we can make that work. 
Here we'll query for the movies with `$em ->getRepository()` and the first cool thing here is that...you guessed 
it! We get autocomplete on that. Type the entity name, select the right one and hit tab.

The second cool thing is that it autocompletes the methods on the repository, and this includes any custom methods
you have inside of there. We'll use the normal `findAll();`. Down below, we'll `render $this->render('movies/list.html.twig');`
which doesn't exist yet, with an array and we'll pass it movies. Awesome!

Let's go create that file, list.html.twig and to save some time I'll just paste in the code for this template,
it's really straight forward. The only interesting thing here is that you do get autocomplete on these different
properties. Which really is pretty amazing. The reason that works is because PHPStorm knows that the movie repository
returns movies so that cascades down into Twig.

So as long as you have good PHPDoc that says what types of objects things are returning and that should cascade
down to how things look in Twig.

Let's try this whole thing out, before we do that we need to setup our database. Head over to `parameters.yml`
by using our shortcut `command+shift+O` to open it up. Everything seems to be in order here, so let's just
change our database to be `phpstorm`. 

Just when you thought I couldn't get any lazier with my shortcuts, I'm going to use the built in terminal
from PHPStorm. This drops me right into the correct directory so I can run `./app/console doctrine:database:create`
and `./app/console doctrine:schema:create`. Now let's hide this little terminal, head back and refresh our
browser. And we see... oops we have a small rendering problem here which is probably in our form file. 
Back to PHPstorm, `command+shift+O` and search `_form.html.twig`. And yep there it is, change `form-control` to
`form-group`. Refresh again and there we go! 

Finally I can fill out my form, let's add the movie Snakes on a Plane. With our character, Neville Flynn. 
Yes, to main character, and clearly this film was a 10 out of 10. I mean come on, this is Samuel L Jackson
at his best! And as everyone knows that was released on August 18, 2006. And let's save this small piece of
history. 

Beautiful! Now for a little refactoring. First, we have `$em = $this->getDoctrine()->getManager();`
in a couple of places. So I'm going to refactor that, select that line and we'll see another important
shortcut, `control+t`. This is the refactor shortcut, if you ever forget it, just go to the refactor menu
at the top and select Refactor This from the list. 

We've got our line selected, press `control+t` there's a lot of options in here, but we want the one called
method. In the Extract Method form, add 'getEm` as the name, make sure that the private radio button is
selected and refactor!

And boom! It puts this on the bottom and it changes `$this->getEm();` right there, that's pretty nice!
Copy this line, pressing `control+c` will select the whole line and we'll paste it right up here.
This shortcut is going to be useful in more than just this controller, so this is the perfect time to
create a baseController for my whole project. Click the `Controller` directory at the top of your IDE, 
and from there press `command+n`, select Controller from the menu and name is `BaseController`.

To start, remove that public function and add `abstract`. This is now the spot for our own shortcuts.
In `MovieController` update it to extend `BaseController`. This use statement is showing up in a darker
gray to indicate that it isn't being used any more and the same for the response use statement so delete
both of those.

With the `BaseController` in action, let's refactor `getEm` into the `BaseController`. Select the method,
one cool way to do that is hit `option+up` which will select larger and larger contexts. Now hit `control+t`.
Select Pull Members Up from the menu, which will pull them up to the top class. It already recognizes that
`BaseController` is the top class, and at the bottom it's warning us that the access will be changed from
private to protected which is awesome! Hit refactor and we can see it's gone from this file, because now
it lives inside of `BaseController`. That there is a really fast way to refactor things!

Now that I have this here I'm realizing that `Em` is not that great of a name choice. So back to `command+t`,
select rename from the menu and change it to `getEntityManager` to make my code a little clearer. When we do
that I get a summar down here of all the spots in our project where PHPStorm sees `getEm`. Click the Do Refactor
button and we can see that it changed the name all over our project. Sah-weet!

There are a lot of other things you can do with the refactor feature in PHPStorm. For example, we can extract
this out to a variable. This could add a level of clarity to what things are.

Say you get into a spot where you messed up your formatting in some terrible way. Oof that looks just awful.
Make it stop! At any point you can go up to the code menu at the top and select reformat code, which is also
`command+option+L` and it will tidy that back up for you.

So let's hit `command+A` to select all the code I want to reformat, then `command+option+L` and now everything
is back into place based on our coding standards, which you can of course control. 



