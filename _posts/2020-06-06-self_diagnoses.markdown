---
layout: post
title:      "Self.diagnoses"
date:       2020-06-06 21:14:44 +0000
permalink:  self_diagnoses
---


In the current climate it looks like there is alot of self diagnosis going on, trapped in our homes people are reflecting. Do we really need to go into the office everyday? Do we have to do the awkward unneccessary hug and kiss when we greet new people? Is public transport the right method to take for a 15minute walk? 

Along with this self reflection, there is also an immense feeling of community and solidarity. Young people helping with shopping for the elderly, communities supporting local producers. People are integrating, talking and supporting others they would of never crossed paths with before. Hence I created a [plant diagnostics](https://github.com/RebeccaHA/plant-diagnostics) app, users can help each other care for their plants and also upvote the best diagnosis. 

I feel the same support and community in the development world. So I feel a fitting topic is to talk about Single Sign-On and how other 3rd party providers help support that.

We were tasked with creating an app with certain requirements, one requirement was the ability to sign in to the app using a 3rd party provider. It's something we see all over the web 'Sign in using Google', so it's great knowledge and experience to have in your back pocket.

To make the magic happen, you need support from a few Rails gems created by the development community (cheers guys!). First, '[OmniAuth](https://github.com/omniauth/omniauth)' is needed, then followed by its close friend 'OmniAuth-#{insert provider here}'. Then lastly we need to lean on the '[dot-env](https://github.com/bkeepers/dotenv)' gem. 

Let's start with the easy one. DotEnv enables us to load variables into our configuration environment and gives us access to them in our ENV hash. This means we can have the option to access multiple key value pairs without updating our code each time. We store these keys and values in the .env file which lives at the root of the application. Don't forget we don't want other developers to have access to the inside of our pants, so include this file in the .gitignore so our private keys and values aren't uploaded into the repository. 

It should look something like this in the .env file: 
```
GOOGLE_OAUTH_CLIENT_ID=8681538697897567v3
GOOGLE_OAUTH_CLIENT_SECRET=837429hih878yr2uhir98000009808

```

Ok now for some more fiddly stuff. Most 3rd party providers have developer sites, giving us access to API's, analytics and all sorts of fun stuff. As always each one is slightly different but once you've figured out one with a few extra minutes of hunting you can easily grasp the others. 

The process tends to be create an app project, choose to set up a web configuration, enter your site URL (in this case your local host). Then add your redirect URIs, this is normally something like https://localhost:3000/auth/#{insertproviderhere}/callback. This is your default callback end point. With all of the above set up you should be able to grab the secret keys and add them into your .env file.

Now we need to start telling OmniAuth some of this information. Setting up an omniauth.rb file in our config initialisers folder and adding the following code: 
```
Rails.application.config.middleware.use OmniAuth::Builder do
    provider :google_oauth2, ENV['GOOGLE_OAUTH_CLIENT_ID'], ENV['GOOGLE_OAUTH_CLIENT_SECRET']
end
```
Gives OmniAuth access to our secret keys in the .env file. 

For the last piece of the puzzle we need to set up a route in order to initiate this whole proccess, OmniAuth has a standard convention for this /auth/:provider, with that set up we can use our old friend link_to and add a link for the user to click in order to sign in.

Similar to creating a user we need to set up the a create action in our controller that the route points to. It's great to stick pry into this to see what we are getting back from our 3rd party, there is all sorts. This can be found in our request.env['omniauth.auth'] hash. 

Let's use this time of relfection to learn, support and help each other. Hopefully this post will help support you when tasked with setting up a 3rd party single sign on.
	
	

