# BEHIND THE SCENES

- javaScript:
1. high level
2. garbage-collected
3. interpreted
4. multi paradigm -> oop and funadmental programming # impretive and declaretive
5. prototypes based object oriented
6. first class functions # passing function into another
7. dynamic # data types of variables can be change automatically
8. single thread
9. non blocking event loop # event loop takes long running tasks, execute them in background and puts back them in the main when thay are finished

## JavaScript Engine

- all of browser have own javaScript engine
- engine has 2 part: call stack (where that code is executed, stack), heap (where objects are stored)
- at first convert to machine code then executed immediatly and also javascript at first create unoptimized version of machine code to execute faster and thene during the executing optimized it more and more

- we can't use function expretions before we write ththem in code, also for const and let variables before of their decleration

## This Keyword

- console.log(this); # this in global scope is window object

- const calcAge = function (birthYear) { # 'this' here is undefigned in regular function because here 'this keyword' is for function scope and not point to any object
  console.log(2037 - birthYear);
  console.log(this);
};
calcAge(1991);

- const calcAgeArrow = birthYear => { # because arrow funtion does not have own 'this keyword' and its 'this' is from parents that here is window
  console.log(2037 - birthYear); 
  console.log(this);
};
calcAgeArrow(1980);

- const jonas = { # 'this' points to jonas because 'this' always points to object that call the method
  year: 1991,
  calcAge: function () {
    console.log(this);
    console.log(2037 - this.year);
  },
};
jonas.calcAge();

- const class: {} # it's not block it's an object litteral block

- const jonas = {
  firstName: 'Jonas',
  year: 1991,
  calcAge: function () {
    // console.log(this);
    console.log(2037 - this.year);
    
    const self = this; // self or that
    const isMillenial = function () {				# here if we don't use self and use 'this' in fuction, because of regular function has own 'this' point to undefigned.  
      console.log(self);
      console.log(self.year >= 1981 && self.year <= 1996);
    };

    // Solution 2
    const isMillenial = () => {				       # here because of arrow function does not have own 'this' point to parent's 'this' that here is jonas.
      console.log(this);
      console.log(this.year >= 1981 && this.year <= 1996);
    };
    isMillenial();
  },
}


## Primitives and object Primitives and Refrence Types

- primitives -> number, string, boolean, undefigned, null, symbol, bigInt # stored in call stack (execution contect)
- let age = 30; # age points to 30 that stored in stack 
- let oldAge = age; old age also points to same address
- age = 31; age now points to new address that 31 has been stored in it
- console.log(age); # 31
- console.log(oldAge); # 30

- Objects -> object literals, arrays, functions, ...
- const me = { # me points to a address in stack that has stored me's address in heap.
    name: 'Jonas',
    age: 30,
- };
- const friend = me; # friend and me point to same address of stack(that has stored me's address) so if we change the age both of them will change.
- friend.age = 27;
- console.log('Friend:', friend); # 27
- console.log('Me', me); # 27

## Primitive types
- let lastName = 'Williams';
- let oldLastName = lastName;
- lastName = 'Davis';
- console.log(lastName, oldLastName);

## Reference types
- const jessica = {
    firstName: 'Jessica',
    lastName: 'Williams',
    age: 27,
  };
- const marriedJessica = jessica;
- marriedJessica.lastName = 'Davis';
- console.log('Before marriage:', jessica);
- console.log('After marriage: ', marriedJessica);

## Copying objects
- const jessica2 = {
    firstName: 'Jessica',
    lastName: 'Williams',
    age: 27,
    family: ['Alice', 'Bob'],
  };

- const jessicaCopy = Object.assign({}, jessica2); # merge jessica2 with empty obj, so it's real copy of original (it means new object had create in heap with same property but if you change it, original one doesn't change)
- assign just work in first level, that mean's if the original obj has object in it when you assign just the properties that are not object copied(string, number, ...) and objects are not copied (array, ...) so again the second object that merged just point to the for example array that is in first object (this copy is shallow copy)

