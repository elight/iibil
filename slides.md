
!SLIDE middle
# Evan Light
## **<u>Freelance Mentor and Code Janitor</u>**
## [@elight](http://twitter.com/elight)
## [http://tripledogdare.net](http://tripledogdare.net)
## [evan.light@tripledogdare.net](mailto:evan.light@tripledogdare.net)

!SLIDE middle
}}} images/stuff_i_do-16x9.png

!SLIDE
# "[Use Rails until it hurts](http://evan.tiggerpalace.com/articles/2012/11/21/use-rails-until-it-hurts/)"

!SLIDE
# Martin Fowler's [Patterns of Enterprise Application Architecture](http://www.amazon.com/gp/product/0321127420/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0321127420&linkCode=as2&tag=hipphack-20)

!SLIDE 
    I have a set of alarm bells that go off when people say, "Always do this".
-- Martin Fowler, Patterns of Enterprise Application Architecture

!SLIDE
# What about when we go
# off the Rails?
!NOTES
# Which patterns do we choose?
# Which tools?

!SLIDE
# It depends
!NOTES
# These questions are difficult to answer unless you're an expert

!SLIDE
# HEURISTIC
## noun, /hyo͞oˈristik/
## involving or serving as an aid to learning, discovery, or problem-solving by experimental and especially trial-and-error
##### [Source: Meriam-Webster](http://www.merriam-webster.com/dictionary/heuristic)
## &nbsp;
## TL;DR: experience-based

!SLIDE
# Contemporary alternative Rails 
# patterns tend to use 
# their own idioms

!SLIDE
# But they're new 
### (at least to Rails)
# They're bleeding edge

!SLIDE bottom-right
}}} images/jarjar-16x9.jpg
# If it bleeds, it leads

!SLIDE
# NEOPHILIA
## noun \nē-ə-ˈfi-lē-ə\
## love of or enthusiasm for what is new or novel
###### [Source: Merriam-Webster](http://www.merriam-webster.com/dictionary/neophilia)
!NOTES
# Our blogs are full of "new"
# Our conferences are full of "new"
# We kid about our attraction to shiny

!SLIDE
    Once you have something that grows faster than education grows, you’re always going to get a pop culture.
-- [Alan Kay](http://queue.acm.org/detail.cfm?id=1039523)

!SLIDE
# New patterns and tools:
# our pop culture
!NOTES
# Less reliable due to being untried, less tried, or less understood

!SLIDE
# PATTERN
## noun /ˈpatərn/
## A form or model proposed for imitation : exemplar.
##### [Source: Meriam-Webster](http://www.merriam-webster.com/dictionary/pattern)

!SLIDE
# If it can be imitated
# maybe it can be automated

!SLIDE
# Step 1
# Identify practice

!SLIDE
# Step 2
# Name practice as pattern

!SLIDE
# Pattern ends here

!SLIDE
# Step 3
# Create tool from pattern
!NOTES
* Tools encode knowledge
* Reduces number of choices required by a pattern user

!SLIDE
# Step 4
# Identify best practices for tool
!NOTES
# Further reduce number of choices of a pattern user
# Managing the "paradox of choice"

!SLIDE
# Step 5
# Identify failings in tool
!NOTES
# Failings in our current practices lead us to new practices
# New practices lead to new patterns

!SLIDE
# Step 6
```
GOTO 1
```

!SLIDE
# Rails
## Automated patterns

!SLIDE
# Rais patterns
#### on the surface
## Front Controller
## Model View Controller
## Active Record
## Template View

!SLIDE
# Post-Rails Rails Patterns
## [Presenter](http://blog.jayfields.com/2007/03/rails-presenter-pattern.html) ([gem](https://github.com/jcasimir/draper))
## [Exhibit](http://objectsonrails.com/) ([gem](https://github.com/objects-on-rails/display-case))
## [Form Objects](http://pivotallabs.com/form-backing-objects-for-fun-and-profit/) ([gem](https://github.com/ClearFit/redtape))
## Policy Objects ([gem](https://github.com/bitlove/objectify))
## [DCI](http://dci-in-ruby.info/)
## [Service Object](http://jamesgolick.com/2010/3/14/crazy-heretical-and-awesome-the-way-i-write-rails-apps.html) ([gem](https://github.com/bitlove/objectify))

!SLIDE
# Where did all of these come from?

!SLIDE
# See Step 5: the failings of Rails

!SLIDE
# What's wrong with Rails?

!SLIDE
# Vox populi, vox Dei 
## Persistence and domain logic should not coexist in a model class

!SLIDE
# [Active Record](http://www.martinfowler.com/eaaCatalog/activeRecord.html)
    An object that wraps a row in a database table or view, encapsulates the database access, and adds domain logic on that data.
-- Fowler, POEAA

!SLIDE 
    I have a set of alarm bells that go off when people say, "Always do this".
-- Yep, still Martin Fowler

!SLIDE
# Are we doing it wrong?
    If the [database table to domain model] mapping is simple, [the] Active Record [pattern] does the ... job without an additional layer of code. If the mapping is complex, [the] Data Mapper [pattern] works better, as it's better at decoupling the data structure from the domain objects because the domain objects don't need to know the layout of the database.
-- Fowler, POEAA

!SLIDE
# "If the mapping is simple, Active Record does the ... job"

!SLIDE
# "If the mapping is complex, Data Mapper works better..."

!SLIDE
# Simple? Complex?

!SLIDE
# Heuristic

!SLIDE top-left
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

!SLIDE bottom-right
# [Repository pattern](http://martinfowler.com/eaaCatalog/repository.html)
}}} images/repository_pattern-16x9.png

