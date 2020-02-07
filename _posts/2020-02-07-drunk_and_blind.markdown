---
layout: post
title:      "Drunk and blind."
date:       2020-02-07 17:41:02 -0500
permalink:  drunk_and_blind
---


Coming to the end of my Ruby module, I was unleashed into the wild with the [final project](http://https://github.com/RebeccaHA/final-project-beers.git).

Set free like an owl trying to find it's barn house. You'd think by getting older you learn how to approach things like this e.g stabilizers on a bike before you can cycle, your first sip of beer before you hit the whisky. But no, as per I just dived straight in. Maybe this is the best way to learn? Though you wouldn't say that to a doctor.

Luckily I'm not a doctor, pass me the whisky.

During this project I learnt three things, two about myself and one technical. 

1. Dive in, code away, get something to work
2. Do the opposite of what your mum said, tidy up later
3. The value of self, instance methods and class methods

As this is a technical blog, I will talk you through number three. I felt a big part of this module was being able to differentiate between self, instance methods and class methods. When people explained it to me, their words were smattered with coding talk, which made it more confusing. After I decoded it, this is what I learnt and hopefully it will help others:

* SELF - Refers to the object itself that you are calling self on, could be an instance or a class

* INSTANCE METHOD - Functionality that can only be called on each instance

* CLASS METHOD - Functionality that can only be called on the class producing the instances

Let's put it into real world context, my family. I'm an instance, and I have lots of instance methods e.g cycling to work, thinking of stupid analogies. I have my brothers (other instances), we're similar but have different skills (methods), for example [my brother tries to sell male leggings](http://www.youtube.com/watch?v=WZ5AFwMIffY). 

Who produces all these instances, the class my Mum (sorry Mum, not to make you sound like a factory..).

```
class Mum
 def self.tidy_room
  puts 'class method'
 end
  
def cycle_to_work
 puts 'instance method'
end

end
```

Have a guess what do you think the above would return if you use those methods as class methods and then instance methods on the Mum Class? But let's not try to forget about what self represents here.

Class methods
```
Mum.self.tidy_room # => "class method"
Mum.cycle_to_work # => NoMethodError: undefined method 'cycle_to_work’ for Mum:Class
```

Instance methods
```
Mum.new.cycle_to_work # => instance method
Mum.new.tidy_room # => NoMethodError: undefined method ‘tidy_room’
```

My mum can tell me and my brothers to get in line by height or to tidy our room and we'd do it (probably..), but there is no way I would tidy my room by myself and I'm pretty sure my mum wouldn't get on a bike! 

So what's self I hear you ask? Self in this example is the Mum class, self is being called on Mum. What's self in Mum.new.self.cycle_to_work? The instance of the Mum class.

What does this all mean?

You can't call an instance method on a class and you can't call a class method on an instance. Self refers to the object you are calling self on whether that is a class or an instance.

So hopefully we've all learned one thing, maybe two.





