---
layout: post
title: "Writing Great Scientific Code"
date: 2016-10-12
categories: code
---

# Introduction
As a graduate student in computational neuroscience and machine
learning, I spend quite a bit of time coding. Naturally, I want to produce
valid code as fast as possible. While the desire to produce code quickly leads
many scientists to produce spaghetti code, I have found that using good
software engineering processes has dramatically increased my productivity. If
you are to take away one thing from this post, it is as follows:

Deliberately designing code that is easy to read and test pays huge dividends.

# What are the benefits of writing great code?

- *Well-written code is easy to read and understand quickly, saving time in the
  long run*: Somebody will have to read parts of your code eventually. Better
  written code will be easier to read and understand. This is especially
  important in science because the person reading your code is most likely
  going to be future-you who doesn't remember what current-you was thinking.
  Do yourself a favor and write good code now to save you huge amounts of time
  in the future.

- *Well-written code is easier to modify substantially*: One of the hallmarks
  of scientific coding is that you are likely to know little about the final
  form of your analysis. The majority of your work is identifying what your
  code is going to do and you can only do that by testing different ideas. This
  is in contrast to more typical software engineering situations where the
  functionality of the code is better defined at the start. Given the high
  variability of your code, you should be coding in a way that allows for large
  changes to be made easily. It is often the case that making large changes to
  a codebase incurs a certain type of psychological barrier. It is intimidating
  to dive into some code and make many changes that won't be testable until all
  of them are made.  When you write great code, changes that seem large in a
  messy codebase will be feel smaller in a well-written codebase.

- *The code is easier to validate*: A key goal of a scientist is to create
  validated knowledge about the world. The better that you write your code, the
  easier it will be to be confident that you correctly implemented what you
  said you did.


# High-impact habits for writing great scientific code

- *Write informative descriptions for all of your functions.* For every
  function that you write, write an associated description of that function
  that defines: what the function does in one sentence, a description of the
  parameters and a description of what the function returns. For each parameter
  and return value, give the type of that object. In the case of numerical
  computing, I've found it to be extremely useful to give the shape of all the
  the relevant matrices in each description of the object. When you go back to
  the code in the future to make changes, you will find that your documentation
  will save you huge amounts of time.

- *Use pure functions as much as possible.* A pure function satisfies the
  following:
  - The function always gives the same result given the same argument values.
    (eg. doesn't depend on global variables.)
  - The function doesn't create any side effects (like changing global
    variables, or mutating the inputs)

  The key benefit of using pure functions is that it makes your code easy to
  reason through and test because all of the dependencies of that piece of code
  are localized.

- *Use the 'Extract Method' refactoring pattern.* Going hand in hand with using
  pure functions as much as possible, the best way to create pure functions is
  the 'Extract Method' refactoring pattern. For instance, I have code that
  simulates the eye viewing an image. In the early version of my code, I did
  all of the relevant initializations in one long code block. This code was
  hard to reason through and change because there all of the initializations
  were unnecessarily entangled.   Fortunately, this initialization code can be
  broken down into multiple, relatively independent parts. For instance, this
  mass of code got replaced with two functions, one to initialize the eye and
  one to initialize the image. In this way, I took a mess of code and extracted
  methods that were simpler to reason about. Likewise, in your code, you'll
  find that you can reduce the complexity of your code by breaking large code
  blocks into simpler methods.

- *Use the 'Create Abstract Class / Interface' refactoring pattern.* In my
  code, I load in a variety of different types of eye traces that get put into
  my simulation (eg. various simulated eye traces and eye traces from real
  eyes). An easy way that I simplify my code is that I created a common
  interface that any piece of code that loads eye traces satisfies. The rest of
  the code expects the data loader to output data in a certain format. Thus
  when I want to load in different data, I just write a function that loads the
  data in a way that the rest of the code is expecting, and I don't need to
  worry about modifying the larger code base. More generally, a key of great
  coding is to identify repetition of logic in your code and write an
  abstraction that encapsulates that logic.


