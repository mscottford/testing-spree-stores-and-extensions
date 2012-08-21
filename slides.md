# testing-spree-store-and-extensions

!SLIDE title

# Testing Spree Stores and Extensions

## M. Scott Ford
Software Engineer<br/>
Cardagin Networks

!SLIDE

# About me

!NOTES

* Work at Cardagin
* Focus on testing there
* Prior to that, built Spree stores
* Writing software for 15 years
* First 5 no tests
* a project opened eyes to value of testing

!SLIDE

<img alt='x-31' class='full' src='images/x-31-smaller.jpg' />

!NOTES

* X-31 experimental fighter
* long history of X planes
* Each one built to explore a different aviation problem
* X-1: blah
* X-??: blah
* X-31: thrust vectoring
* What is thrust vectoring?
* Changing the direction of the exhaust to maneuver

!SLIDE

<video width="704" height="480" controls="controls">
  <source src="movies/EM-0036-05.mov" type="video/mp4" />
  Your browser does not support the video tag.
</video>

!SLIDE

<img alt='x-31' class='full' src='images/x-31-smaller.jpg' />

!NOTES

* Play video (it looks like this)
* My role on the project
* Worked on acceptance testing framework that verified whether
  or not plane safe was safe to fly.

!SLIDE

# If my code failed
# people could die

!NOTES

* <Pause>
* "No presure."

* The experience of testing on the X-31 impacted the way I approched
  software the rest of my career.

* Which brings us to our topic, testing.

!SLIDE left

# Structure of the talk

Four parts:

1. Why test?
2. Testing best practices
2. Testing Spree stores
3. Testing Spree extensions

!NOTES

* Here's how the next 57 minutes is going to go.
* First, I'm going to talk about testing:
  * If you're a developer: why you should bother.
  * If you're a store owner: why you should pay for it.

* Then, some specific examples of how to set up a Spree store
  for testing. And what a few different test types looks like.

* Finally, some specific examples of how to set up a Spree extension
  for testing. And what a few different test types look like.

* At the end of each section, there will be some time for questions.

!SLIDE title

# Why Test?

!NOTES

12 minutes

!SLIDE

## Why is Testing Important?

!NOTES

* Testing mitigates risk of a bug
* The amount of testing that testing that you do depends on how important
  your application is, and what is likely to happen if it failed.

!SLIDE

## Safety Critical vs. Mission Critical

!NOTES

* Remember how I said that if my code failed, people could die? That's a big risk. So we did a lot of testing.
* No one ever questions the value of testing a safety critical system.

Here are some examples of safety critical of safety critical applications

!SLIDE

### Safety Critical

If my code fails, people could die.

!SLIDE

### Safety Critical

#### Aircraft and Spacecraft

<img alt='rocket' src='images/rocket-smaller.jpg'/>

!NOTES

* When a rocket takes off, especially when it's manned, there's the potential for a fatality.

!SLIDE

### Safety Critical

#### Emergency Response Systems

<img alt='ambulance' src='images/ambulance.jpg'/>

!NOTES

* Emergency call center software.
  * In the US, this is 911.
  * In Ireland it's 999.

* A failure with that system, could result in a call going unanswered, sending someone to the wrong address, a ton of other potential issues, while someone is in critical need of medical care.

!SLIDE

### Safety Critical

#### Passenger Rail

<img alt='light rail' src='images/light-rail.jpg'/>

!NOTES

* If there's a bug in the software that controls the tracks, or in passing along instructions to drivers, a collision can result.

* All of these systems can fail in catastrophic ways, therefore all of these systems are thoroughly tested.

!SLIDE

### Mission Critical

If my code fails, business is impacted.

!NOTES

So what does that mean? Business can be impacted in many ways. The loss of property, the loss of money, the loss of customers, the loss of credibility, the list goes on.

The amount of testing that goes into a mission critical project, is directly related to the size of the potential impact that a failure would have.

!SLIDE

### Mission Critical

#### Mars Science Lab Landing

