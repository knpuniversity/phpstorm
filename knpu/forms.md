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
click and you're inside integer time! It's like being teleported but without any risk to your atoms. 
