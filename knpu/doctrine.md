# Doctrine

We have a `Movie` class, but its missing all of its annotations! Yikes! I *really* don't
feel like typing all of that.

Let me introduce you to another really important shortcut: generate. You can get to
it with `command+n`. Or just click the code menu at the top, and select generate.
Either way in this class, go down to "Generate ORM Class": and just like *all* menus
in PhpStorm, you can just start typing to search for it.

Sweet - this automatically added all the `Entity` annotation stuff on top for us.

[[[ code('1541652c30') ]]]

But it looks different: usually we'd just have the `@ORM\Entity` stuff on top, and
it added it this way because we don't have the `use` statement yet. There's a simple
solution to that.  Just copy the full `Entity` annotation, say `use`, paste that and
then delete the last part and instead stay  `as ORM;`:

[[[ code('9b747d1705') ]]]

That's the standard `use` statement that you see at the top of all Doctrine entities.

Let's get rid of these lines here, then get back inside of the class because context]
is important with `command+n`. Hit command n and search for 'ORM' and select
"Generate ORM Class":

[[[ code('c1e8be4218') ]]]

Perfect!

Let's add our properties, `private $id;`, `private $title;` for the movie title, 
`private $samsCharacterName` for Sam's character, `private $rating` to give the
movie appearance a rating, `private $isMainCharacter` so we can see if Sam was the
lead in that movie, and lastly `private $releasedAt` which will tell us exactly when
the movie came out.

[[[ code('dd37ce7e7f') ]]]

Easy!

The warning here is that each of these is an unused private field, which is true so
far. But good to know, in the future that could just be extra code.

## Generate ORM Annotations

Now that we have these we can go back to command n, search ORM and select
"Generate ORM annotations". Select all of the fields that are in the menu and hit
ok:

[[[ code('710e4fd487') ]]]

Awesome! Each field has all its annotations! Even better than that, it recognizes
that `id` is our primary key so it set that up and it noticed that `$isMainCharacter`
is probably a boolean, because of the 'is' in the beginning. And it also saw that
`$releasedAt` is a `datetime`. This isn't perfect, I would prefer `$releasedAt` to
just be a date, and rating up here is not a string, but an integer:

[[[ code('421c524e46') ]]]

But I do love getting autocomplete on all of those different types. Pressing
`control+space` gives you a list of all the different types you have access to.

Ok, let's give `$isMainCharacter` a default value just in case it's ever not set.
We'll make `$releasedAt` optional since a movie might not be released yet: set
`nullable=true`: more autocomplete:

[[[ code('5c6d08d9d7') ]]]

Up here for `$samsCharacterName`, well this probably won't be too long so we can
give it a length of 100 instead of the default 255:

[[[ code('76ea2ad0b9') ]]]

Alright, this is all looking really nice.

## Generating Getters and Setters

At this point we just have private properties so we need our getters and setters.
Back to generate! Use our favorite shortcut, command+n, select getters and then
`$id`:

[[[ code('53abef0cae') ]]]

Then back to generate and select getters and setters and select everything else.
Before I finish this I want to pause and say that you don't necessarily need a getter
and setter for every field in Doctrine. Sometimes you might want to wait to add the
getters and setters until you actually need them. Then when the need arises you have 
these awesome shortcuts available.

[[[ code('c02dcb5e61') ]]]

If I press `command+,` to get into preferences, you'll find that the templates that
generate these methods are editable. Search for "templates", and you'll see the area
where you can modify the getter and setter templates. I've already done this: usually
they generate with some PHPDoc, which to me is kind of meaningless, so I've already
removed it for nice clean rendering.

## Generating the Repository

One last thing here! This entity needs a repository. Back to the action shortcut,
which is... `alt+enter`! This opens up a menu to add the doctrine repository, which
as you may have guessed, adds a repository class here:

[[[ code('c689aab62b') ]]]

[[[ code('7b628a4bef') ]]]

In my case I prefer to have these in a `Repository` directory. So that's nice that
it helped me create that, but I'll move it manually. 

A quick copy and paste will do that, then update the namespace to end with `Repository`:

[[[ code('dfd410a2d9') ]]]

Even though I had to move that manually, what's really cool is that it's highlighting and
saying "Yo! Your repository Class is messed up! You can't use the short class name because
now it's in a different namespace." I can delete what's there  and type `MovieRepository`
and I get autocomplete on the entire name:

[[[ code('ebf90a195a') ]]]

And there's more autocompleting goodness I won't show here for when you're building
relationships and using the Query Builder.
