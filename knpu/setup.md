#Setup

Hey guys! If you've watched even one video on KnpU then you've seen me
using PHPStorm. 

Now think about how much you use your editor. If you work 40 hours a 
week then it would be a fair guess that you are looking at your IDE 
20 hours every week, which is about 80 hours a month or 1,000 hours a
year!

So that means that if you can learn something that can save you a few
seconds in this tutorial that can add up to 10's of hours in the future.

Particularly in Symfony development, mastering PHPStorm is going to 
completely speed up the way you develop and help you catch mistakes
you may have otherwise missed.

If you've never used PHPStorm before it does have a free trial period
that you can use to see if it's going to work for you.

###UI Updates

I'm working with a fresh version of PHPStorm, this is not how my
development environment looks. So download your copy and we can get
this into working order together.

Let's get this into full screen first. If I open any of my files right 
now you'll see that they look pretty ugly. Let's clean that up first, 
open up preferences and in Appearance under Appearance & Behavior you 
can select your theme, change that to Darcula. This is the theme of the
UI which also goes and sets the scheme for the editor. This is already
so much better. Staring into a white screen for 1,000+ hours a year is
very similar to just staring at a lightbulb -- not so great on the eyes.

Speaking of eyes, I'd like to see my font size a bit bigger here. Back to
preferences, on a mac its shortcut is ⌘, so I'll start using that. Use this
search to look for font. This pulls up a few things, general appearance, 
colors & fonts. Let's pick font here and there's font size. 

I can't immediately change the font size I've got because that would change
the Darcula scheme. So first let's click 'save as' so we can customize this,
save it as 'darcula mine'. And now I can change the font size to 14 and give it a
line spacing of 1.2. Ahh so much better.

###Project Organization

Over here on the left, you can see the tuts and knpu directory. These are what I
used to help me build this tutorial. So any time you have a directory that you
don't want PHPStorm to look into, or you just don't want to see it in the tree
you can hide it. Right click tuts, find 'mark director as' and select 'excluded'. 
In a second that will hide this for me. Let's also do this on the knpu directory.

And now we can change the view in the upper left from 'project' to 'project files'.
Let's also exclude this .idea directory. If you ever need to see those in the tree
again you can just switch back to 'project' and they'll reappear and even unmark
them if you want to.

### Plugins

Okay back to the 'project files' view. So PHPStorm is the best editor I've ever seen.
But the real power with Symfony comes from a plugin. Back in settings if you search
for Symfony it brings you to a plugin spot. Click 'Browser Repositories', here you
see the community plugins for Symfony and there's one AMAZING one called the 'Symfony
2 Plugin'. To prove how great it is just look at its 1.2 million downloads. So press
the 'Install Plugin' button to get this added to our IDE. 

The other plugin that you are definitely going to want to install is this one called
'PHP Annotations'. Let's find that one in the search and install it as well. Perfect.

We can close out of this window, and then press ok which will ask you to researt 
PHPStorm which we definitely need to do.

You only need to install the plugin once, but each time you start a new project you
will need to enable the plugin. Back in preferences you'll search Symfony and clicking
the 'Enable Plugin for this Project' checkbox. That's just one time per project - not bad!

The checkbox had a note that it requires a restart, that's mostly not true. But I am going
to restart one more time because there are a few small features that will not work unless
you do this.

Now we're really ready to go! I've already got my my site running on localhost:8000, we've
got a nice looking 404 page since there isn't anything inside of here yet. 

Just to prove that the Symfony Plugin is now installed and running, in the bottom right of
PHPStorm you should see a little Symfony menu. Clicking it gives you a quick way to open up
the profiler.

Now that our editor is all setup let's get to the real work!

