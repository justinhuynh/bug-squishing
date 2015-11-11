# Bug Squishing
**Some thoughts on problem decomposition and debugging.**

## Introduction
Problem decomposition and debugging in Ruby are made more straightforward thanks to the very beautiful and developer-friendly syntax of the language, coupled with nice tools for inspecting issues during code execution [like Pry](http://pryrepl.org/). You may also find extensions to Pry like [Pry Nav](https://github.com/nixme/pry-nav) or [Pry Byebug](https://github.com/deivid-rodriguez/pry-byebug) useful for particularly thorny issues.

# Strategies for Problem Decomposition

## Make a Plan: Pseduo code and doodling FTW

Let's say I want to write a program to model a library. Rather than diving in and starting to write out a class definition of a `Book`, I should step back and first make a list of all the classes I'll need to model a library. Maybe I'll need books, shelves, categories, and patrons. Starting out with an idea of where you're going sounds like a basic step, but it's easy to think the problem is "straight forward" and begin coding, only to realize you aren't sure what you need or where to go next. Make a list of all your objects and take it from there.

Pseudo-coding is another good way to make a map of where you are going. Pseudo code is just writing the logical instructions you want the computer to follow, but in plain English. It's a good way to step through the functionality you want your methods to produce without needing to get in the weeds with implementation details in your language of choice right off the bat.

For example, let's say I'm writing a program that analyzes people's emails in order to make decisions about their communication style. I want to count the number of words in each email as one metric that assesses them on a scale from terse to verbose based on the average over time compared with other users. A first draft of the method to do that (in pseudo code) might look something like this:

```
initialize a counter for the number of emails analyzed
initialize a counter for the total number of words
get all the user's emails, go through each one
add the word count to the total number of words
increment the number of emails counter

divide the number of words total by the number of emails counter
```

Writing it out this way produces plenty of opportunities for re-factoring. I probably just realized that I could do this more efficiently by collecting the number of emails from the array or other data structure they are stored in (using `count` or `size` or `length`, etc). Pseudo code is a good way of nailing down what you want to achieve before you begin.

Finally, doodling is your friend, too! If you are a visual person, it can be helpful to draw a picture or diagram of what you are trying to do. Whiteboarding, doodling, etc are all good ways to get some tactile engagement with your planning process, and they are more amenable to visualization and easy modification.

## The test is your friend

A test is another great way to nail down what you are trying to do. If you know what objects you need, you can write tests to help you decide how they should behave or what their methods should produce.

Tests also give you more feedback about what's wrong. Consider this (slightly contrived) example in a file called `greeting.rb`:


```
class Greeting
  def hello_world
    "Hello World"
  end
end

puts hello_word

```

If we run `ruby greeting.rb`, we'll never see any output to our terminal. Yikes, why not? Well, because we've misspelled `hello_world` when calling it at the end of `greeting.rb`. A test would give us more information about this, even if we made the same mistake:

```
Rspec.describe Greeting do
  it 'should say hello world' do
    expect(greeting.hello_word).to eq("Hello World")
  end
end
```

Let's say I am trying to use this method and I can't figure out why it's never hitting the `do_a_thing` method. If some

NOTE TO SELF: RETURN TO THIS, IT DOESN"T MAKE SENSE YET LOLZ FOREVS


## Rubber Ducky, you're the one...you make debugging lots of f--well, less terrible

## The stack trace does not lie

!["Read the stack trace, Luke."](/images/luke.png)
!["A sad tip"](/images/sadtip.png)




## Beast-mode uses of Pry

Pry is your friend. The best piece of advice regarding use `pry` that I have is this: Throw a `binding.pry` on the line before things blow up. That line can be before the `expect` statement in the test, it can be on the line before you get an error in your ruby file, whatever, but put it in there.



## Google Fu

## Just write the damn code (Red, Green, Refactor)

## Asking for help online

## 


