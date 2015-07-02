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

So as long as you have good PHPDoc that says what types of 

