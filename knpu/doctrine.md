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
released. 


