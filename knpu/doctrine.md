#Doctrine

We have a movie class but its missing all of its annotations! Yikes! Fortunately all 
that stuff can be generated for us.

Let me introduce you to this second really important shortcut, generate. You can get to
it with command n. Or just click the code menu at the top, and select generate. Either way
in this class we're going to go down to 'Generate ORM Class' and just like all menus
you can just start typing to search it. And this automatically adds the stuff on top for us.

But it looks different, usually we'd just have the `@ORM\Entity` stuff on top, and it added
it this way because we don't have the use statement yet. There's a simple solution to that. 
Just copy this part, say 'use', paste that and then delete the last part and say `as_ORM;`.
That's the standard use statments that you'd see on the top of Doctrine entities. 

Let's get rid of these lines here, then get inside of the class because context is important
when you hit command n. Now actually hit command n and search for 'ORM' and select Generate
ORM Class. Perfect!

Let's add our properties, `private $id;`, `private $title;` for the movie title, 
`private $samsCharacterName` property for Sam's character, `private $rating` to give the
movie appearance a rating, `private $isMainCharacter` so we can see if Sam was the lead
in that movie, and lastly `private $releasedAt`which will tell us exactly when the movie was 
released. Easy! 

The warning here is that each of these is an unused private field, which is true so far.
But good to know, in the future that could just be extra code.

Now that we have these we can go back to command n, search ORM and select generate ORM annotations.
Select all of the fields that are in the menu and hit ok. Cool, each field now has its annotations!
Even better than that, it recognizes that ID is our primary key so it set that up and it noticed that
`$isMainCharacter` is probably a boolean, because of the 'is' in the beginning. And it also saw that
`$releasedAt` is a datetime. This isn't perfect, I would prefer `$releasedAt` to just be a date, and
rating up here is not a string, but an integer. But I do love getting autocomplete on all of those
different types. Pressing control space gives you a list of all the different types you have access to.

Ok, let's give `$isMainCharacter` a default value just incase it's ever not set. We'll make `$releaseDate`
optional since a movie could not yet be released and nullable = true which has an autocomplete.

Up here for `$SamsCharacterName`, well this probably won't be too long so we can give it a length to 100
instead of the default 255. Alright, this is all looking really nice.

At this point we just have private properties so we need our getters and setters. Back to generate!
Use our favorite shortcut, command n, select getters and then `$id`. Then back to generate and select getters
and setters and select everything else. Before I finish this I want to pause and say that you don't necessarily
need a getter and setter for every field in Doctrine. Sometimes you might want to wait to add the getters and
setters until you actually need them. Then when the need arises you have these awesome shortcuts available.

If I hold command , you'll find that these templates are editable. Search for templates, and you'll see the 
area where you can modify the getter and setter templates. I've already done this, usually they generate with
some PHPDoc, which to me is kind of meaningless so I've already removed it for nice clean rendering.

One last thing here! This entity needs a repository. Back to the action shortcut, which is alt enter!
This opens up a message to add the doctrine repository, which as you may have guessed, as a respository
class here. In my case I prefer to have these in a repository directory, so that's nice that it helped me
out but I'll move it manually. 

A quick copy and paste will do that, then update the namespace to end with `\repository;`. Even though I had
to move that manually what's really cool is that it's highlighting and saying "Yo! Your repository Class is
messed up! You can't use the short class because it's in a different namespace." I can delete what's there 
and type `MovieRepository` and I get autocomplete on the entire thing.

And there's more autocompleting goodness when you're building the @ORM relationships and queries in the
Query Builder.


