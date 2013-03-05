
!SLIDE middle
# Evan Light
## **<u>Freelance Code Janitor</u>**
## [@elight](http://twitter.com/elight)
## [evan.light@tripledogdare.net](mailto:evan.light@tripledogdare.net)

!SLIDE 
    I have a set of alarm bells that go off when people say, "Always do this".
-- Martin Fowler, POEAA

!SLIDE
# Why?
!NOTES
* Prematurely optimizing around Rails
* Purists wanting one and only one way to solve any given problem in a Rails app
* "Use Rails Until it Hurts"
* Instead of using every flavor-du-jour gem/technique...
* ... use plain ol' Rails up until it causes you pain
* **THEN** choose a pattern/tool or two to use when you leave the golden path
* Purists tend to be more experienced developers
* How should more experienced Rails developers accomodate everyone else?

!SLIDE top-left
}}} images/jarjar.jpg
# If it bleeds...

!SLIDE bottom-right
}}} images/jarjar.jpg
# ... it leads

!SLIDE middle
}}} images/stuff_i_do.png

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
# Name practices

!SLIDE
# Pattern ends here

!SLIDE
# But then we automate what we can predict

!SLIDE
# Step 3
# Partially implement pattern as tools
!NOTES
* Tools encode knowledge
* Reduces number of choices required by a pattern user

!SLIDE
# Step 4
# Best practices for tools
!NOTES
* Further reduce number of choices of a pattern user
* Managing the "paradox of choice"

!SLIDE
# Step 5
# Identify holes in tools
!NOTES
* "Frustration Driven Development"
* Pain tells us that we need additional change

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
## Active Record
## Model View Controller
## Front Controller
## Template View

!SLIDE
# Post-Rails Rails Patterns
## [Presenter](http://blog.jayfields.com/2007/03/rails-presenter-pattern.html) ([gem](https://github.com/jcasimir/draper))
## [Exhibit](http://objectsonrails.com/) ([gem](https://github.com/objects-on-rails/display-case))
## [Form Objects](http://pivotallabs.com/form-backing-objects-for-fun-and-profit/) ([gem](https://github.com/ClearFit/redtape))
## [Policy Objects](https://github.com/bitlove/objectify)
## [DCI](http://dci-in-ruby.info/)
## [Service Object](http://jamesgolick.com/2010/3/14/crazy-heretical-and-awesome-the-way-i-write-rails-apps.html) ([gem](https://github.com/bitlove/objectify)

!SLIDE
# Layering
## e.g., Presenters/Exhibits as layer between Model and View in MVC.
!NOTES
TODO: Discuss how layering, ultimatley what these tools offer  simplifies managing a complex problem but sometimes with the cost of cascading changes across multiple layers
TODO: Cascading changes are additional complexity

!SLIDE


!
!SLIDE
# [Active Record](http://www.martinfowler.com/eaaCatalog/activeRecord.html)
    An object that wraps a row in a database table or view, encapsulates the database access, and adds domain logic on that data.

!SLIDE
# Hypothesis
## Any non-trivial Rails contains either bloated ActiveRecord::Base subclasses or non-ActiveRecord domain model classes

!SLIDE
# The Popular thinking: persistence and domain logic should not coexist in a Rails app due to model bloat

!SLIDE
# Are we doing it wrong?
    If the \[database table to domain model\] mapping is simple, Active Record (160) does the same job without an additional layer of code. If the mapping is complex, Data Mapper (165) works better, as it's better at decoupling the data structure from the domain objects
-- Martin Fowler, POEAA

!SLIDE
# Possible Solution: Data Mapper

!SLIDE
# Clear separation between data source, data mapping, and domain model

!SLIDE
# What's keeping us?
## [DataMapper](http://datamapper.org) is not a true [Data Mapper](http://martinfowler.com/eaaCatalog/dataMapper.html)
## [DataMapper 2](https://github.com/datamapper) is still WIP
## For instance, DM2 doesn't have an official [Unit of Work](http://martinfowler.com/eaaCatalog/unitOfWork.html) (application-level notion of transaction) impl.
!NOTES



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






!SLIDE
# NEOPHILIA
# &nbsp;
# &nbsp;

!SLIDE
# NEOPHILIA
## noun \nē-ə-ˈfi-lē-ə\
## love of or enthusiasm for what is new or novel
###### [Source: Merriam-Webster](http://www.merriam-webster.com/dictionary/neophilia)


!SLIDE
# Sources
## Martin Fowler, [Patterns of Enterprise Application Architecture](http://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420)
