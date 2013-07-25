# Object Orientation: Classes, Instances, and Methods

## Overview
Linguists group spoken languages into categories. For example, French, Italian, and Spanish are all romance languages. Similarily, computer scientists group programming languages into categories. Ruby is an Object Oriented programming language. 

In computer science, an object is a collection of data and functionality that logical go together. Frequently objects represent real world things. For example if you created an object to represent yourself (a "me" object) it would have some identifying data such as name, height, and eye color. In computer science, these pieces of data are called attributes. Your "me" object would also have some functionality such as walk, talk, and daydream. In programming things objects do are called methods. Sometimes methods can produce output. A talk method might return words, for example. If you are having trouble remembering the difference between methods and attributes a general rule is: Methods are verbs, adjectives and nouns are attributes.

In programming we create new objects from classes. A class is an abstract idea, sort of like a very rough blueprint. Think about your "me" object again. You are an actual human being, not the abstract idea of a human being. In programming, we call the actual thing an object or an instance. The abstract idea is a class. The class Human specifies what attributes all humans have such as a height and a name. The instance has specific values for these attributes like "5.5 feet" and "Marsha". The class also specifies what individual Humans can do like walk and talk but the instances perform these actions.

Rubyists are fond of saying "in Ruby everything is an object". What that means is that every piece of data in a ruby is an instance of some class. Every piece of data in Ruby has both attributes and methods that can be interacted with. Also every method returns (outputs) an object of some kind or another.

A class is an abstract idea. It defines what all objects of that type can know and do. Think of the chair you’re sitting in. It’s not an abstract chair, it is an actual chair. We’d call this actual chair an instance - it is a realization of the idea chair. It has measurable attributes like height, color, weight. The class chair, on the other hand, has an abstract weight, color, and size – we can’t determine them ahead of time.

We'll start with something that *could* be a physical object, like a Product. First let's define a couple things.
<pre><code>
class Product
  def name
    "Fleece Wolf Blanket"
  end  
  def weight_in_ounces
    12
  end
end
</code></pre>    

Here is a list of the Objects involved in this class:

- Product (Class)
- Product.new (returns an instance of the product class)
- Product.new.name => "Fleece Wolf Blanket" (String, ALL ruby classes are objects)
- Product.new.weight_in_ounces => 12 (Integer)

The things that are not Objects are 

- `def`
- `end`
- The actual method name (i.e. `weight_in_ounces`)

### Return Value
When we say that "every method returns an object", we bring up a very important concept. 

Executing code is transactional, meaning that we give the computer code to execute, and the computer gives us a response. The response the computer gives is ALWAYS an object. Methods can be separated by `.`, which just tells the computer to execute the next word on the object that the last word returned. 

Let's imagine that the computer is a person and we're asking them to process this request for us.

    product = Product.new
    product.name
    product.name.reverse.upcase
    product.destroy
    
Us: Hey Computer.  

Compi: Yeah?

Us: We need your help.

Compi: Awesome, I love to help.

Us: Great, pretty simple: let's start with `product = Product.new`

Compi: Oh that's easy. `Product.new` tells me you want a new instance of a product like `#<Product:0x000001009ea6c8>`. I'll go ahead and remember that as the variable `product` in case you wanna use it later.
  
Us: Thanks, I actually wanna use it now. How about `product.name`.

Compi: Ok, so `product` returns that instance of `Product` - here you go: `#<Product:0x000001009ea6c8>`. 
  
Let's see, next you want `name`, ok, just to be clear, I am giving you the name of `#<Product:0x000001009ea6c8>`, not `Product`. 
  
Checking, checking. Okay, got it. It's `"Fleece Wolf Blanket"`. So there you go: `"Fleece Wolf Blanket"`.
  
Us: Perfect again! Next is gonna be a bit trickier, how about `product.name.reverse.upcase`?

Compi: No problem. You gave me `product` so I'll give you `#<Product:0x000001009ea6c8>`.

Next is `name`. I'll give you `"Fleece Wolf Blanket"`. 

Let's see, is there anything you wanted me to do with `"Fleece Wolf Blanket"`? 

Oh right, `reverse`. That's `"teknalB floW eceelF"`. 

