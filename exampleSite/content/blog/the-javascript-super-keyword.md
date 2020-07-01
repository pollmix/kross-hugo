+++
date = 2020-06-30T18:00:00Z
description = "The super keyword is used to access and call functions on an object's parent."
image = "/images/ming-wei-lim-kfxlcfl5oe4-unsplash-min.jpg"
title = "The JavaScript super keyword"

+++
When we work with classes in JavaScript, it’s common to use the `super` keyword.

In this post I want to clarify what’s it useful for.

Suppose you have a class `Car`:

    class Car {
    
    }

and in this class we have a `constructor()` method:

    class Car {
      constructor() {
        console.log('This is a car')
      }
    }

The constructor method is special because it is executed when the class is instantiated:

    const myCar = new Car() //'This is a car'
    

You can have a `Tesla` class that extends the `Car` class:

    class Tesla extends Car {
    
    }
    

The `Tesla` class inherited all the methods and properties of `Car`, including the `constructor` method.

We can create an instance of the `Tesla` class, creating a new `myCar` object:

    const myCar = new Tesla()

And the original constructor in `Car` is still executed, because `Tesla` does not have one of its own.

We can override the `constructor()` method in the `Tesla` class:

    class Tesla extends Car {
      constructor() {
        console.log('This is a Tesla')
      }
    }

and

    const myCar = new Tesla()

will print `This is a Tesla`.

In the `constructor()` method we can also call `super()` to invoke the same method in the parent class:

    class Tesla extends Car {
      constructor() {
        super()
        console.log('This is a Tesla')
      }
    }

Calling

    const myCar = new Tesla()

will now execute 2 console logs. First the one defined in the Car class constructor, the second the one defined in the Tesla class constructor:

    'This is a car'
    'This is a Tesla'

Note that `super()` can only be called in the constructor, not in other methods.

And we can pass in any parameter, if the constructor accepts parameter