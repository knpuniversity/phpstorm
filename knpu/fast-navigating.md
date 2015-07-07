# Fast Navigating

I just hate seeing developers click manually into their directory tree to search for
things. Most projects are too big to be opening files like this. Really, you want to
have your hands off your mouse as often as possible.

Time to introduce you to some new best friend shortcuts for navigating! In fact, PHPStorm
thinks they're so important that they even have some of these listed front and center when
you don't have any files open.

## Navigating to Class and File

Click the navigate menu at the top. The first option in the list is "Navigate to Class". Its
shortcut is `command+O`. Knowing that I want to get into the `MovieType` class, I'll hit
`command+O`, start typing the name and boom, I've got that open with just my keyboard. 

Need to open a file, like config.yml? Well you're in luck, just use `command+shift+O`,
start typing the file name in the search box and there it is. We could even look up this
`bootstrap_3_layout` thing here. Use `command+shift+O` again, type the file name, and we
can see where it is in the project.

Great! In this case we can see how deep that structure is for this particular file, it's
way down in Symfony. If I saw you navigating here manually, I'd be tempted send Samuel
L Jackson to your office to tip over your chair. He'd arrive before you navigated there.

## Navigating Deep Directories

And what's *really* cool - other than *not* being tipped over by Sam - is that we can
use the navigation tree on top to actually click and look around inside of these deep
directories.If we really wanted to, we could move the tree on the left all the way to
that specific spot by double clicking that directory name at the top. And now we're there
and can look around and see what other interesting stuff is hiding here.

## Navigating to Function Names

The next shortcut on the list up there is "Symbol", which is `command+alt+O`. Symbol is
referring basically to function names. So here we can look for something like the `buildForm`
method from inside of my `MovieType`. And now it's showing me all of the instances in the
project where `buildForm` is used. I'll pick the top one and it takes me straight there. 

Inside of my controller I call `createForm`. So back to `command+alt+O`, type `createForm`,
and there is the one inside of the base `Controller` class we extend. This is the function
I am calling when I say `$this->createForm()` from inside `MovieController`.

## Clicking into Functions

In this case, if I wanted to know exactly where this `createForm()` function lives,
I would just hold command and click into it -- so don't forget about that shortcut as well.
We can do the same thing here for `handleRequest` if we needed to know where that is.
Clicking that will take us right into this core Symfony spot and again we can look around
inside of here and double click the tree to move us here.

## Recent Files

Most of the time, you might be interested in the shortcut `command+E`: this will pop up
a list of your recent files. Just start typing the name of the file you're looking for
until it appears in the results. 

## Navigating Tabs

Once you have some tabs open, you'll see me do this a lot: my cursor will stay in place
while I hold `command+shift+[` and `command+shift+]` to move around the open files. I use
this constantly to jump around from one file to the next.

## Searching ALL THE THINGS!

Okay, the last shortcut I'm going to show you for finding things in your project is easy
to remember: `shift+shift`. Hitting shift twice will open up a feature called 'search everywhere'.
This is a bunch of searches put together, where you can start typing `MovieController` and find that,
or `buildForm` and it will find that for you. Or you can even find CSS tags. In one of the core
Symfony files, there's a CSS snippet called `.block-exception`. And there it is in our list of
results. And clicking on it takes you straight to that file deep inside of Symfony.

There are a lot of ways to move around your project, but the biggest ones to remember are
`command+O` and `command+shift+O`. Or put them together, with `shift+shift`. 

Ya! We're working way faster.
