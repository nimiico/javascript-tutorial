# FUNDAMENTALS

- console.log(value) # see value in inspect console

- <script src="script.js"></script> # declare script file in the latest part of body element in html

- let firstName = "Nima"; # declare variable

## Data Types
- Number # float
- String
- Boolean
- Undifined # let child;
- Symbol # value that is unique
- BigInt #larg integers

- console.log(typeof javaScriptIsFun); # type of value

## Declaring
- let year = 1991; # mutable and block scoped
- const year = 1991; # immutable  
- var year = 1991; # mutable and function scoped

## Operators
- * / + - ** # multiple divide add mines exponeniation 
- > => < =<

- console.log('Nima' + ' ' + 'Eslami') = Nima Eslami # concatenation

## Template literals
- const name = 'Ali'
- const age = 22
- `${name} is ${age} years old.` # template literals  # expretions can be placed in {} and expretions is everything that make value
- ` a
    b  # multiline
    c`

## Type Conversion
- const year = '1991';
- console.log(Number('1991')); # convert string to number

- console.log(10 + "3" + 4) = 1034
- console.log(10 + 3 + '4') = 134
- console.log("23" - "10") = 13
- console.log("10" * "2") = 20
- console.log("10" / "2") = 5
- console.log("10" > "1") = true

- Falsy values: 0, '', undefined, null, NaN

## Equality Operation
- '18' == 18 -> true # == has type convertion (!=)
- 18 === '18' -> false # === does not have type covertion (!==) # use this

## Logical Operator
- and(&&) * or(||) * not(!)

## switch statement
- const day = "saturday";
switch (day) {
  case "sunday":
    console.log("sunday");
    break;
  case "saturday":
    console.log("saturday");
    break;
  default:
    console.log("none");
}

## Conditional Ternary
- const age = 17;
  const x = age >= 18 ? "OK" : "NO"; # true statement : false statement
  console.log(x);



