# FUCTIONS

- const createBooking = function (flightNum, numPassengers = 1, price = 199 * numPassengers) {} # put default value
- primitives type when you pass them to function they are new value and will be store in stack but passing non primitives value is new refrence to the value that is stre in heap so if change it all of refrenes that point to this valuew will be change.

- Higher Order Function -> function that give function in arguments or return a function
- callbacck -> the function that pass to another function 

## Functions Returning Functions

- const greet = function (greeting) {
    return function (name) {
      console.log(`${greeting} ${name}`);
    };
  };
  
- const greetArr = greeting => name => console.log(`${greeting} ${name}`); # arrow function returning arrow function

- const greeterHey = greet('Hey');  # first way
- greeterHey('Jonas'); # pass argument for function thar returning another function 

- greet('Hello')('Jonas'); # second way 

## Call Method

- book.call(swiss, 583, 'Mary Cooper'); # when you have some Objects with common function we can write it and then for calling this function for Objects we can use call method. (function.call(<obj>, <arguments of fun>))

## Bind Method

- const bookEW = book.bind(eurowings); # bind book function by eurowings object. so when we call bookEW it called by eurowings object and point to eurowings
- bookEW(23, 'Steven Williams'); # call it
- const bookEW23 = book.bind(eurowings, 23); # also we can preset arguments

## Invoke Fuv=ction

- (function () {
    console.log('This will never run again'); # this fuction call by () and just somewhere that you declare it, you can call it
    const isPrivate = 23;
  })();

  ## Closure

- the function access to veraibles that exist in create place. (in bottom example, f access to g veraibles and closure is like bagpack that include this veraibles that every where we use f, we also access to a because a is in bagpack.)

- let f; # at first assign to prent that g and then assign to h 

const g = functio to h{
  const a = 23;
  f = function () {
    console.log(a * 2);
  };
};

const h = function () {
  const b = 777;
  f = function () {
    console.log(b * 2);
  };
};

g();
f();
console.dir(f);

// Re-assigning f function
h();
f();

- read more in examples and practice

