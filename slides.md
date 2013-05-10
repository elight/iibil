
!SLIDE middle
# Evan Light
## **<u>Freelance Mentor and Code Janitor</u>**
## [@elight](http://twitter.com/elight)
## [http://tripledogdare.net](http://tripledogdare.net)
## [evan.light@tripledogdare.net](mailto:evan.light@tripledogdare.net)

!SLIDE middle
}}} images/stuff_i_do-16x9.png

!SLIDE
}}} images/duty_calls-16x9.png::Duty Calls::::http://xkcd.com/386/
!NOTES
# Why I give presentations

!SLIDE
# "[Use Rails until it hurts](http://evan.tiggerpalace.com/articles/2012/11/21/use-rails-until-it-hurts/)"
### how this talk came to be
!NOTES
# Often why I write blog posts
# Blog post several months ago

!SLIDE
}}} images/all-the-things-16x9.jpg
!NOTES
# Response to this Rails backlash trend
# Almost anti-Rails
# Low coupling == good
# Loose coupling everything? Over-optimization.

!SLIDE
# Rails makes ***SMALL*** app development ***FAST***
!NOTES
# 20-ish models seems to be the fuzzy threshold for the 80%

!SLIDE
# Shortcuts via ***selective*** tight coupling
# &nbsp;
# Constraining around the first 80%
!NOTES

!SLIDE
# Examples
!NOTES
# Shortcuts: Controller-View tight coupling on intance variables
# ActiveRecord: domain logic-persistence coupling

!SLIDE
## What about the remaining 20%?
# Which gem do I use?
# Which pattern do I use?

!SLIDE top-right
# This is how I know
}}} images/opml.png

!SLIDE
# "It depends"
## There are too many choices!
!NOTES
# Requires an expert

!SLIDE
# HEURISTIC, noun
## /hyo͞o'ristik/
## involving or serving as an aid to learning, discovery, or problem-solving by experimental and especially trial-and-error
##### [Source: Meriam-Webster](http://www.merriam-webster.com/dictionary/heuristic)
## &nbsp;
## TL;DR: experience-based
!NOTES
# Requires background knowledge

!SLIDE 
# Anecdotes suck as evidence...

!SLIDE
}}} images/research-everywhere-16x9.jpg


!SLIDE
> Choosing well is especially difficult

> for those of us determined to make 

> only the best choices

<cite>-- Barry Schwartz, [The Paradox of Choice](http://www.amazon.com/gp/product/0060005696/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0060005696&linkCode=as2&tag=hipphack-20)</cite>

!SLIDE
> We would be better off if we embraced certain voluntary constraints

> on our freedom of choice, instead of rebelling against them.

<cite>-- Barry Schwartz, The Paradox of Choice</cite>
!NOTES
# Inevitably, we're confronted with the results of poor choices
# But we accept expert-imposed constraints by using Rails

 

!SLIDE
# Available information > Reliable information

!SLIDE
# More vulnerable to effective advertising
# than we like to believe

!SLIDE
 > Once you have something that grows faster than education grows, 
 
 > you're always going to get a pop culture.
 
 <cite>-- [Alan Kay](http://queue.acm.org/detail.cfm?id=1039523)</cite>
!NOTES
# Pop culture is HIGHLY available
# Our culture lacks heavy commercial marketing
# But we market our OSS all of the time
## Blogs
## Conference talks

!SLIDE
# NEOPHILIA, noun
## /nē-ə-ˈfi-lē-ə/
## love of or enthusiasm for what is new or novel
###### [Source: Merriam-Webster](http://www.merriam-webster.com/dictionary/neophilia)
!NOTES
# Our blogs are full of "new"
# Our conferences are full of "new"
# We kid about our attraction to shiny
# We're obsessed with the bleeding edge

!SLIDE bottom-right
}}} images/jarjar-16x9.jpg::mangaholix::::http://mangaholix.deviantart.com/art/Kriss-HATES-Jar-Jar-Binks-163018356
# "If it bleeds, it leads"

!SLIDE
# New patterns and tools:
# Ruby community pop culture
!NOTES
# Less reliable due to being untried, less tried, or less understood

!SLIDE
# PATTERN, noun
## /ˈpatərn/
## A form or model proposed for imitation : exemplar.
##### [Source: Meriam-Webster](http://www.merriam-webster.com/dictionary/pattern)

!SLIDE
# Step 1
# Identify practice

!SLIDE
# Step 2
# Propose as pattern

!SLIDE
# But if it can be imitated
# maybe it can be automated...

!SLIDE
# Step 3
# Create tool from pattern
!NOTES
* Tools encode knowledge
* Reduces number of choices required by a pattern user

!SLIDE
# Step 4
# Use tool 
# and 
# Identify its best practice patterns
!NOTES
# Further reduce number of choices of a pattern user
# Managing the "paradox of choice"