And finally `upcase`! Since that's the last method, I'll go ahead and finally return `"TEKNALB FLOW ECEELF"` for you to do what you'd like with.

Us: Totally spot on. Nice work, Compi! Next I want to `product.destroy`.

Compi: Alright, so `product` again returns `#<Product:0x000001009ea6c8>`. Next is `destroy`. Oh I didn't realize you we're gonna destroy that nice product I spent so little time creating. But ok. 

Just to let you know, I've executed your request, but there isn't much I can return, since it's gone and all. I'm just gonna give you `nil`. This is an object, but you can't do much with it. I wouldn't recommend trying to call any more methods on it.

In this example, for every word we type, the computer is returning an object. In the case of `product.name.reverse.upcase`, the computer is given four methods and is returning four objects. Even though we will only see the final result that `upcase` gives us, the computer is computing the first three methods all the same. So according the computer, this is what happened

- Receives `product`, returns `<Product @name>`
- Receives `<Product @name>`.name, returns `"Fleece Wolf Blanket"`
- Receives `"Fleece Wolf Blanket".reverse`, returns `"teknalB floW eceelF"`
- Receives `"teknalB floW eceelF"`.upcase, returns `"TEKNALB FLOW ECEELF"`

The computer handles things one word at a time.

## Lesson: Personal Chef
To get a better understanding of objects and their attributes and methods, we'll walk through section 4 of [JumpStart Lab's Ruby in 100 Minutes](http://tutorials.jumpstartlab.com/projects/ruby_in_100_minutes.html#4.-objects,-attributes,-and-methods). 

* This lesson combines a script file and IRB. You can load files in IRB by using the `load` command. You can then dynamically interact with the code you defined in the file. 

* Make sure that `personal_chef.rb` is in a `classroom_projects` folder (which should be a git repo). Push your files to GitHub at the end of the lesson.

From this exercise, you should now understand:  

* Classes and instances
* Methods
* Method parameters
* Return values

## Frequently-Used Objects
In the last section, we said *everything is an object*. This is a confusing concept at first, but let's go over a couple of examples to highlight that point.

We're already familiar with strings and integers. Strings and integers are objects, too! Try `"hello".class` in IRB. What do you get? 

Just like our PersonalChef class, which defined the abstract idea of a personal chef, there's a String class that defines the abstract idea of string. The same is true for `2.class` (Fixnum) and `2.3.class` (Float). 

Even classes have classes! Try `"hello.class.class"`!

Commonly-used classes have pre-defined methods baked in - that's how Ruby from the inside out. To see what methods are available on any object, just call `.methods`. Try it with `"hello".methods`. 

Just to go further down the rabbit hole, `"hello.methods"` is even an object, so you can call `.class` on it. Turns out that it is an Array (which is an object type we'll get to very soon). 

We can use Array's predefined methods on `"hello".methods`, like `.count`. `"hello".methods.count` will give us the number of methods you can call on any string. How many are there?

## Advanced Strings: Methods, Concatenation, and Interpolation
Let's walk through JumpStart Lab's [Ruby in 100 Minutes' section on Strings](http://tutorials.jumpstartlab.com/projects/ruby_in_100_minutes.html#5.-strings). Stop when you get to Section 6: Symbols.

Through this lesson, we'll be introduced to:  

* Common methods: `.length`, `.delete()`, `.gsub(x,y)`, `.split()`
* Extracting substrings with [x..y]
* Working with Strings and Variables
* Concatenation versus Interpolation

## Optional Lesson: More About Methods
Can't get enough methods? Check out Chapter 6 of Learn to Program. It'll go over some common (and not-so-common) methods for some of our favorite types of objects: integers and strings. 

## Homework  
* Work through Chapter 7 and Chapter 8 of Learn to Program on your own.
* Read Chapter 2 (stuff you know) and Chapter 3 (stuff you know, plus some new ideas) in Beginning Ruby. 

### Attributions
Overview (modified), Personal Chef, and Advanced Strings are from JumpStart Lab's [Ruby in 100 Minutes](http://tutorials.jumpstartlab.com/projects/ruby_in_100_minutes.html).
