# FUNDAMENTALS Part 2

## Strict Mode
- "use strict"; # add this to the top of the js file to activate strict mode. for more secure more and give visible errors

## Functions
- function add(a, b) {
    return a + b;
}
add(2, 3);

## Function Declaration

- function calcAge1(birthYear) {	# Function declaration
  return 2037 - birthYeah;
}
- const age1 = calcAge1(1991);

- const calcAge2 = function (birthYear) {	# Function expression (without fuction name) and you must call function after that you declare it.
  return 2037 - birthYeah;
}
- const age2 = calcAge2(1991);

- const calcAge3 = birthYeah => 2037 - birthYeah; # Arrow fuction # input => return
- const yearsUntilRetirement = (birthYeah, firstName) => { # Arrow fuctions for multi input and some more complex body
  const age = 2037 - birthYeah;
  const retirement = 65 - age;
  return `${firstName} retires in ${retirement} years`;
}

## Arrays

### kind of creating array
- const friends = ['Michael', 'Steven', 'Peter'];
- const y = new Array(1991, 1984, 2008, 2020);

- const firstName = 'Jonas';
- const jonas = [firstName, 'Schmedtmann', 2037 - 1991, 'teacher', friends]; # different types can be in one array

### Arrays methods
- const friends = ['Michael', 'Steven', 'Peter'];

- friends.push('jay') # add element to end of array
- friends.unshift('jay') # add element to beginning

- friends.pop() # remove the last one
- friends.shift() # remove from beginning

- friends.includes() # boolean for including

## Objects

- const jonas = {  # like class
  firstName: 'Jonas',
  lastName: 'Schmedtmann',
  age: 2037 - 1991,
  job: 'teacher',
  friends: ['Michael', 'Peter', 'Steven']
  
  calcAge: function () {		# object method
    this.age = 2037 - this.birthYear;   # create new property age
    return this.age;
  },
};

### Accessing
- console.log(jonas.lastName); # get value of the key by property. if this property doesn't exit give undefined
- console.log(jonas['lastName']); # get value of the key by expretion of property. if this expretion doesn't exit give undefined
- console.log(jonas.calcAge());

## Loops

- for (let rep = 1; rep <= 30; rep++) {
  console.log(`Lifting weights repetition ${rep} 🏋️‍♀️`);
}

- let rep = 1;
while (rep <= 10) {
  // console.log(`WHILE: Lifting weights repetition ${rep} 🏋️‍♀️`);
  rep++;
}