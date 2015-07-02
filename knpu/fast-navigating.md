#Fast Navigating

We're moving onto navigating around our project. I just hate seeing developers do is click
manually into their directory tree to search for things. Most projects are too big to be opening
files like this. Really, you want to have your hands off your mouse or trackpad as often as possible.

Time to introduce you to your new best friend shortcuts! In fact, PHPStorm thinks they're so important
that they even have some of them listed right here when you don't have any files open. Click the navigate
menu at the top, the first option in the list is Navigate to Class. It's shortcut is command O. Knowing that
I want to get into the movieType class, I'll hit command O and start typing the name and boom, I've got that
open with just my keyboard. 

Need to open a file, like config.yml? Well you're in luck, just use command shift O, start typing the file
name in the search box and there it is. We could even look up this bootstrap_3_layout thing here. Use command
shift O again, type the file name, and we can see where it is in the project. Wait, why are there 3 of these files?
Well they all point to the same spot, so click anyone and you'll get to where you want to go.

Great! In this case we can see how deep that structure is for this particular file, it's way down in Symfony.

What's really cool, is that because we have this up here we can actually click on this and look around inside
of those directories.  If we really wanted to we can move the tree on the left all the way to that specific spot
by double clicking that directory name at the top. And now we're there and can look around and see what other
files are in there.

The next shortcut on the list up there is "Symbol", which is command alt O. Symbol is referring to function
names. So here we can look for something like the buildform method from inside of my MovieType. And now it's
showing me all of the instances in the project where buildform is used. I'll pick the top one and it takes
me straight there. 

Inside of my controller I call createform, so back to command alt O, type createform, and there the is the one
inside of the controller. And here is the function I am calling when I call createform. Hitting command O now will
let me open MovieController and what I'm referring to is this createform right there. 

In this case, if I wanted to know exactly where this createform function actually lives, I would just hold command
and click into it -- so don't forget about that shortcut as well. We can do the same thing here for handleRequest
if we needed to know where that is. Clicking that will take us right into this core Symfony spot and again we can
look around inside of here and double click that to move there.

Most of the time you might be interested in the shortcut command E, this will pop up a list of your recent files. 
Just start typing the name of the file you're looking for until it appears in the results. 

Once you have a ton of tabs open, you'll see me do this alot, my cursor will stay in place while I hold command shift
and then hit the left or right curly braces to move around the open files. I use this constantly to jump around from
one file to the next.

Okay, the last shortcut I'm going to show you for finding things in your project is shift shift. Hitting shift twice
will open up a feature called 'search everywhere'. This is a bunch of searches put together, where you can start typing
MovieController and find that, or buildform and it will find those for you. Or you can even find CSS tags. In one of 
the core Symfony files there's a tag called `.block-exception`, and there it is in our list of results. And clicking on
it takes you straight to that file deep inside of Symfony.

There are a lot of ways to move around your project, but the biggest ones to remember are the command O and command shift
O. Or to put them together, shift shift. 

Yay we're on our way to working way faster!
