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

At this point 