<img alt='mars rover landing' src='images/mars-rover.jpg'/>

!NOTES

How many people here followed the landing of the Mars rover? I watched it live, woke my wife up. She was pissed. :)

This gives us a good definition of safety critical vs. mission critical. Why the rocket was launching, that was a safety critical problem. If that launch had failed, there's the chance that people could die. People on ground nearby, could have crashed and hit someone's house, etc...

The landing on Mars was unmanned, and very, very far from Earth. No one was going to die if it crashed. However, a lot money and time went into producing a piece of technology that would be extremely difficult to replace.

Luckily, they pulled it off flawlessly, and I was cheering along, loudly, at 3am Eastern time. :)

So what are some other examples of mission critical projects.

!SLIDE

### Mission Critical

#### Stock Trading Software

<img alt='stock exchange' src='images/stock-exchange.jpg'/>

!NOTES

Recently a US company, Knight Capital Group, had a bug in their trading
software that cost them $440 million or €357 million.

That's a lot of money, and lot of negative press. This was mentioned on
news programs in the US for several days.

The business impact was huge. Probably immeasurable. I don't have insight
into the amount of testing that went into this particular software, but
given the amount of risk, I hope they tested it well.

!SLIDE

### Mission Critical

#### E-Commerce

<img alt='spree logo' src='images/spree-logo.jpg'/>

!NOTES

It's not hard to imagine an e-commerce site, that is the sole revenue generator for a business. Each minute the site is down, is money that the business is not making. The proportion of a company's revenue that is generated by the online store, is a good indicator for how well the site should be tested. For some, the e-commerce store isn't much more than a hobby, and if it happens to be down for a few days, not a big deal. For others, the tolerance for how long it can be down may be measured in minutes. This is a good way to measure a client's risk tolerance. The more risk a client is willing to tolerate, the less rigorous the testing needs to be.

!SLIDE

## Why Don't We Test More Often?

!NOTES

Here are some common reasons that I hear.

!SLIDE

## Why don't we test more often?

### "Testing is frustrating."

!NOTES

Testing is frustrating, because we are putting in work now, but we don't
often see the benefit until later. It's a lot like working out at the gym.
It's slow and painful, but healthy. And it's helps you go faster.

!SLIDE

## Why don't we test more often?

### "I don't see the benefit"

!NOTES

If you're not seeing failures, then having the tests in place is working. You usually don't have something tangible that you can point to.

!SLIDE

## Why don't we test more often?

### "I don't have time"

!NOTES

Early in my career, I said the same thing.

* Then if I encountered an issue, here's how I would have to fix it. Open the app. click a button, click another button, type in a field. Click another button. Did it work? Nope. Go back and look at the code. Make a change. Open the app. click a button again. and another again. type in the field again....

* I'm a lazy software developer. I despise repeating the same thing over again. When I moved to automated testing, I would write the test once, and then I could run it as many times as I needed.

!SLIDE left

# Why Test?

## Summary

* Why is Testing Important?
* Safety critical vs. Mission critical
* Why Don't We Test More Often?

!SLIDE

# Best Practices

!NOTES

There are a few generally accepted testing conventions and definitions.

!SLIDE

## Test First vs. Test Last

!NOTES

There are two schools of thought. In one, you write your tests first, and then they drive what code is written to make them pass. In the other, you write your code first, and then write the tests that you feel are needed to ensure it works.

So which of these is "right"?

From my point of view, it does not matter, as long as your tests don't succeed when they really should fail. For example, if you mean to test X, but accidentally test Y, then when X fails, your test for Y will still pass. That's an example of a false positive.

When following test driven development strictly, this is much less likely. A little more diligence is required when writing your tests after the fact.

Both ways of testing have merit. For me, it's less important how you're testing and more important that you are testing and that you are doing so accurately.

!SLIDE left

## Different Levels of Testing

These are the kinds of tests that this talk is going to cover

* Acceptance
* Integration
* Unit

!NOTES

Briefly define each one, and give a very brief example of when you use each one. And mention that the technical portion shows examples of these three for both store and extensions.

