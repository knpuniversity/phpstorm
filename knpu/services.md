#Services

Alright, remember this hardcoded quote? Let's create a new class that can replace it with
a random Samuel L Jackson quote instead.

In `AppBundle` I'll create a new directory called `Service`. Inside of our new `Service` directory
let's add a php class called `QuoteGenerator`, and look how nicely it added that service name for us!

Let's get to work by adding `public function getRandomQuote()`. I'll paste in some quotes, then we can
use `$key = array_rand($quotes);` to get one of those quotes and return it. 

I've isolated this logic somewhere else and I want to register this as a service and use it inside of my
controller. So hit `shift+command+O`, search `services.yml`, delete the commented out code under the
services key,  and put our service name there instead. I'll give it a nickname of `quote_generator`.

Notice that PHPStorm is autocompleting my tabs wrong, I want to hit tab and have it give me four spaces. 
So let's go ahead and fix that in preferences real quick by first hitting `command+,`, then searching out
tab. In the left tree find yml under Code Style and update the indent from 2 to 4. Click apply, then ok and
that should do it!

Yep, that looks perfect. As I said, we'll call the service, `quote_generator`, but this name really doesn't matter.
And of course we need the class key, and we get autocomplete again here. If you hit `control+space bar` you'll get
a list of all the different things that you can have inside of a service definition which is pretty incredible. 
It even includes different versions! 

So we'll do class, and instead of typing the whole long thing we have autocomplete here. Like everywhere else, start
with the end, here we'll type `Quote` and get the full line. Now add arguments, which we don't have any of. This is
now ready to be used in `MovieController`.

Use `command+shift+]` to move over to that tab. And here instead of this quote, we'll say `$this ->get('')` and
the plugin is already smart enough to know that the `quote_generator` service is there. And it even knows that
there is a method on it called `getRandomQuote`. Which is pretty incredible. 

Save that, head back to the form, refresh and now we see a new random quote at the bottom of the page.

Now in `QuoteGenerator` let's pretend like we need access to some service. To keep things simple, let's say we
want to log something inside of here. The normal way of doing that is with dependency injection, we pass this
through the `constructor`. So that's what we'll do here!

I could type `public function __Construct`, but instead I'm going to use the generate command. With `command+n`
and pick the Constructor option from the menu here. I don't think this constructor comment is all that helpful,
so going back into preferences with `command+,`, search for templates, and under file and code templates
we have the one for PHP Constructors. I'll just go in here and delete the comment in there.

Ok, let's try adding the constructor again, there we go! 

Now it only plugs in the stuff that we need. At this point we need the logger, so add `LoggerInterface $logger`.
This is the point where we would create the `private $logger` above, and set it down here as `$this->logger = $logger;`.
This is a really common task, so if we can find a faster way to do this that would be awesome. 

Time to go back to the actions shortcut, `option+enter`, select Initialize fields, `logger`, and it goes and adds all
that code for you. We don't even have to feed it!

Farther down here it's really easy to use, `$this->$logger->info('Selected quote: '.$quote);`. We've added the argument
here, so now we need to go to `services.yml`, which I'll move over to, and notice it's highlighting `quote_generator`. 


