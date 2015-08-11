# Forms

Now that we've got our entity let's create a form! Click on AppBundle, press our handy
shortcut `command+n`, and if you search form you'll find that option in the menu!
It's all coming together!

We'll call this `MovieType`:

[[[ code('02ed18b005') ]]]

Notice it was actually smart enough to put that inside of a `Form` directory *and*
build out the whole structure that we'll need. All I need next is for it to pour me
a cup of coffee.

The first thing we always do inside of here is call `$resolver->setDefaults(array())`
and pass the `data_class` option so that it binds it to our `Movie` entity. Conveniently,
this gives us more autocomplete: we can just type `Movie` and it adds the rest:

[[[ code('2ea35a9e0b') ]]]

## Configuring Form Fields

This will even help us build our fields. If we type `$builder->add('')` here, because
this is bound to our `Movie` entity, it knows all the properties we have there. So
let's plug in our property of `title` which should be a `text` field, `samsCharacterName`
which is probably a text field as well and `isMainCharacter` which will be a checkbox.
We'll want to make sure that we prevent html5 validation on that. A third argument of
`'required' => false` will take care of that for us and even that has autocomplete.
It's madness!

[[[ code('0e15d80b89') ]]]

Let's also include `rating` as an integer field and lastly, `releasedAt` which is a
date field:

[[[ code('41d1f189a4') ]]]

## Digging into Options and Fields

We can control how this date field renders: by default with Symfony it would be 3
select boxes. I'll set a `widget` option, except I don't remember what value to set
that to. No worries, I'll just hold the command key over the `widget` option and
it will take me straight to where that is setup inside of the core code:

[[[ code('f8fa91004e') ]]]

Why is that awesome you ask? Because I can search for what I need inside of here
and boom `setAllowedValues` `single_text`, `text` and `choice`. So let's paste
`single_text` back into our file.

[[[ code('e8dfebf605') ]]]

That trick of holding command and clicking works for the field types too: command+click
`integer` and suddenly you're inside the class that provides this!

[[[ code('53e2f2ef9f') ]]]

It's like being teleported but, you know, without any risk to your atoms. You can
even use this to take you to the property inside of `Movie` for that specific field. 

## Form Rendering

Our form is setup so let's go ahead and create this inside of our controller, 
`$form = $this->createForm(new MovieType(), $movie);`. Like always, we need to pass
our form back into our template with `$form->createView()`:

[[[ code('08e910f785') ]]]

Time to render this! Click into the `new.html.twig` template, ah that's right my
form is actually going to be over here in `_form.html.twig`. It shouldn't surprise
you that you'll get autocomplete here on things like `form_start` and `form_end`:

[[[ code('cf9b1912c8') ]]]

Want more autocomplete awesomeness you say? You're mad! But ok: type `{{ form_row(form) }}`
and it'll auto-complete the `title` field for you. So we'll plug in all of our fields
here:

[[[ code('2aa00e7f74') ]]]

And if I forget one of them, I can hit `control+space` to bring up all of my options.
This will also show you some other methods that exist on that `FormView` object.
Ah ok so we still have `rating` and `releasedAt` to add here. Clean up a bit of
indentation here and perfect!

[[[ code('130fee6193') ]]]

Time to try this out: back to our new movies page, refresh and there we go! It renders
with no problems other than the fact that this is a form only it's developer could
love. And well, maybe not even that: I'm going to make it prettier. In `config.yml`,
down in the `twig` key add `form_themes`:

[[[ code('22b519f3bb') ]]]

Now this should autocomplete, but for whatever reason this one key is not doing that.
But for the most part, you will see autocompletion inside of your configuration files.

## Form Theming

Right here let's plug in the bootstrap form theme: and the plugin isn't perfect because
we don't get autocomplete on this either. But I do know that there is a file inside
the project for bootstrap, so I'll go to find, file and start typing in bootstrap.
We want the one called `bootstrap_3_layout.html.twig`. To cheat, I'll just copy
that file name and paste that in here:

[[[ code('4768f4e24e') ]]]

Refresh with our new form theme and .... Awesome!
