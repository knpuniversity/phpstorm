# Live Templates

Now that we have our form rendering, we want to be able to submit it! Crazy idea,
I know but let's see what we can do. We'll use our standard code for this
`$form->handleRequest($request);`. Now we don't have the `$request` object yet, so
let's put our type hint in for it. And like always, make sure you have the right one
and let it autocomplete to get the `use` statement for you. And real quick, plug
request in here too:

[[[ code('d57fabeb48') ]]]

Below, let's add `if ($form->isValid())` with a TODO to remind us to actually start
saving stuff. Next, there are two things we typically do here: first add a flash
message, like "Sam would be proud". And I truly think he would. And second, we redirect
with `return $this->redirectToRoute()` and let's send our users to the `movies_list`
route, which of course we get a nice autocomplete on:

[[[ code('8b19367400') ]]]

## Creating a Live Template

That was pretty easy, but we'll be writing those 8 lines of code over and over and
over again inside of our project. There must be a better way! To fix that we are going
to use something called a "Live Template". That's what lets us just type `a` in a
twig template, hit tab and get a full `a` tag printed out. We want to do the same
type of thing and have it generate all this form handling boiler plate code for us. 

To make this, first select all the code that you want included. Then click on the
Tools dropdown menu, and select "Save as Live Template". Let's give this a name, like
`formhandle` with a description of "Adds controller form handling code". Inside the
template text tweak the indentation but other than that, let's just leave this alone
for now. Hit 'ok'.

Now that we have this, we can delete our hard work. Replace it by typing `formhandle`,
hitting tab, and then... boom!

[[[ code('0d3e9dc470') ]]]

Enjoy that autocompletion.

## Live Template Variables
 
Of course now we need to make parts of this dynamic. We'll need to edit our live
template...how do we do that? Well, it's probably in the preferences menu and if
we search for it, it is!

We'll assume that the variable is always called `$form` because it ususally is, but
we do want to change our success message here. Let's swap it out for `'$SUCCESSMESSAGE$'`
with dollar signs on both sides and surrounded in quotes.  Let's do the same thing
down here in the redirect, we'll change that to `'$ROUTENAME$'`. In the event that
the route has parameters add in array next to it for convenience. Save this.

Get rid of the code and again type in `formhandle` and tab. Type in 'Sam would be proud',
hit tab, type `movie_list` for our redirect, then tab one more time. Now that is
awesome and so much faster than typing it all out again and again and again.

Another great spot to use Live Templates is inside of this form row stuff since we'll
be typing this all the time. Copy one of our rows, go to Tools and "Save as Live Template".
We'll call this one `formrow` with a description of "Renders form_row in Twig". Below,
there's a note saying its applicable for HTML, HTML text and HTML Twig files - so
that's right. Let's update this line of code to be `form.$FIELD$`. Click ok and now
we can try this out.

Type `formrow`, hit tab and now we can just start typing in the field property name
and select it from the list that pops up. Now, as great as `formrow` is, sometimes
you can't use it. womp womp. That's when you'll end up rendering a field manually,
which will probably be a `div` and the three parts: `{{ form_label(form.releasedAt) }}`.
Copy that and update for `form_widget`, and `form_errors`:

[[[ code('392cbecddb') ]]]

Clearly this is also begging to be turned into a Live Template. 
 
You know the drill! Select the full div, go to Tools, Save as Live Template. Let's
name this one `formrowfull`, and it "Renders widget/label/errors". What's cool here
is that there's just one variable that's duplicated 3 times. So we can just say
`$FIELD$` and repeat that each time. Just a quick indentation fix there and click
ok. Awesome!
 
Let's get rid of the div we had, type `formrowfull`, hit the tab key, and as we start
typing the property name we get the autocomplete and it's filling instantly on each
of the three lines. I'll fix the spacing here to wrap it up!

So, live templates: big win.
