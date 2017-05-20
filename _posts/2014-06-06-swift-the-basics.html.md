---
layout: post
title: Swift, The Basics
author: James Barrow
date: 2014-06-06
tags:
- apple
- basics
- swift
- tutorial
image: swift-logo.jpg
---

There are some awesome things happening when you look at Swift as a basic language. Swift is not another language built off of C, it's a brand new language. This means that there are no performance or historical drawbacks to Swift, as it doesn't rely on an underling langue.

```swift
let name = "James"
var greeting = "Hello "
greeting += name
println("\(greeting)")
>> Hello James
```

So in this simple code snippet you can instantly see some differences compared to the normal Obj-C code you might be used to. For starters their aren't any semicolons `;`. You just don't need semicolons in Swift. You can use them if you want, but they're not required (unless in specific circumstances).

READMORE

### var and let

You might have also noticed that there are two different versions of string, `var` and `let`. A `var` is the representation of a variable and mutable, where as `let` is the representation of a constant and so immutable.

Put simply `let` can only have its value set when it is created. Where as `var` allows you to change the value after the item has been created. This can been seen in the code snippet above where we concatenated the `Hello` string to the `name` constant and assign it to the greeting variable.

Apple has gone to a lot of effort to make Swift a very safe language. This means that if you do something wrong, more often than not you will get a compile time error. Where as in Obj-C we could make these errors, compile and run and then get the app crashing and have to go back and find where we went wrong.

### Type Declaration

The other thing we have there is how we stated that the variables were strings... oh wait, we didn't. Swift is a type-inferance language. This means that `name` knows that it should be of the type `String` due to the fact we assign it a string. We can declare the type if we wanted to and then we'd get the following:

```swift
var myString: String = "Hello World"
```

### Types

Swift gives us the standard types that you would expect:

- `String`
- `Bool`
- `Int`
- `UInt`
- `Double`
- `Float`
- `Array`
- `Dictionary`

`String` and `Bool` are pretty self-explanatory, but `Int` and `UInt` might need a little more explanation. These work very much like NSInteger and NSUInteger, on a 32-bit systems they are `Int32` or `UInt32` and on 64-bit systems they are `Int64` or `UInt64` respectively. As you might have guessed from my explanation there, you can also define an integer in 8, 16, 32 and 64 bit forms. It's probably worth mentioning that Apple suggests that you use `Int`, even when you know you won't use any negatives values.

`Double` and `Float` are the 64-bit and 32-bit representations of floating point numbers respectively, and don't need much more or an explanation than that.

`Array` and `Dictionary` are created in a visually very similar way. They use square brackets `[]` to encapsulate the values and key-values.

```swift
var myArray = ["Hello", "Bonjour", "Hej"]
var myDictionary = ["Dog": 4, "Snake": 0, "Ant": 6]
```

Adding items to an `Array` is a simple as using `+=` and adding to a `Dictionary` is just adding the new key in `[]` and then assigning the value.

```swift
myArray += "Hallo"
myDictionary["Kangaroo"] = 2
```

And lastly retrieving values can be done by the follow:

```swift
let greeting = myArray[2]
println("\(greeting)")
>> Hej

let legs = myDictionary["Dog"]
println("\(legs)")
>> 4
```

These are simple and logical, but it's worth mentioning as it's useful to know how to do the simple things.

### If and Switch Statements

```swift
let inProcess = True
if inProcess == True {
	println("In Process")
}
```

There might be an obvious omission to if statements in Swift, you don't have to have parentheses `()`. Like the semicolon at the end of every line, you can continue to do so if you want to, but there's no real need.

```swift
let myNumber = 5
switch myNumber {
case 0:
  println("Zero")
case 1...10:
  println("Top ten!")
case 11..100:
  println("Eleven to ninety nine")
default:
  println("One hundred or more...")
}
```

Again there's an obvious omission to this switch statement, no break case at the end of every case. Again it's just one of those things you just don't need to do in Swift. Switches are actually amazingly powerful, you can pass in nearly any type of constant to case check against making they very adaptable to most circumstances.

In Obj-C I use switches a lot, due to looking up some speed tests once on if statements vs. switch in Obj-C. Switches won hands down, but the thing that annoyed me over the years is the fact they could get big and messy, fast. With not needing to add break in there anymore, that 1 line omission should help clean them up a lot, but that tied into the fact you can perform almost any logic in a case means I think I'll be using switches even more that I did before in Obj-C.

### ...and on and on...

I could go on here more and more but I have decided to leave it here. I don't want to write a detailed how to and why, as Apple has already done that very well in the "The Swift Programming Language" book they released on iBooks. So for more details and abilities of these features in Swift, I encourage you to take at the Apple documentation and references below. They go into so much more detail I could in this post, so go check them out.

Next time I'm going to go into a few of the features I've enjoyed and liked being added in Swift that weren't in Obj-C, and lets see if we can get a bit more focus in these posts.

For any of the sessions from WWDC 2014 find them at: <a herf="https://developer.apple.com/videos/wwdc/2014/" target="_blank">developer.apple.com/videos/wwdc/2014/</a>

Also check out the excellent book that Apple released that goes though the Swift language in a lot of detail: <a herf="https://itunes.apple.com/se/book/swift-programming-language/id881256329?l=en&amp;mt=11 target="_blank">Swift Programming Language</a>
