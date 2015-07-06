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

To start, remove that public function



