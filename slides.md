
!SLIDE middle
# Evan Light
# &nbsp;
# &nbsp;
# [@elight](http://twitter.com/elight)
# [http://tripledogdare.net](http://tripledogdare.net)
# [evan.light@tripledogdare.net](mailto:evan.light@tripledogdare.net)

!SLIDE middle
}}} images/stuff_i_do-16x9.png

!SLIDE
# Patterns of Enterprise Application Architecture
### by Martin Fowler
### &nbsp;
# [READ THIS BOOK](http://www.amazon.com/gp/product/0321127420/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0321127420&linkCode=as2&tag=hipphack-20)

!SLIDE
}}} images/all-the-things-16x9.jpg
!NOTES
# Response to this Rails backlash trend
# Almost anti-Rails
# Low coupling == good
# Loose coupling everything? Over-optimization.

!SLIDE
# Coupling?

!SLIDE
# Tight coupling example
## &nbsp;
@@@ ruby
class UserController
  def index
    @user = User.all
  end  
end  
@@@

!SLIDE
# (Hypberbolized) Loose coupling example
## &nbsp;
@@@ ruby
class UserController
  cattr _accessor :finder

  def index
    @user = finder.all
  end
end
	
# ... in a config initializer or similar
UserController.finder = User
@@@


!SLIDE
# History lesson
!NOTES

!SLIDE top-left
# 1995
}}} images/java.jpg

!SLIDE top-left
# 1999 - Enterprise Java Beans
}}} images/russian-roulette.jpg

!SLIDE
# Enterprise Java Beans
> [a] managed server-side component architecture

> for module construction of ... applications

<cite>-- [Wikipedia](http://en.wikipedia.org/wiki/Enterprise_JavaBeans)</cite>

!SLIDE
# 2002
## Spring Framework

!SLIDE
# Spring Framework
> an open source application framework and

> inversion of control container for the Java platform

<cite>-- [Wikipedia](http://en.Wikipedia.org/wiki/Spring_Framework)</cite>

!SLIDE
# 2003ish
## Commoditization 


!SLIDE
# 2005ish
## Exodus

!SLIDE
# Predictors?
## Overabundance of choices / Inadequate curation
## Loose coupling fixation

!SLIDE
# Where is Ruby/Rails now?
!NOTES
# Some of our brightest are moving on
## Clojure
## JavaScript



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
# What about the remaining 20%?


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
# Living in a time of over-abundance

!SLIDE
> Choosing well is especially difficult

> for those of us determined to make 

> only the best choices

<cite>-- Barry Schwartz, [The Paradox of Choice](http://www.amazon.com/gp/product/0060005696/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0060005696&linkCode=as2&tag=hipphack-20)</cite>

!SLIDE
> We would be better off 
>
> if we embraced certain voluntary constraints
>
> on our freedom of choice, 
>
> instead of rebelling against them.

<cite>-- Barry Schwartz, The Paradox of Choice</cite>
!NOTES
# Inevitably, we're confronted with the results of poor choices
# But we accept expert-imposed constraints by using Rails


!SLIDE
# Available information > Reliable information
# &nbsp;
# Near source > Trusted source
!NOTES
# Schwartz cites studies


!SLIDE
# Vulnerable to effective advertising


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

!SLIDE
> Once you have something that grows faster than education grows, 
> 
> you're always going to get a pop culture.
 
<cite>-- [Alan Kay](http://queue.acm.org/detail.cfm?id=1039523)</cite>
!NOTES
# Pop culture is HIGHLY available
# Our culture lacks heavy commercial marketing
# But we market our OSS all of the time
## Blogs
## Conference talks


!SLIDE
# Our pop culture?

!SLIDE
## [Presenter](http://blog.jayfields.com/2007/03/rails-presenter-pattern.html) ([gem](https://github.com/drapergem/draper))
## [Exhibit](http://objectsonrails.com/) ([gem](https://github.com/objects-on-rails/display-case))
## [Form Object](http://pivotallabs.com/form-backing-objects-for-fun-and-profit/) ([gem](https://github.com/ClearFit/redtape))
## Policy Object ([gem](https://github.com/bitlove/objectify))
## [DCI](http://dci-in-ruby.info/) ([gem](https://github.com/saturnflyer/casting))
## [Service Object](http://jamesgolick.com/2010/3/14/crazy-heretical-and-awesome-the-way-i-write-rails-apps.html) ([gem](https://github.com/bitlove/objectify))

!SLIDE
}}} images/srbaker.png

!SLIDE bottom-right
}}} images/jarjar-16x9.jpg::mangaholix::::http://mangaholix.deviantart.com/art/Kriss-HATES-Jar-Jar-Binks-163018356
# "If it bleeds, it leads"

!SLIDE
# PATTERN, noun
## /ˈpatərn/
## A form or model proposed for imitation : exemplar.
##### [Source: Meriam-Webster](http://www.merriam-webster.com/dictionary/pattern)

!SLIDE
# The 6 Steps of Patterns

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
!NOTES
# Failings in our current practices lead us to new practices
# New practices lead to new patterns

