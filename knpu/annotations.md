#Annotations

We've got a big project today, a site about movies. But only movies that 
have Samuel L. Jackson. 

We'll start by creating a movie controller. We could right click on the
controller directory, go to new and select file from the menu. But instead
we'll use shortcuts. For mac users use ⌘n to get the new menu open, and because
we have the Symfony2 Plugin by typing 'controller' you'll find an option to create 
a controller. Let's keep things simple and obvious and call it 'MovieController'.

When you use Git PHPStorm asks you whether you want to add the file. I prefer to
just do this myself so I'll click 'no'. Beautiful!

We'll need a route to this MovieController, so add some annotations above indexAction.
Let's update these to `@Route` and let autocomplete do its thing. The one we want is
`Sensio\Bundle\FrameworkExtraBundle\Configuration\Route`, select that option and hit
tab and notice that it added a use statement on line 5. That's really important
because when you use annotations you need to have a use statement for them. Now instead
of spending your time looking it up in the documentation autocomplete will take care of it
for you. Robots FTW!

Let's have our route be `\movies\new` and change `indexAction` to `newAction`. And we'll
fix up our render call in a second. Head over to the browser and check if our new route 
is hitting our endpoint. Perfect! It can't find the template but that's fine because
there isn't one :)

###Annotation Options

Annotations have a lot of options, one of them is called `name` which we have autocomplete
for. Fill that in with `movies_new`. If you're the curious sort and wondering what other
options you have 


