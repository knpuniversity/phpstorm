# Setup

Hey guys! If you've watched even one video on KnpU - please tell me that
you have - then you've seen me using PHPStorm. 

Now think about how much you use your editor. If you work 40 hours a 
week I bet you stare deeply into your editor at least 20 of those hours.
So over a year, that's... let's see here - carry the one - over 1,000 hours!

So if you could learn something that saves you a few seconds now, that's
going to mean you're saving 10's of hours in the future.

Particularly in Symfony development, mastering PHPStorm is going to 
completely speed up the way you develop and help you catch mistakes
you may have missed otherwise.

If you've never used PHPStorm before it does have a free trial period
that you can use to see if it's going to work for you.

## UI Updates

I'm working with a fresh version of PHPStorm, this is not how I want
my development environment to look - all this white is stressing me
out. So download your own copy and let's customize this thing together.

If I open any of my files right now you'll see that they look pretty ugly.
Let's clean that up first: open up preferences and in Appearance under
Appearance & Behavior you can select your theme, change that to Darcula.

(insert Dracular slow laugh here)

This is the theme of the UI which also goes and sets the scheme for the
editor. And this is already so much better. Staring into a white screen
for 1,000+ hours a year is very similar to just staring at a lightbulb -- not
so great on the eyes.

Speaking of eyes, I'd like to see my font size a bit bigger here. Back to
preferences, on a mac its shortcut is `⌘,` so I'll start using that. On
Windows and Linux, it's the longer `Ctrl+Alt+S` - you can check out the key 
mappings under the keymap section, to see and simplify these.

Use this search to look for font. This pulls up a few things, general appearance, 
colors & fonts. Let's pick font here and there's font size. 

I can't immediately change the font size I've got because that would change
the Darcula scheme. So first let's click 'save as' so we can customize this,
save it as 'darcula mine'. And now I can change the font size to 14 and give it a
line spacing of say 1.2. Ahh so much better.

## Project Organization

Over here on the left, you can see the `tuts` and `knpu` directories. I use
these to help me build this tutorial - but when I'm coding, I don't want
to see them. Any time you have a directory that you don't want PHPStorm to look
into, or that you just don't want to see, you can hide it. Right click `tuts`,
find 'mark directory as' and select 'excluded'. In a second that will hide this
for me. Let's also do this on the `knpu` directory.

And now we can change the view in the upper left from 'project' to 'project files'.
Let's also exclude this `.idea` directory. If you ever need to see those in the tree
again you can just switch back to 'project' and they'll reappear. Then you can even
unmark them if you want to.

## Plugins

Okay back to the 'project files' view. So PHPStorm is the best editor I've ever seen.
But the real power with Symfony comes from an *amazing* plugin. Back in preferences if
you search for Symfony it brings you to a plugin spot. Click 'Browse Repositories',
here you see the community plugins for Symfony and there's one called the 'Symfony
2 Plugin'. To prove how great it is just look at its 1.2 million downloads. So press
the 'Install Plugin' button to get this added to our IDE. 

The other plugin that you are definitely going to want to install is this called
'PHP Annotations'. Find that one in the search and install it. Perfect.

Close out of this window, and then press ok and restart PHPStorm.

You only need to install the Symfony plugin once, but each time you start a new project you
will need to enable it. Back in preferences, search Symfony and check the
'Enable Plugin for this Project' checkbox. Do that just one time per project - not bad!

The checkbox had a note that it requires a restart, that's mostly not true. But I am going
to restart one more time because there are a few small features that will not work until
you do this.

Now we're really ready to go! I've already got my my site running on localhost:8000 and
we've got a nice looking 404 page since there isn't anything inside of here yet. 

Just to prove that the Symfony Plugin is installed and running, in the bottom right of
PHPStorm you should see a little Symfony menu. Clicking it gives you a quick way to
jump into the profiler for any recent requests.

Now that our editor is all setup let's get down to work!
