#Namespaces

Since we have this new movie form we're going to want to save the data to the database. 
To do this let's create a movie entity. I'm not going to generate it, let's just do this 
in a good ole fashioned PHP Class called 'movie'. When I do this, notice the namespace
is empty. I could type `AppBundle\Entity` here but I'd rather that it happend automatically
for me. 

The way to do that is to set `src` as a resource route. Go into preferences, search
for 'directories' and here you can see the three directories that we excluded earlier, if you
want you can unmark these as excluded here. Click on `src` and click the blue sources route
button above. Now we can see this on the right, clicking the little 'p' allows us to edit the 
properities. So, if we were using PSR-4 inside of this directory we could actually put our prefix
in this box. But for now we're aren't worrying about that, all we needed to do was mark it as a 
source route which is done!

When we head back, oh look the entity directory is actually missing! Where did we miss place that?
Well, sometimes PHPStorm does that to empty directories, temporarily I'll switch back to project
view and now do a new PHPClass where we have this nice autocomplete. Let's call it Movie.

Okay switch back to Project Files and there it still is. Excellent! In a second we'll set this up
as an entity but right now I want to use it inside of my movie controller. We'll add a form here
in the future, and we'll need a new movie object, so we'll say `$movie = new`... I could end this
with AppBundle\Entity\Movie -- but you really don't want to do that. Always go directly
to the last part, in our case Movie, and let that autocomplete. When you do that it adds the use
statement on line 5 which is HUGE. If you are not using the autocomplete functionality for
use statements then you're killing your productivity.

Now if something went wrong and you didn't autocomplete or you end up with Movie over here without
the namespace you can import it if you want. Just hit alt and enter. Alt enter is the first important
shortcut we are going to see. It's called the actions shortcut. Often when you're in the code you can
alt enter and get a list of actions to do. I'll select 'import class' from this list and it will add
that use statement for us.

To take this a bit further let's add a `public function listAction()` that will list those movies
from the database. I don't want to build this out now, I just want it to return a simple response
that says to do. So let's add `return new Response` and select the response we want, which is the
one from HttpFoundation, hit tab, the use statement goes up that and I'll add 'TODO'. Now let's add
a route above this, `@Route("/movies", name = "movies_list")`. Oh and now that we have this second
endpoint, back in new.html.twig, if we want to create a link to it we can. So we can use another 
live template. Add an a tag, and use `{{path}}` and we'll get autocomplete on those. And for the link
text here we'll say "back to list'. 

Refresh that, and there's our link right back to our list. Awesome!

So, don't. write. use statements. ever.








