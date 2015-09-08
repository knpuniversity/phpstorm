# Services

Alright, remember this hardcoded quote? Let's create a new class that can replace
this with a random Samuel L Jackson quote instead.

In `AppBundle` I'll create a new directory called `Service`. Inside of our new `Service`
directory let's add a php class called `QuoteGenerator`, and look how nicely it added
that namespace for us!

[[[ code('368a3cbb8c') ]]]

Let's get to work by adding `public function getRandomQuote()`. I'll paste in some
quotes, then we can use `$key = array_rand($quotes);` to get one of those quotes
and return it:

[[[ code('fed7cf3673') ]]]

## Registering a Service

Next, I want to register this as a service and use it inside of my controller. So hit
`shift+command+O`, search for `services.yml`, delete the comments under the
services key, and put our service name there instead. I'll give it a nickname of
`quote_generator`:

[[[ code('99b9186c2e') ]]]

Notice that PHPStorm is autocompleting my tabs wrong, I want to hit tab and have it
give me four spaces. So let's fix that real quick in preferences by first hitting
`command+,`, then searching for "tab". In the left tree find yml under "Code Style"
and update the indent from 2 to 4. Click apply, then ok and that should do it!

Yep, that looks perfect. As I was saying: we'll call the service, `quote_generator`,
but this name really doesn't matter. And of course we need the `class` key, and we
have autocomplete here too. If you hit `control+space` you'll get a list of all the
different keys you can use to determine how a service is created, which is pretty
incredible.

So we'll do `class`, but don't type the whole long name! Like everywhere else, just
type the last part of the class: here `Quote` and hit tab to get the full line.
Now add an empty `arguments` line: we don't have any of those yet:

[[[ code('a2feb2742e') ]]]

This is now ready to be used in `MovieController`.

Use `command+shift+]` to move over to that tab. And here instead of this quote,
we'll say `$this->get('')` and the plugin is already smart enough to know that
the `quote_generator` service is there. And it even knows that there is a method
on it called `getRandomQuote()`:

[[[ code('909822c3c7') ]]]

This is one my *favorite* features of the Symfony plugin.

Save that, head back to the form, refresh and now we see a new random quote at the
bottom of the page.

## Generating the Constructor

Now in `QuoteGenerator`, let's pretend like we need access to some service - like
maybe we want to log something inside of here. The normal way of doing that is with
dependency injection, where we pass the logger through via the `constructor`. So let's
do exactly that, but with as little work as possible.

I could type `public function __construct`, but instead I'm going to use the generate
command. Hit `command+n` and pick the "Constructor" option from the menu here. I don't
think this constructor comment is all that helpful, so go back into preferences with
`command+,`, search for "templates", and under "file and code templates", we have
one called "PHP Constructors". I'll just go in here and delete the comment from the
template.

Ok, let's try adding the constructor again. Much cleaner:

[[[ code('f3bccdba28') ]]]

## Generating Constructor Properties

At this point we need the logger, so add the argument `LoggerInterface $logger`:

[[[ code('7e10c0bf98') ]]]

This is the point where we would normally create the `private $logger` property above,
and set it down in the constructor with `$this->logger = $logger;`. This is a really
common task, so if we can find a faster way to do this that would be awesome. 

Time to go back to the actions shortcut, `option+enter`, select "Initialize fields", then
choose `logger`, and *it* adds all that code for you:

[[[ code('2e96111923') ]]]

We don't even have to feed it!

Farther down, it's really easy to use, `$this->logger->info('Selected quote: '.$quote);`:

[[[ code('3c0657befd') ]]]

We've added the argument here, so now we need to go to `services.yml`, which I'll
move over to. And notice it's highlighting `quote_generator` with a missing argument
message because it knows that this service has one argument. So we can say `@logger`,
or even `command+O` and then use autocomplete to help us:

[[[ code('2b66876735') ]]]

Head back, refresh, it still works and I could go down here to click into my profiler
to check out the logs. Or, in PhpStorm, we can go to the bottom right Symfony menu,
click it and use the shortcut to get into the Profiler. Click that, go to logs, and
there's our quote right there.

The autocompletion of the services and the ability to generate your properties is
probably one of the most important features that you need to master with PHPStorm
because it's going to help you fly when you develop in Symfony.
