---
layout: post
title:      "Corpse Reviver #2"
date:       2020-04-12 06:36:44 -0400
permalink:  corpse_reviver_2
---

Corpse Reviver #2 - A bright complex drink with a hint of anise.

It's project week two, week five of isolation and Easter weekend. Corpse Reviver seemed like a topical name. 

Amidst of all the craziness we were set the task of building a full stack Sinatra app. A great task for such bleak times. Speaking with friends I have heard how Corona Virus has affected so many people in different ways, sat in my frontroom cooking fancy dinners and treating it like a "holiday" I felt helpless. Why not use this time to better ourselves and help others. That's how the [Cocktail Suggester](https://github.com/RebeccaHA/cocktail-suggester.git) was created (yes I know the name needs a little work..).

A close friend of mine works as a Creative Drinks Consultant at [JKS](https://jksrestaurants.com/), with all of his clients closed for the foreseable future he was faced with some tough decisions. Give up on his dream or turn to stacking shelves? He knew he would look great in the fluorescent green fleece and hair net, but he isn't one for giving up. 

On a Tuesday evening over a video call, we were discussing some of lifes biggest questions 'how do vinyl players work?'. With Nils Frahm in the background, I asked my friend to make me a cocktail. He asked me to shout out the random bottles of booze I have leftover from various parties and he would suggest a cocktail. After a few Old Fashion's, the Power Rangers unite! His knowledge, my coding brawn, let's make something together.

<iframe src="https://giphy.com/embed/t6f2bNAjx7Bio" width="280" height="160" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

The coming together of two different backgrounds, forming ideas to solve the same goal is what I learnt in project week two and exactly what the nation is trying to do now. The remaining Power Rangers of mine and my friend's team were Bulma, Flash, Sinatra, ActiveRecord and CSV import, a great team! Sadly Boris is still sat on the bench.

My friend supplied me with an excel sheet of tantalising cocktails made from the random bottles of booze we all have in our cupboards. As people search in their cupboards, I searched google for 'Sinatra CSV import ruby'. Bingo! A ruby gem,  Sinatra-CSV made the team pretty quickly. This gem gives you access to the CSV class containing methods to read and parse data. So I added the cocktail.csv file to my project folder and the following code into my seed.rb file:

```
require 'pry'
require 'csv'

csv = CSV.open('db/cocktails.csv', headers: :first_row).map(&:to_h)
    csv.each do |row|
        cocktail = Cocktail.new
        cocktail.name = row['name']
        cocktail.description = row['description']
        cocktail.glassware = row['glassware']
        cocktail.ingredients = row['ingredients']
        cocktail.method = row['method']
        cocktail.garnish = row['garnish']
        cocktail.save
        puts "#{cocktail.name} saved"
    end
		
    puts "There are now #{Cocktail.count} rows in the cocktails table"
```

The CSV class opens the cocktail.csv file, taking the first row as headers (make sure they match your Object's attributes) and turning them into keys, it then maps through the file turning each row of data into a hash. 

Then it's like riding a bike, iterating through each hash creating a new cocktail instance in my database, setting the cocktail attributes to the cocktail.csv file hash keys. When ever you update or create a new instance, alway remember to save it(I got caught out on that one a few times).

Lastly, in this current climate, everyone knows and understands the importance of preparation. This situation is no different, make sure you prep your CSV file for import - otherwise like me you'll end up with 920 'nil' entries. 















