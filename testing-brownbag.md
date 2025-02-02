# Testing Brownbag

# Notes to cover

## It's About Understanding

Source this quote and get it exact: Steve McConnell or The Other Steve "When you
have a bug, you do not understand what the computer is actually doing."

Find Sandy's quote from POODR about "you can't maintain what you can't
understand".

## Audience

1. I'm using your gem/lib/app for its intended purpose. I don't care how it
   works, I just need to know that it DOES work. I want green dots. "I have
   installed your thing and I want to use your thing. Does it work on my
   machine?" See also: when we do `configure && make && make install` it's
   sometimes nice to run `bin/program_name --test` after the `make` but before
   the `make install`
1. I need to use your software library, mostly indirectly. I am building
   something that uses your software, but maybe without needing to look at your
   software. `rspec --format=documentation --order=defined`.
   * Author needs to write their describe/context/specify such that the -f d
     actually presents the d.
   * Good example: when you try to access my thing, but the network is down, it
     "raises an exception" or "it returns false". <-- Now you know that network
     failures are exploding network failures or polite network failures. This is
     a great place to tell the developer "if this sad path occurs, the
     appropriate behavior is to x." Maybe it's explode, like Model.find. Maybe
     it's return a polite failure, like Model.find_by. Or maybe the correct
     behavior is to succeed anyway: "When the cache is down, this method should
     calculate the value the hard/correct way, update the cache, and return the
     correct value." (Or for volatile data: "When the value is in the cache, but
     it was cached two days ago, this method should clear the cache, calculate
     the value, update the cache, return the correct value."
1. I am extending/modifying your code. I probably want -f d but I DEFINITELY
   want to READ your spec code. I want to see a StackOverflow example in your
   specify blocks.
1. I am debugging your code.
   * Robust error messages.
1. I am writing the code right now.  Something high-value today might be very
  low-value tomorrow. "Don't test private methods. Unless you want to. Then test
  them as much as you want." Sandy was pushing me to understand that if you're
  trying to lock down a difficult operation,

## Every Good Argument For Testing Private Methods Is An Even Better Argument
  For Extracting A Class, Making It A Public Method, and Testing The Method
  Publicly


## The Occluded Context: Overriding partial lets in nested contexts

Works well when the happy path is a BIG thing with a bunch of tiny things that
each independently affect the big thing. (This is also a good candidate for
shared_examples, e.g. when this value is x, the document should be valid, but
when this value is y, the document should be invalid.)


## TDD vs. Test-After

- Integration tests are suuuuper slow, but they cover everything... STOP: Test
  the thing and only the thing, and test it as close to the same level of
  abstraction as the thing. If you're up too high, you will not have the agility
  to drill into every code path. If you're down too low, you will not have the
  perspective to identify coupling points.

## Integration vs. Model vs. Unit

Test the thing and only the thing you are testing.

## I Don't Trust My Tests

Yup, it's a thing. This is a good motivation to increase your test coverage and
improve the readability and maintainability of your spec suit. Unfortunately
it's also the SAME motivation to slap low-value tests into the system.

### Errors Get Through

We had to revert because oops.

# ==========================

### We