!SLIDE left

## Other Kinds of Tests

These tests are important, but we don’t have enough time to go into them here.

* Security
* Performance
* Exploratory

!NOTES

Briefly define each one, and give a very brief example of when you use each one.

!SLIDE left

## Properties of a Good Test

* Reads like a story (beginning, middle, and end)
* Easy to read and understand what’s being tested

!NOTES

Explain why with examples.

!SLIDE left

## Tool Choice

Cucumber vs. RSpec vs. Test::Unit vs. others

!NOTES

Cucumber is great, if a non-developer is going to actively participate in the test authoring process. It's best to limit cucumber to acceptance tests.

RSpec and Test::Unit are good tools for all three kinds, and make the most sense if the tests are only ever authored and read by developers. Since Spree is tested with RSpec, the examples in this presentation will use it as well.

There are many more testing frameworks that might be a good fit. If your team likes it. Keep using it. If your team doesn't then migrate away from it quickly.

!SLIDE left

## Tips for Consultants

* Don’t list testing as on giant line item in your estimate
* Don’t make testing optional
* Let your client's risk tolerance dictate how much you test

!NOTES

Explain why. With examples.

!SLIDE left

# Best Practices

## Summary

* Test first vs. test last
* Properties of a good test
* Different levels of testing
* Tool choice
* Tips for consultants

!NOTES

(1 minute)

!SLIDE

# Testing Spree Stores

http://github/mscottford/sample-store

!NOTES

12 minutes

!SLIDE left

# Getting Started

Create a new spree store project with RSpec and Capybara

http://github.com/mscottford/sample-store

branch: master

!SLIDE left

## Create a Rails App

@@@ bash
$ gem install rails -v 3.2.8
$ rails _3.2.8_ new sample-store --skip-test-unit
@@@


!SLIDE left

## Add Spree

@@@ bash
$ echo "gem 'spree', '~> 1.1.0'" >> Gemfile
$ bundle update
$ rails g spree:install
$ echo "/public/spree" >> .gitignore
@@@

!SLIDE left

## Add RSpec and Capybara

`Gemfile`:

@@@ ruby
group :test do
  gem 'rspec-rails'
  gem 'capybara'
  gem 'database_cleaner'
  gem 'factory_girl'
  gem 'faker'
end
@@@

!SLIDE left

## Add RSpec and Capybara

@@@ bash
$ bundle update
$ rails g rspec:install
@@@

!SLIDE left

## Configure RSpec

Add to `spec_helper.rb`, right before `RSpec.configure`:

@@@ ruby
require 'database_cleaner'
require 'spree/core/testing_support/factories'
require 'spree/core/testing_support/env'
require 'spree/core/testing_support/controller_requests'
require 'spree/core/url_helpers'
require 'paperclip/matchers'
@@@

!SLIDE left

## Configure RSpec

In `spec_helper.rb`, change:

@@@ ruby
config.use_transactional_fixtures = true
@@@

to:

@@@ ruby
config.use_transactional_fixtures = false
@@@

!SLIDE left

## Configure RSpec

In `spec_helper.rb` inside `RSpec.configure` block, add:

@@@ ruby
config.before(:each) do
  if example.metadata[:js]
    DatabaseCleaner.strategy = :truncation, {
      :except => [
        'spree_countries', 'spree_zones',
        'spree_zone_members', 'spree_states',
        'spree_roles' ]}
  else
    DatabaseCleaner.strategy = :transaction
  end
end
@@@

!SLIDE left

## Configure RSpec

In `spec_helper.rb` inside `RSpec.configure` block, add:

@@@ ruby
config.before(:each) do
  DatabaseCleaner.start
end

config.after(:each) do
  DatabaseCleaner.clean
end
@@@


!SLIDE left

## Configure RSpec

In `spec_helper.rb` inside `RSpec.configure` block, add:

@@@ ruby
config.include FactoryGirl::Syntax::Methods
config.include Spree::Core::UrlHelpers
config.include Spree::Core::TestingSupport::ControllerRequests
@@@

