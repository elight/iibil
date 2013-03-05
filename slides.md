
!SLIDE middle
# Evan Light
## **<u>Freelance Mentor and Code Janitor</u>**
## [@elight](http://twitter.com/elight)
## [http://tripledogdare.net](http://tripledogdare.net)
## [evan.light@tripledogdare.net](mailto:evan.light@tripledogdare.net)


!SLIDE middle
}}} images/stuff_i_do.png

!SLIDE
# "[Use Rails until it hurts](http://evan.tiggerpalace.com/articles/2012/11/21/use-rails-until-it-hurts/)"
!NOTES

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
}}} images/jarjar.jpg
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
# New tools and patterns:
# our pop culture
!NOTES
# Less reliable due to being untried, less tried, or less understood

!SLIDE
# PATTERN
## noun /ˈpatərn/
## A form or model proposed for imitation : exemplar.
##### [Source: Meriam-Webster](http://www.merriam-webster.com/dictionary/pattern)

!SLIDE
# Step 1
# Identify practice

!SLIDE
# Step 2
# Name practice

!SLIDE
# Pattern ends here

!SLIDE
# But then we automate
# what we can predict

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
# PATTERN (software)
## noun /ˈpatərn/
## A set of concepts outlining a partial solution to a common technical problem
###### Source: Me

!SLIDE
# Rails

!SLIDE
# Rais as POEAA patterns
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
# Layering
## e.g., Presenters/Exhibits as layer between Model and View in MVC.
!NOTES
TODO: Discuss how layering, ultimatley what these tools offer  simplifies managing a complex problem but sometimes with the cost of cascading changes across multiple layers
TODO: Cascading changes are additional complexity

!SLIDE
# [Active Record](http://www.martinfowler.com/eaaCatalog/activeRecord.html)
    An object that wraps a row in a database table or view, encapsulates the database access, and adds domain logic on that data.
# -- POEAA

!SLIDE
### Any non-trivial Rails app contains either/both
### bloated ActiveRecord::Base subclasses 
### and
### non-ActiveRecord domain model classes

!SLIDE
### Vox populi
# persistence and domain logic 
# should not coexist in a Rails app

!SLIDE
# Are we doing it wrong?
    If the [database table to domain model] mapping is simple, [the] Active Record [pattern] does the ... job without an additional layer of code. If the mapping is complex, [the] Data Mapper [pattern] works better, as it's better at decoupling the data structure from the domain objects because the domain objects don't need to know the layout of the database.
-- Martin Fowler, POEAA

!SLIDE
# "If the mapping is complex,
# Data Mapper works better..."

!SLIDE top-left
# Possible Solution: Data Mapper
}}} images/data_mapper.png

!SLIDE
# Clear separation between
## source
## mapping
## model

!SLIDE
# What's keeping us?

!SLIDE
# Can we use ActiveRecord as a Data Mapper?

!SLIDE
# [Repository pattern](http://martinfowler.com/eaaCatalog/repository.html)
## well... sort of

!SLIDE
# [edr](http://github.com/nulogy/edr)
# &nbsp;
###### See [Building Rich Domain Models in Rails. Separating Persistence.](http://engineering.nulogy.com/posts/building-rich-domain-models-in-rails-separating-persistence)

!SLIDE
}}} images/lipstick_on_a_pig.jpg::DailySaving::::http://daily-saving.blogspot.com/2010/11/dont-fall-for-lipstick-on-pig-its-still.html

!SLIDE
# ActiveRecord is *not* a pig

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

!SLIDE
# Domain Model to ActiveRecord
# &nbsp;
@@@ ruby
Edr::Registry.define do
  map Order, OrderData
  map Item, ItemData
end
@@@

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
# [DataMapper](http://datamapper.org) is not a true [Data Mapper](http://martinfowler.com/eaaCatalog/dataMapper.html)

!SLIDE
# [DataMapper 2](https://github.com/datamapper) is still WIP
# &nbsp;
###### For instance, DM2 doesn't yet have an official [Unit of Work](http://martinfowler.com/eaaCatalog/unitOfWork.html) implementation





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
