#Forms

Now that we've got our entity let's create a form! Click on AppBundle, press our handy
shortcut command n, and if you search form you'll find that option in the menu! It's all
coming together!

We'll call ours MovieType, notice it was actually smart enough to put that inside of a form
directory for us and build out the whole structure that we'll need. All I need next is for it
to pour me a cup of coffee.

The first thing we always do inside of here is call `$resolver->setDefaults(array())` and pass
the `data_class` option so that it binds it to our movie entity. Conveniently this gives us one
other shortcut where we can just type 'Movie' and get an autocomplete on that spot. This will even
help us build our fields. If we type `$builder->add('')` here, because this is bound to our movie
entity it knows all the properties we have there. So let's plug in our variables of `title` which
is a `text`field, `samsCharacterName` which is probably a text field as well, `isMainCharacter`
which will be a checkbox and we'll want to make sure that we prevent html5 validation on that. A third
argument of `'required' => false` will take care of that for us and even that has autocomplete - what madness!
Let's also include `rating` as an integer field and lastly, `releasedAt` which is a date field. We can
control how this date field renders, by default with Symfony it would be 3 boxes. I'll use a widget option,
except I don't remember what value to set that to, so I'll hold the command key over the widget option and
it will take me straight to where that is setup inside of the core code. 

Why is that awesome you ask? Because I can search for what I need inside of here and boom `setAllowableValues`
`single_text`, `text` and `choice`. So let's paste `single_text` back into our file.

That trick of holding command and clicking an option name like the class behind the integer just command
click and you're inside integer type! It's like being teleported but without any risk to your atoms. 
You can even use this to take you into the proprety inside of movie for that specific field. 

Our form is setup so let's go ahead and create this inside of our controller, 
`$form = $this->createForm(new MovieType(), $movie);`. Like always, we need to pass our form back into
our template with `$form->createView()`. 

Time to render this! Click into the new.html.twig template, ah that's right my form is actually
going to be over here in _form.html.twig. It shouldn't surprise you that you'll get autocomplete
here on things like form.row, but it might surprise you that you will get it on the individual fields of the form.
This is going to help you remember that "Oh yea! We have a `{{form_start}}` and `{{form_end(form)}}`!" 

Want more autocomplete awesomeness? Typing `{{form_row}}` and you'll get `form.title`inserted in there for you.
So we'll plug in all of our fields here again and if I forget one of them I can hit control space to bring up
all of my options. This will also show you some other methods that exist on that form object. Ah ok so we still
have `rating` and `releasedAt` to add here. Clean up a bit of indentation here and perfect!

Time to try this out, back to our new movies page, refresh and there we go! It renders with no problems other than
the fact that this is a form only it's developer could love. And well maybe not even that, I'm going to fix that
in config.yml, down in the Twig key add `form_themes`. Now this shoudl autocomplete, but for whatever reason this
one key is not doing that, but for the most part you will see autocompletion inside of your configuration files.

###Form Theming

Right here let's plug in the bootstrap form theme, and the plugin isn't perfect because we don't get autocomplete
on this either. But I do know that there is a file on this inside the project, so I'll go to find, file and start
typing in bootstrap. We want the one called `bootstrap_3_layout.html.twig`. To cheat I'll just copy that file name 
and paste that in there.

Refresh with our new form theme and .... Awesome!