!SLIDE left

## A simple test to make sure it's working

`spec/requests/home_spec.rb`:

@@@ ruby
require 'spec_helper'

describe 'home' do
  it 'should load home page' do
    visit '/'
    page.should have_content('Home')
  end
end
@@@

@@@ shell
$ bundle exec rake db:test:prepare
$ be rspec
@@@

!SLIDE

## Writing an Acceptance Test

Example scenario: related products

!NOTES

Many store owners want products to be related with other products. Since
this feature is provided by an extension, it's a good idea to write a
simple test that makes sure that the extension is installed correctly.

This may seem like overkill, because related products is an official
extension, but the more extensions that you add to a project, the greater
the chance that one extension will interfere with another one. You won't
get much warning about that. It often just will stop working, leaving you
to try and figure out why. But if you have a test, then you'll have an
easier time tracking down when things went awry.

!SLIDE

## Demo

http://github.com/mscottford/sample-store

branch: acceptance-test

!SLIDE

## Writing an Integration Test

Example scenario: Adding a method to `Spree::Product`.

!SLIDE

## Demo

http://github.com/mscottford/sample-store

branch: integration-test

!SLIDE

## Writing a unit test

Example scenario: Adding a helper method

!SLIDE left

# Testing Spree Stores

## Summary

http://github.com/mscottford/sample-store

* Getting started - branch: master
* Acceptance test - branch: acceptance-test
* Integration test - branch: integration-test
* Unit test - branch: unit-test

!NOTES

(1 minute)

!SLIDE

# Testing Spree Extensions

http://github.com/mscottford/spree_sample_extension

!NOTES

(12 minutes)

!SLIDE left

## Getting Started

http://github.com/mscottford/spree_sample_extension

branch: master

@@@ shell
$ gem install spree_cmd
$ spree extension sample_extension
@@@

!SLIDE

## Writing an Acceptance Test

Scenario: Special Pricing

!SLIDE

## Demo

http://github.com/mscottford/spree_sample_extension

branch: acceptance-test

!SLIDE

## Writing an Integration Test

Scenario: Special pricing for select products

!SLIDE

## Demo

http://github.com/mscottford/spree_sample_extension

branch: integration-test

!SLIDE

## Writing a unit test

Scenario: TODO

!SLIDE left

# Testing Spree Extensions

## Summary

http://github.com/mscottford/spree_sample_extension

* Getting started - branch: master
* Acceptance test - branch: acceptance-test
* Integration test - branch: integration-test
* Unit test - branch: unit-test

!NOTES

(1 minute)

!SLIDE left

# Testing Spree Stores and Extensions

## Summary

* Why Test?
* Best Practices
* Testing Spree Stores
* Testing Spree Extensions

!NOTES

(1 minute)
Brief overview of what was covered

!SLIDE left

# Additional resources

* Read the Spree RSpec tests<br/>
  [http://github.com/spree/spree](http://github.com/spree/spree)
* Developing Spree Extension with TDD<br/>
  [http://nebulab.it/en/nebulog/developing-spree-extension-with-tdd](http://nebulab.it/en/nebulog/developing-spree-extension-with-tdd)

!NOTES

A great way to learn more about how to test your store and extensions is to look at how Spree is tested.

!SLIDE left

# Additional resources

* Presentation<br/>
  [http://github.com/mscottford/testing-spree-stores-and-extensions](http://github.com/mscottford/testing-spree-stores-and-extensions)
* Sample Store code<br/>
  [http://github.com/mscottford/sample-store](http://github.com/mscottford/sample-store)
* Sample Extension code<br/>
  [http://github.com/mscottford/spree_sample_extension](http://github.com/mscottford/spree_sample_extension)

!NOTES

(1 minute)

!SLIDE left

# Contact info

* email: scott@mscottford.com
* github: mscottford
* twitter: @mscottford
* blog: http://mscottford.com

!SLIDE

# Questions?

!NOTES

(6 minutes)
