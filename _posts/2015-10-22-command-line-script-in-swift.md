---
layout: post
title: Create a command line Script with Swift
excerpt: "Why using Ruby if we can use Swift? Learn how to develop a command line script using Swift"
modified: 2015-10-22
tags: [commandline, swift, reactivecocoa, carthage, reactive]
comments: true
image:
  feature: headers/sea_rocks.jpg
  credit: Simon Schmitt
sitemap   :
  priority : 0.5
  isfeatured : 0
---

When I first heard about Carthage I was quite surprissed about the fact that it was implemented on Swift. Most of the scripts I knew that were being used by the iOS community was written on Ruby, CocoaPods is a big example of that.

> If you want to know more about Carthage and why Swift you can watch this talk that Justin gave at Realm explaining Carthage, [Ruthlessly Simple 
Dependency Management 
with Carthage](https://realm.io/news/swift-dependency-management-with-carthage/). Questions at the end of the talk are quite good.

Ruby has tipically been used for scripting as a replacement of bash, it allows you to write your code using OOP, and connecting your script with other dependencies distributed via Bundler. If we analyze the advantages and disadvantages that it presents as a language used for scripting purposes:

### Ruby Scripts

**Advantages**

- You can use a lot of libraries distributed via Bundler.
- It's very easy to start working on a new *gem* thanks to a command line script, `bundle gem MyGem`
- The community is very focused in code quality and the importance of tests.
- You'll find great frameworks if you're planning to use Ruby for scripts like, [Thor](https://github.com/erikhuda/thor)

**Disadvantages**

- If you are an Objective-C/Swift developer you have to learn Ruby...
- It requires a having the proper Ruby version running on your machine.
- It also requires an initial setup that you'll most of the cases do following the README and using Bundler for dependencies.

I wondered, why not using Swift/Objective-C instead as Carthage did? At the end we've been using that language for building apps and natively it's possible, why are we constantly struggling with Ruby when we can use our environments where we are comfortable working? It presents cool advantages, in my opinion that makes it definitively a great alternative to the typical Ruby based scripts:

### Swift/Objecttive-C Scripts

**Advangates**

- You don't need an interpreter running to execute the script
- You can distribute it using `brew` or a `.pkg` file
- You can use Objective-C/Swift libraries you're used to work with *(e.g. Alamofire)*
- Compared to bash the language is more simple and we organize our script as we consider. Have very complex scripts perfectly organized on different components.
- It doesn't require to setup anything, just use the binary file and voila! :tada:

**Disadvantages**

- You don't hae a lot of libraries/tools to build command line scripts. [Carthage](https://github.com/Carthage/Carthage) is doing a great job here though. We'll see later some of their contributions.

> As soon as we start writing more and more scripts in Swift/Objective-C more libraries will come out in order to simplify tasks and make Swift a first class command line script language that every Swift/Objective-C developer will use for automatizing tasks.

Would you like to know how to do it? Follow the next steps and you'll learn all you need to build your first script.

## Building a Command Line Script with Swift

### Creating the project

The first we have to do is creating an **Cocoa Application**. The reason why we're not creating a **Command Line Tool** sript is because these projects don't allow frameworks which is not what we want. We can create a **Cocoa Application** that is actually a script and then *extract the binary from the compiled app**. After creating the OSX app we'll see s


![]({{site.url}}/images/posts/swift_script_setup.png)



## References

- [Carthage](https://github.com/Carthage/Carthage)
- [Carthage/Commandant](https://github.com/Carthage/Commandant)
- [Carthage/ReactiveTask](https://github.com/Carthage/ReactiveTask)
- [ReactiveCocoa/ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa)


#### DON'T FORGET 
- Asynchronous