!SLIDE
# Layering

!SLIDE
# The Cost of Indirection
    Refactoring tends to break big objects into several smaller ones and big methods into several smaller ones.  Indirection is a two-edged sword... Every time you break one thing into two pieces, you have more things to manage. It can also make a program harder to read as an object delegates to an object delegating to an object. So you'd like to minimize indirection.
-- Fowler, Refactoring

!SLIDE
# "Every time you break one thing into two pieces, you have more things to manage."

!SLIDE
# Managing software complexity is hard
# &nbsp;
## So have another beer!

!SLIDE
# [edr](http://github.com/nulogy/edr)
# &nbsp;
###### See [Building Rich Domain Models in Rails. Separating Persistence.](http://engineering.nulogy.com/posts/building-rich-domain-models-in-rails-separating-persistence)
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
# Redesign [edr](http://github.com/nulogy/edr) to automate more via reflection
## PDI

!SLIDE top-left
# Why not [DataMapper](http://datamapper.org)?
}}} images/datamapper.jpg

!SLIDE
# [DataMapper](http://datamapper.org) is not a true [Data Mapper](http://martinfowler.com/eaaCatalog/dataMapper.html)
### It's actually an Active Record
###### Confused yet?

!SLIDE
# [DataMapper 2](https://github.com/datamapper) is still WIP
# &nbsp;
###### For instance, DM2 doesn't yet have an official [Unit of Work](http://martinfowler.com/eaaCatalog/unitOfWork.html) implementation

!SLIDE
# [DataMapper 2](https://github.com/datamapper) is always looking for contributors
### Contact [@dkubb](http://twitter.com/dkubb) or
### or dkubb on #datamapper on freenode IRC

!SLIDE
# NEW UNEDITED CONTENT FOLLOWS

!SLIDE
# Vox populi, vox Dei 
## Rails templating sucks

!SLIDE
# Really, most templating ***still*** sucks

!SLIDE
    [C]ommon [templating] implementations make it too easy to put complicated logic in the page thus making it hard to maintain ... [and] to test...
-- Fowler, POEAA

!SLIDE
# Presenters, Decorators, and View Models
## [Presenters and Decorators: A Code Tour](http://www.confreaks.com/videos/884-railsconf2012-presenters-and-decorators-a-code-tour) by [Mike Moore](http://twitter.com/blowmage)
## [Fat Models Aren't Enough](http://blip.tv/rubynation/jeff-casimir-fat-models-aren-t-enough-5562605) by [Jeff Casimir](http://twitter.com/jcasimir)

!SLIDE
# JUNK DRAWER FOLLOWS

!SLIDE
# When and how do we use these newer patterns?
## Buy the book
## Read the blog post(s)
## Read the source
## Listen to the conference talk
!NOTES
Could almost use a flow diagram here! Is there a tool?  No? IS there a book?  No?  .....


!SLIDE
# Welcome to the bleeding edge
## Book? Ha!
## Blog post? Maybe one or two
## Conference talk? Maybe one or two but weaker examples than a good blog post.
## Source? Oh, you want me to build this pattern **for you**? Ha!

!SLIDE
# More moving parts
## In addition to Rails
## Add more complexity due to more types
## More files/nouns per project
## Easy things easy and hard things possible

!SLIDE
# Maybe these are the wrong patterns





!SLIDE left
# &nbsp;
# &nbsp;
# Attribution
# &nbsp;
#### [Glenn Goodrich](http://twitter.com/ruprictgeek): Introduced me to edr which led me to read POEAA
#### [Martin Fowler](http://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420): For his POEAA book
#### [Ryan Bigg](http://twitter.com/ryanbigg): For early feedback on this talk
#### [Gary Bernhardt](http://twitter.com/garybernhardt): [Capability vs. Suitability](http://www.youtube.com/watch?v=NftT6HWFgq0) informed early concepts for this talk

!SLIDE
# Citations
## Martin Fowler, [Patterns of Enterprise Application Architecture](http://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420)
!NOTES
# TODO: Finish this list from links in the preso if I have time!