!SLIDE
# Step 5
# Identify failings in tool
### familiarity breeds contempt
!NOTES
# Failings in our current practices lead us to new practices
# New practices lead to new patterns

!SLIDE
# Step 6
```
GOTO 1
```
### Look for next shiny pattern
<img src="images/troll.png" style="width: 600px; height: 600px; bottom: 100px; right: 300px; position: absolute"></img>

!SLIDE
# Rails patterns
## Front Controller
## Application Controller
## Model View Controller
## Active Record 
#### (note the space between **Active** and **Record**)
## Template View

!SLIDE
# Patterns of Enterprise Application Architecture
### by Martin Fowler
### &nbsp;
### If you get nothing else from this presentation...
# [READ THIS BOOK](http://www.amazon.com/gp/product/0321127420/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0321127420&linkCode=as2&tag=hipphack-20)


!SLIDE
# Post-Rails Rails Patterns
## [Presenter](http://blog.jayfields.com/2007/03/rails-presenter-pattern.html) ([gem](https://github.com/drapergem/draper))
## [Exhibit](http://objectsonrails.com/) ([gem](https://github.com/objects-on-rails/display-case))
## [Form Objects](http://pivotallabs.com/form-backing-objects-for-fun-and-profit/) ([gem](https://github.com/ClearFit/redtape))
## Policy Objects ([gem](https://github.com/bitlove/objectify))
## [Data Context Interaction a.k.a. "DCI"](http://dci-in-ruby.info/)
## [Service Object](http://jamesgolick.com/2010/3/14/crazy-heretical-and-awesome-the-way-i-write-rails-apps.html) ([gem](https://github.com/bitlove/objectify))
## etc., etc. ...

!SLIDE
# Why?
## See Step 5: the failings of Rails

!SLIDE
}}} images/bones-16x9.jpg

!SLIDE
# What's wrong with Rails?
## A few examples

!SLIDE
# Vox populi, vox Dei 
## Persistence and domain logic should not coexist in a model class

!SLIDE
# [Active Record](http://www.martinfowler.com/eaaCatalog/activeRecord.html)
> An object that wraps a row in a database table or view, 

> encapsulates the database access, 

> and adds domain logic on that data.

<cite>-- Fowler, POEAA</cite>

!SLIDE bottom-left
# But prevailing wisdom says to do this
}}} images/rowdatagateway-16x9.png

!SLIDE
# There's a pattern for that!
#### &nbsp;
## [Row Data Gateway](http://martinfowler.com/eaaCatalog/rowDataGateway.htm)
#### Think of it as ActiveRecord minus domain logic

!SLIDE
# ActiveRecord often isn't the best fit
> If the [database table to domain model] mapping is simple, [the] Active Record [pattern] does the ... job without an additional layer of code. If the mapping is complex, [the] Data Mapper [pattern] works better, as it's better at decoupling the data structure from the domain objects because the domain objects don't need to know the layout of the database.

<cite>-- Even more Fowler, POEAA</cite>

!SLIDE
}}} images/fowler.jpg

!SLIDE
# "If the mapping is simple, 
# Active Record does the ... job"

!SLIDE
# "If the mapping is complex, 
# Data Mapper works better..."

!SLIDE
# Simple? Complex?

!SLIDE
# Heuristic

!SLIDE top-right
# Data Mapper
}}} images/data_mapper-16x9.png

!SLIDE
# Clear separation between
## source
## mapping
## model

!SLIDE
# Can we use Active Record as part of a Data Mapper?

!SLIDE
}}} images/yo_dawg_orm2-16x9.jpg

!SLIDE
# Layering is a two-edged sword
> Layers encapsulate some, but not all, things well.  As a result you sometimes get cascading changes.  The classic example of this in a layered enterprise application is adding a field that needs to display on the UI, must be in the database, and thus must be added to every layer in between.

<cite>-- You should be used to seeing Fowler by now, POEAA</cite>

!SLIDE
# "[Y]ou sometimes get cascading changes"

!SLIDE
# Indirection is also a two-edged sword
> Refactoring tends to break big objects into several smaller ones and big methods into several smaller ones.  Indirection is a two-edged sword... Every time you break one thing into two pieces, you have more things to manage. It can also make a program harder to read as an object delegates to an object delegating to an object. So you'd like to minimize indirection.

<cite>-- Fowler, Refactoring</cite>

!SLIDE
# "Every time you break one thing into two pieces, 
# you have more things to manage."

!SLIDE
# Managing software complexity is hard
# &nbsp;
## Fuck it.
## Let's go have a dram

!SLIDE
}}} images/scotty.png

!SLIDE bottom-left
# [Repository](http://martinfowler.com/eaaCatalog/repository.html)
}}} images/repository_pattern-16x9.png

