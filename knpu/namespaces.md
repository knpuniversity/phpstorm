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
to the last part, in our case Movie, and let that autocomplete. 






