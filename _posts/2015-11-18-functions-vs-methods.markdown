---
title: Functions v/s Methods
date: 2015-11-18 22:40:06 -0600
layout: post
summary: Routine-level design very directly impacts the quality and complexity of code. The delineation between Functions and Methods can be helpful in structuring code and making things more readable.
tags: code-complete, functions, architecture
crosspost_to_medium: true
---

> Use a function if the primary purpose of the routine is to return the value indicated by the function name. Otherwise, use a procedure.

Routines come in two varieties: Functions and Procedures (or Methods, as they are referred to in the Cocoa world). This distinction is not just semantic but actually a great guideline while writing classes. The above "key point" from [Code Complete](http://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670/ref=tmm_pap_title_0?_encoding=UTF8&qid=&sr=) is a great heuristic. 

### Functions

> A function returns a value, and the function should be named for the value it returns.

Basically, functions should have no side-effects. A function takes in inputs, performs calculations and returns the value promised in the name. For example, `currentUserID`, `userIsLoggedIn`, etc. The idea of no side-effects is very important. Adhering to it simplifies the flow of control and one doesn't have to worry about things changing elsewhere just by calling a single function. There are a few sources of side effects to mind when designing a function.

`inout` parameters are sort of like passing pointers, as they have reference semantics. So, if we mutate an `inout` parameter in the body of the function, we are modifying the original variable at the call-site, which is effectively a side-effect.

```swift
func boundsOfView(view: UIView) -> CGRect {
	// view in an object passed as a reference and the compiler cannot 
	// check us from modifying its properties here, like:
	view.backgroundColor = UIColor.redColor()
}
```

For value types, Swift does the right thing and the parameters are declared as constants. In order to modify the parameter, it has to be explicitly marked as a `var`. In any case, the big problem is not with value types, but with reference types. A reference variables marked as `let` only means that the variable cannot be assigned to another instance. However, one can still modify the internal variables of the object which might have ripple effects across the program.

### Procedures (aka Methods)

Procedures, on the other hand, have side effects and return nothing. They operate on class data or perform operations like presenting or updating UI. In the object-oriented world, procedures abound. Still, we can do some things to minimize the complexity.

> To name a procedure, use a strong verb followed by an object.

Some good names: `loginWithEmail:password:`, `saveUser:`, `configureTableViewAppearance`, `refreshTweets`. 

[Cohesion](https://en.m.wikipedia.org/wiki/Cohesion_(computer_science)) is an important idea to keep in mind. Basically, (functional) cohesion implies that a unit of code concerns with only one task. All the operations in the unit are in service of accomplishing that task and nothing else. Keeping the scope of a method limited by performing only one task (at the level of abstraction chosen) is a good practice to promote readability and maintainability.

Procedures do not return any values but there are quite a few operations where we might need to report back success status or have a callback. In case of functions returning a success status, I have found Swift 2.0's error handling to be great!

```swift
func saveUser(user: User) -> Bool {
	// save operation
}
```

becomes...

```swift
func saveUser(user: User) throws {
	// save operation
}
```

This allows the method to stay true to the philosophy and also avoide the awkwardness where method name, like `updateUser:`, tells us nothing about the return type. On the other hand, a throwing function has to be marked as `try` at the call site, and we have to handle the corresponding errors. Very self documenting.

### Sidetrack

The simple distinction between functions and procedures is very helpful in understanding the primary ideological difference between functional and procedural programming. 

Functions do not modify things. They perform computations and return something new. Mutability and state are not a part of the the world. And that's the gist of functional programming.

Procedures handle state and modify objects. They can have far reaching (😱) side effects. This all stands well in the wheel house of procedural programming.

In any case, Swift is pretty fantastic as it allows us to choose which paradigm to work with. That's one of the reasons why it is considered so pragmatic. For GUI programming, functional programming makes very little sense (at least to me). While for data and other back-end operations, I find the functional approach to be very natural.

Best of both worlds!