!SLIDE
# [edr](http://github.com/nulogy/edr)
# &nbsp;
##### See [Building Rich Domain Models in Rails. Separating Persistence.](http://engineering.nulogy.com/posts/building-rich-domain-models-in-rails-separating-persistence)
!NOTES
# "Poor-man's" Data Mapper (until DM2 is ready)
# Refactor to this from a "fat model" ActiveRecord class 

!SLIDE
# ActiveRecord
# &nbsp;
@@@ ruby
class OrderData < ActiveRecord::Base
  self.table_name = "orders"

  attr_accessible :amount, :deliver_at

  has_many :items, class_name: "ItemData", foreign_key: "order_id"

  validates :amount, numericality: true
end
@@@

!SLIDE
# Domain Model 
### (sort of...)
# &nbsp;
@@@ ruby
class Order
  include Edr::Model

  fields :id, :amount, :deliver_at

  wrap_associations :items

  def add_item attrs
    wrap association(:items).new(attrs)
  end
end
@@@
!NOTES
# The above could be generated via reflection
# Domain Model could then just be a Domain Model
# maybe EDR::Model < ActiveRecord::Base
# In reality, it could reopen the EDR::Model subclass

!SLIDE
# Domain Model to ActiveRecord
# &nbsp;
@@@ ruby
Edr::Registry.define do
  map Order, OrderData
  map Item, ItemData
end
@@@
!NOTES
# This could be accomplished implicitly via a naming standard for the classes and reflection

!SLIDE
# Repository
# &nbsp;
@@@ ruby
module OrderRepository
  extend Edr::AR::Repository
  set_model_class Order
	
  def self.find_by_amount amount
    where(amount: amount)
  end
end
@@@

!SLIDE
# Redesign [edr](http://github.com/nulogy/edr) API for terseness
# via reflection
## see my [fork](https://github.com/elight/edr)
### a (slow) work in progress

!SLIDE top-left
# Why not [DataMapper](http://datamapper.org)?
}}} images/datamapper.jpg

!SLIDE
# [DataMapper](http://datamapper.org) is not a true [Data Mapper](http://martinfowler.com/eaaCatalog/dataMapper.html)
### It's actually an Active Record
###### Confused yet?

!SLIDE
# [DataMapper 2](https://github.com/datamapper) ***is*** a true Data Mapper

!SLIDE
# [DataMapper 2](https://github.com/datamapper) is always looking for contributors
# &nbsp;
### Contact [@dkubb](http://twitter.com/dkubb) or
### or dkubb on #datamapper on freenode IRC

!SLIDE
# Vox populi, vox Dei 
## Rails templating sucks

!SLIDE
# Really, ***most*** templating sucks

!SLIDE
> [C]ommon [templating] implementations make it too easy to put complicated logic in the page thus making it hard to maintain ... [and] to test...

<cite>-- Fowler, POEAA</cite>

!SLIDE
# Presenters, Decorators, and View Models
# &nbsp;
## [**Presenters and Decorators: A Code Tour**](http://www.confreaks.com/videos/884-railsconf2012-presenters-and-decorators-a-code-tour) by [Mike Moore](http://twitter.com/blowmage)
## [**Fat Models Aren't Enough**](http://blip.tv/rubynation/jeff-casimir-fat-models-aren-t-enough-5562605) by [Jeff Casimir](http://twitter.com/jcasimir)
!NOTES
# These techniques and tools can help but maybe we'd benefit from something more turtles all the way down?

!SLIDE
# [Cells](https://github.com/apotonick/cells)
# &nbsp;
### What if we had component views instead of partials?

!SLIDE
# Template
# &nbsp;
@@@ ruby
<div id="header">
  <%= render_cell :cart, :show, :user => @current_user %>
@@@

!SLIDE
# Cell
### Very much like a Controller
### &nbsp;
``` ruby
class CartCell < Cell::Rails
  def show(args)
    user    = args[:user]
    @items  = user.items_in_cart
		  
    render
  end
end
```
!NOTES
# Dabbled with cells
# Call to render is currently required
# ***Almost*** turtles all the way down

!SLIDE
# Model View Controller Pattern

!SLIDE
# Are Cells better than Partials?

!SLIDE
# The Layering hobgoblin

!SLIDE
# Can we be ***more Rails than Rails?***
## &nbsp;
## Data Mapper 2
## Cells

!SLIDE
# Tools that can help you now
## Cells: Model View Controller Pattern
## Draper: Decorator Pattern

!SLIDE
# For the future
### and could use your help
## Edr: Repository Pattern 
## DataMapper 2: Data Mapper Pattern



!SLIDE middle
# THANKS!
# &nbsp;
## Evan Light
### **<u>Freelance Mentor and Code Janitor</u>**
### [@elight](http://twitter.com/elight)
### [http://tripledogdare.net](http://tripledogdare.net)
### [evan.light@tripledogdare.net](mailto:evan.light@tripledogdare.net)
