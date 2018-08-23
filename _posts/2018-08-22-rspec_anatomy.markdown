---
layout: post
title:      "RSpec Anatomy"
date:       2018-08-23 01:07:58 +0000
permalink:  rspec_anatomy
---

![](https://i.imgur.com/hQWfRbt.png)

I'm currently looking into test-driven development (TDD) in Rails. It's been a while since I worked with RSpec, so these are some notes to refamiliarize myself with testing.

In this example, I'm testing an imaginary `Car` class in Ruby. `Car` has a class method `.colors`, which returns an array of colors `['red', 'black', 'green', 'blue']`.

**RSpec Hierarchy**

* spec file – `car_spec.rb`
* example group – `describe` keyword
* nested group – `describe`/`context`
* example – `it`
* expectations – `expect().to()`

**The `describe` Keyword**

`describe` is an RSpec keyword. It is used to describe an *example group*, i.e. a class name and/or a string. You pass a block argument to `describe`, which will contain the individual tests.

```
describe 'Car' do
   #examples
end
```

**The `context` Keyword**

`context` is similar to `describe`. It accepts a class name and/or a string. The idea of `context` is that it encloses tests of a certain type. 

**The ` it` Keyword**

it is used to define an example. With it, it's common to pass a string and a block argument. 

```
describe 'Car' do 
   it "has a reading for number of wheels" do
	    #expectations
	 end
end
```

**The `expect` Keyword**

`expect` is used to define an expectation. This is where we verify that a specific condition has been met. The `to` keyword (as well as `not_to`) is part of an `expect` statement.

```
expect().to()
expect().not_to()
```

An example of a spec testing the `.colors` method in our `Car` class might look like this:

```
describe 'Car' do
   describe '.colors' do
	    it "returns an array of colors" do
			   c = ['red', 'black', 'green', 'blue']
				 expect(Car.colors).to match_array(c)
			end 
	 end
end
```

**Links:**

[RSpec Docs](http://rspec.info/)












