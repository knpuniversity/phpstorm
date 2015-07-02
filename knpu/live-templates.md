#Live Templates

Now that we have a form rendering we want to be able to submit it! Crazy idea, I know
but let's see what we can do. We'll use our standard code for this
`$form->handleRequest($request);` now we don't have the request object yet, so let's put
our type hint in for it. And like always, make sure you have the right one and let it autocomplete
so it will add the use statement for you. And real quick, plug request in here too.

Below, let's add `if ($form->isValid())` with a TODO to remind us to actually start saving stuff. 
Next, there are two things we typically do, first add a flash message, like "Sam would be proud".
And I truly think he would. And second, we redirect with `return $this->redirectToRoute()` and let's
send our users to the movies list, which we get a nice autocomplete on. 

That was pretty easy, but we'll be writing those 8 lines of code over and over and over again inside
of our project. We can do better! To fix that we are going to use something called a "Live Template".
That's what lets us just type a in a twig template, hit tab and get a full a tag printed out. We want 
the same idea and have it generate all this form handling boiler plate code for us. 

To make this, first select all the code that you want included. Then click on the tools dropdown menu,
and select "Save as Live Template". Let's give this a name, like `formhandle` with a description of
"Adds controller form handling code". Inside the template text let's tweak the indentation but other
than that let's just leave it alone. Oh and double check that you have the correct template name down there,
then hit 'ok'.

 Now that we have this we can delete our handleRequest and if statement and replace it instead with 
 `formhandle` and hit tab to enjoy our handy autocompletion. There it is!
 
Of course now we need to make parts of this dynamic. We'll need to go edit our live template...how do we do that?
Well, it's probably in the preferences menu and if we search for it there it is.

We'll assume that the variable is always called `$form` because it ususally is, but we do want to change our success
message here. Let's swap it out for `'$SUCCESSMESSAGE$'` with dollar signs on both sides and surrounded in quotes. 
Let's do the same thing down here in the redirect, we'll change that to `'$ROUTENAME$'`. In the event that the route
has parameters add in array next to it for convenience.

Now, let's get rid of this stuff and again type in `formhandle` and let that autocomplete. Type in 'Sam would be proud'
for our success message and `movie_list` for our redirect. Now that is awesome and so much faster than typing it all out
again and again and again.

Another great spot to use Live Templates is inside of this form row stuff since we'll be typing this all the time. 
copy one of our rows, go to tools and Save as Live Template. We'll call this one `formrow` with a description of
"Renders form_row in Twig". Below there's a note saying its applicable for HTML, HTML text and HTML Twig files. 
Let's update this line of code to be `form.$FIELD$`, click ok and now we can try this out.

 Type `formrow` hit tab and now we can just start typing in the field property name and select it from the list that
 pops up. Now, as great as formrow is, sometimes you can't use it. womp womp. That's when you'll end up entering the
 fields manually and they'll look like this, `<div class="form-control"></div>` and break it out into the three 
 different parts. `{{form_label(form.releasedAt)}}`, and copy that and update for form widget, and form errors. 
 Clearly this is also begging to be turned into a Live Template. 
 
 You know the drill! Select the full div, go to tools, Save as Live Template. Let's name this one formrowfull,
 and it Renders widget/label/errors. What's cool here is that these are duplicated, so we can just say `$FIELD$`
 and repeat that variable three times. Just a quick indentation fix there and click ok. Awesome!
 
 Let's get rid of the div we had, type formrowfull, hit the tab key, and as we start typing the property name
 we get the autocomplete and it's filling instantly on each of the three lines. I'll fix the spacing here to
 wrap it up!