- *Test your code: use a unit-testing framework.* Whenever you write a complex
  piece of code, it will inevitably need to be debugged. As humans, we have a
  limited amount of complexity that we can handle. Thus the best way to build
  complex code is to decompose the task into simpler parts that will be
  assembled later. This way, you can assure that each smaller part is reliable
  and when you are putting these parts together, you know that the errors are
  coming from the connections between the parts and not the parts themselves.
  Programmers create frameworks that allow you to efficiently test a large body
  of code. For python users, I recommend using `py.test`. The main idea is that
  for each part of your code, you write tests to verify that they work
  correctly. By running a unit-testing framework, you collect all of these
  tests and run them. Furthermore, suppose that you are in the situation where
  you want to change one of the smaller parts of your code. Without unit tests,
  if you wanted to verify that those changes worked, you need to run your
  complex set of code. This is going to be extremely slow. Instead, if you have
  unit tests, you can know that your changes to the smaller pieces of your code
  work before seeing how those changes impact the larger codebase.

- *Use code linters that check for style.* A code linter is a tool that goes
  through your code and verifies that it satisfies a set of rules. Many
  languages have a community dedicated to writing code well. These people
  create packages that automatically check your code for style. The stylistic
  choices adopted by your coding community help you avoid common pitfalls in
  coding in your language and help others read your code. If you are a python
  user, check out pyflakes, pylint, and pep8. While the suggestions from these
  code linters can seem excessively pedantic, for the most part, they will help
  you improve your code quality dramatically.


- *Use version control!* (actually practice reverting a change to your code).
  Unless you are an amazing coder, it is likely that changes to your code are
  going to need lots of debugging. If you are in the unfortunate situation of
  not being able to track-down a bug in your code, you can back-track and
  figure out what changes broke your code if you use version control.
  Furthermore, version control lowers the psychological barrier to making
  changes to your code. If you know that you can undo any changes, it is much
  easier to get in there and make changes.

- *Don't leave code half-finished* When you make changes to code, you keep a
  mental tab of what changes were made. If you get up before the code is
  working, you lose track of the changes that you made after the most recent
  valid version of the code. Likewise, if you are using an interactive
  programming style (such as an jupyter notebook), it is essential to make sure
  that the code runs from start to finish without any errors. Thus when you
  come back to your code in the future, you are starting from code that works.
  If you are feeling like you cannot possibly make the changes to your code in
  one sitting, you should thinking carefully about decomposing your change into
  smaller tasks that can be finished in one sitting without breaking the code.

# Conclusions

All improvement starts with developing great habits to replace
lackluster habits. In order to feel better about your code and to be more
productive, I recommend taking one code habit and practicing it regularly. The
more effort that you spend on writing great code, the more that you will enjoy
writing code and the more that you will accomplish.


# Additional Comments

- Technical debt: You aren't always going to write amazing code. Sometimes it
  is more efficient to write poor code now in order to meet a deadline or to
  explore your ideas quickly. In software engineering, there is a concept
  called techincal debt. The idea is that writing poor code now incurs debt
  that needs to be paid off in the future. Thus the habits in this article
  shouldn't be taken as rules that should never be broken. Instead, you should
  simply understand that when you break one of these habits, you will most
  likely need to spend time in the future to fix the mess that you created now.

- For more information on refactoring, check out 'Refactoring Improving the
  Design of Existing Code' by Martin Fowler.

- Many computational scientists will end up working in industry. You greatly
  improve your marketability by demonstrating that you know how to write great
  code.

- Further reading:
  - Python style guide: [pep8].
  - Book on refactoring: [refactoring].
  - Python testing framework: [py.test].

[pep8]: https://www.python.org/dev/peps/pep-0008/
[refactoring]: https://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672
[py.test]: http://doc.pytest.org/en/latest/
