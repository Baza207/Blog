---
layout: post
title: Swift, Optionals and nil
author: James Barrow
date: 2014-06-07
tags:
- apple
- languages
- nil
- optionals
- swift
- tutorial
image: swift-logo.jpg
---

Optionals are something that I had never heard of before Swift came out. I have coded in quite a few languages, but as far as I'm aware, I hadn't come across this thing. But it seems to be everywhere in Swift, so what is it? It took me a little while to sit down and work that out, but I now feel like I've wrapped my head around it.

`nil` is something I use on a daily basis, but it's not the same in Swift. It looks like it is, but under the hood, it really isn't. Below I'm going to talk about how Swift deals with optionals, this new way of thinking of `nil` and why I've come to realise and really love this new way of looking at things.

READMORE

In Obj-C if we create a variable, let's say its an NSString, we'd create it with something like the following:

```swift
NSString myString = nil;
/* some code */
myString = @"Hello World";
```

This string has no value on creation, so we set it, or should I say the pointer, to `nil` then somewhere else we set it to the string `Hello World`. This is something I use every day in lots of different places.

So in Swift you could assume that we would write the following:

```swift
var myString: String = nil
```

This will produce a compile error before we even got to trying to assign anything to our variable later on. Why? Well a variable in Swift can not be set to `nil` as `nil` is not the same thing. But we'll come back to that in a second.

So to make this work we need to make myString into an optional. For this the syntax is very simple addition of a question mark `?` after the type declaration.

```swift
var myString: String? = nil
/* some code */
myString = "Hello World"
```

Now we get no compile time errors and we can then go and set our variable to "Hello World" somewhere else in our code.

So why? Why would we want to have the ability to not be able to set a variable to `nil` and to have to add an extra character to make it even compile?

Well we have to look at how the two languages treat `nil`. To quote from the iBook that Apple realised "The Swift Programming Guide",

> In Objective-C, `nil` is a pointer to a non-existant object. In Swift `nil` is not a pointer - it is the absence of a value of a certain type.

The important bit to note here is that `nil` in Swift is nothing to do with a pointer, it's the absence of a value altogether. If you were able to set `nil` to any variable at any time, you would have the ability to call something on `nil` which would crash your code instantly. So to fix that we have optionals, which make everything safe.

If a variable can't be set as `nil`, then you always know if you call something on it, it won't crash!

I just said that if you have a variable you can set to `nil` then you could call something on it and cause a crash. So couldn't we just call something on an optional, and so crash out code in the same way. Well Swift has already though of that for us. To be able to access an optional you have to check it contains a value before you use it, otherwise we get a compile time error.

This means calling something like the following will not compile:

```swift
var myCar: Car? = nil
myCar.fillTank()
```

To fix this we can wrap it in an if statement that checks to see if `myCar` has a value assigned to it.

```swift
var myCar: Car? = nil
if myCar != nil {
  myCar!.fillTank()
}
```

This is great but what's the exclamation mark `!` Optional variables wrap up their values, which means when we want to access them again we have to unwrap them. That's what the exclamation mark `!` is doing, it's telling the compiler, "Please unwrap this variable. I would like to use it." and the compiler unwraps the variable and passes it back. This is fine in our 1 line example here, but what happens when you want to do a lot of things on myCar? Even 10 lines of code, having to type `!` to unwrap a variable every time would get a little annoying. And we know, from the way Swift can imply types and other places, that Swift was built with inference in mind. So what about trying this?

```swift
var myCar: Car? = nil
if let car = myCar {
  car.fillTank()
}
```

Here we've managed to do a few things, we've created a new constant reference of `myCar` called `car`, we've done this in the logic of the if statement and we no longer have to unwrap anything. Swift and the compiler is cleaver (if you hadn't already picked that up), it knows that we've created a constant `car` and assigned `myCar` to it. But we've done it in an if statement, so it knows it's being requested to check if `car` actually gets populated with a value. It automatically unwraps `myCar`, and if it finds a value, sets it to `car` and goes into the statements scope. If it finds nothing, it just continues. This allows us to have a unwrapped version of `myCar` in `car`, so anything we want to perform, we can perform on car within the scope of the if statement. ARC being awesome as well, as soon as we leave that scope `car` is cleaned up and we can carry on using `myCar`.

But, to use a phase I've heard a lot watching the WWDC session videos on Swift, "we can do better". This is still 3 lines of code, to check and call the function on `myCar` if it doesn't contain `nil`. Wouldn't it be amazing if we could do this in 1 line?

```swift
var myCar: Car? = nil
myCar?.fillTank()
```

What's happening here now? Well, we're taking our instance of `myCar`, then we have a question mark `?` and then we try to `fillTank()`. In this case the question mark `?` is not telling us we want to use an optional, as we did that in the declaration. Here we're using it to check `myCar` has an actual value. You can think of us actually using it to ask a question. "Does `myCar` exist?" If it doesn't, our code breaks out and continues on its merry way. If it does have a value assigned to it, it calls the next item in the chain and so on. This is called _optional chaining_.

These are of course simple examples, and as such it doesn't look that impressive. Ok, let's make something a little bit bigger. Imagine we have a garage, that garage has customer who in turn has a car. A car has a thing that need to be done on it and each thing is either complete or it isn't. In code we might represent this with `Garage`, `Customer`, `Car` and `Task` objects. Where a task has a `Bool` that represents if the task is compete or not. Now if we were to set this in code with if statements it'd look like this.

```swift
var myGarage: Garage? = Garage()
if let garage = myGarage {
  if let customer = garage.customer {
    if let car = customer.car {
      if let task = car.task {
        task.completed = true
      }
    }
  }
}
```

What a MESS! Yes, this will compile and run, and if a car doesn't actually have any tasks, then it won't go into try to set `true` to `nil` and the code will carry on its way. But that's 3 nested if statements spanning 9 Ïlines of code! Not exactly concise. Let's do that again with optional chaining.

```swift
var myGarage: Garage? = Garage()
myGarage?.customer?.car?.task?.completed = true
```

1 line. And this compiles, and will work in the exact way the nested if statement did. And actually, that's not even a very complicated example, but I hope now you can see the point and how powerful this feature can be.

Swift is a language that wants to help you, and it does. We can make things that could before time multiple lines of code, work in just a few, if not one. It's reasons like this that are making me love Swift, and I can't wait until later this year when it gets released to the world and I can start writing full apps in it.

If you haven't downloaded the book "The Swift Programming Language" from the iBooks store, you really should. That along with the Apple documentation and WWDC sessions are all great places to find more information about Swift.

For any of the sessions from WWDC 2014 find them at: <a herf="https://developer.apple.com/videos/wwdc/2014/" target="_blank">developer.apple.com/videos/wwdc/2014/</a>

Also check out the excellent book that Apple released that goes though the Swift language in a lot of detail: <a herf="https://itunes.apple.com/se/book/swift-programming-language/id881256329?l=en&amp;mt=11 target="_blank">Swift Programming Language</a>