!SLIDE
# Step 6
```
GOTO 1
```
<img src="images/troll.png" style="width: 600px; height: 600px; bottom: 100px; right: 300px; position: absolute"></img>

!SLIDE
# Rails is made of patterns!
## Template View
## Front Controller
## Application Controller
## Model View Controller
## Active Record 

!SLIDE
# Where did these come from?
## Presenter
## Exhibit
## Form Object
## Policy Object
## DCI
## Service Object


!SLIDE
# See Step 5: the failings of Rails

!SLIDE
# But...

!SLIDE
> Refactoring tends to break big objects into several smaller ones and big methods into several smaller ones.  

<cite>-- Fowler, Refactoring</cite>

!SLIDE
> Indirection is a two-edged sword... Every time you break one thing into two pieces, you have more things to manage. 

<cite>-- Fowler, Refactoring</cite>

!SLIDE
> [Indirection] can also make a program harder to read 

> as an object delegates to an object delegating to an object. 

> So you'd like to minimize indirection.

<cite>-- Fowler, Refactoring</cite>


!SLIDE
}}} images/bphogan.png

!SLIDE
}}} images/bones-16x9.jpg
!NOTES
# PLEASE BE CAREFUL
# Pop Culture Patterns are still bridging the cashm

!SLIDE
# [Active Record](http://www.martinfowler.com/eaaCatalog/activeRecord.html)
> An object that wraps a row in a database table or view, 

> encapsulates the database access, 

> and adds domain logic on that data.

<cite>-- Fowler, POEAA</cite>

!SLIDE
# Active Record
# &nbsp;
# ActiveRecord

!SLIDE bottom-left
# But prevailing wisdom says to do this
}}} images/tabledatagateway.png

!SLIDE
# There's a pattern for that!
#### &nbsp;
# [Table Data Gateway](http://martinfowler.com/eaaCatalog/tableDataGateway.html)
!NOTE
#ActiveRecord minus business logic

!SLIDE
# Active Record often isn't the best fit
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
# Simple?
# Complex?

!SLIDE
# Heuristic
<img src="images/troll.png" style="width: 600px; height: 600px; bottom: 100px; right: 300px; position: absolute"></img>


!SLIDE top-right
# Data Mapper
}}} images/data_mapper-16x9.png

!SLIDE
# Separation
!NOTES
# Source
# Mapper
# Model

!SLIDE top-left
}}} images/datamapper.jpg

!SLIDE
# [DataMapper](http://datamapper.org) is not a true [Data Mapper](http://martinfowler.com/eaaCatalog/dataMapper.html)
### &nbsp;

!SLIDE
# It's actually an Active Record

!SLIDE
# But can we use ActiveRecord as part of a Data Mapper?

!SLIDE
}}} images/yo_dawg_orm2-16x9.jpg

!SLIDE bottom-left
# [Repository](http://martinfowler.com/eaaCatalog/repository.html)
}}} images/repository_pattern-16x9.png

!SLIDE
# [edr](http://github.com/elight/edr)
## A step in the right direction
### ... sort of
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
  def add_item attrs
    repository.create_item self, attrs
  end
  
  # Business logic GOES HERE
end
@@@
!NOTES
# The above could be generated via reflection
# Domain Model could then just be a Domain Model
# maybe EDR::Model < ActiveRecord::Base
# In reality, it could reopen the EDR::Model subclass


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
# You probably don't want to try that at home

!SLIDE
# What if your models could look something like this?
# &nbsp;
```ruby
class Item
  include Virtus
  
  attribute :item_number,  String
 
  # biz logic here
end

class Order
  include Virtus 

  attribute :order_number, String
  attribute :items,        Array[Item]
  
  # here too
end
```

!SLIDE
# They can, if you DIY
```ruby
class OrderMapper
  def self.load(row_id)
    od = OrderData.find(row_id)
    order_from_order_data(od)
  end
  
  def self.dump(order)
    od = OrderData.find(order.id)
    attrs = order.attributes
    if od
      od.update_attributes(attrs)
    else
      OrderData.create!(attrs)
    end
  end
end
```

!SLIDE
}}} images/rom.jpg

!SLIDE
# [Ruby Object Mapper](https://github.com/rom-rb) 
# will be a ***true*** Data Mapper


!SLIDE
# [ROM](https://github.com/rom-rb) is always looking for contributors
# &nbsp;
### Contact [@dkubb](http://twitter.com/dkubb) or [@\_solnic\_](http://twitter.com/_solnic_)
### or dkubb or solnic on #rom-rb on freenode IRC


!SLIDE
# Rails is almost 10 years old

!SLIDE
# Rails apps are growing more complex
# We need more than an 80% framework


!SLIDE
# There are too many choices
# &nbsp;
# We need ***more*** curation

!SLIDE
# Doing my part:
## Look to ROM for the backend future

!SLIDE
# POEAA predates Rails
# &nbsp;
# Seek more answers within

!SLIDE middle
# THANKS!
