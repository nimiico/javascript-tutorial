# DATA STRUCTURES

## Destructuring

- const arr = [1, 2, 3]; # (packing)
- const [x, , z] = arr -> x = 1, z = 3 # array destructuring (unpacking)

- let x = 1;
- let y = 2;
- [x, y] = [y, x] -> x = 2, y = 1 # change values without temp
- const [p=1, q=1, r=1] = [8, 9] # p = 8, q = 9, r = 1

- const resturant = { name: 'nimico', location: 'tehran'}
- const {name: resturantName = [], location: loc} -> resturantName = nimico, loc = tehran # destructuring object # <property name>: <variable name> = <default value> (<variable name>, <default value> is optional)

- let a = 111;
- let b = 999;
- const obj = { a: 23, b: 7, c: 14 };
- ({ a, b } = obj); # put () for mutating object's poperties

- const resturant: {
    orderDelivery({ starterIndex = 1, mainIndex = 0, time = '20:00', address }) {
      console.log(
        `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
      );
    }
  }
- restaurant.orderDelivery({	# pass just one object and destructuring in method
  time: '22:30',
  address: 'Via del Sole, 21',
  mainIndex: 2,
  starterIndex: 2,
});

## Spread Operator

- it's work on all iterables (arrays, string, maps, set and not objects)

- const arr = [7, 8, 9];
- const newArr = [1, 2, ...arr]; # ... extend arrayto seperate elements
- console.log(newArr); # [1, 2, 7, 8, 9]

- const newRestaurant = { foundedIn: 1998, ...restaurant, founder: 'Guiseppe' };
- console.log(newRestaurant); # add properties to the object

## Rest Pattern 

- const [a, b, ...others] = [1, 2, 3, 4, 5]; # rest pattern
- console.log(a, b, others);

- const { sat, ...weekdays } = restaurant.openingHours; # rest pattern for objects
- console.log(weekdays); # all days except sat

- const add = function (...numbers) {				# get an array of any numbers # rest pattern
  let sum = 0;
  for (let i = 0; i < numbers.length; i++) sum += numbers[i];
  console.log(sum);
};
- add(2, 3);
- add(5, 3, 7, 2);
- add(8, 2, 5, 3, 2, 1, 4);

## Short Circuiting

- console.log(3 || 'Jonas') # 3 # because it's 'or' and javascript when get to first truthy value choose (like python)
- console.log(undefined || null); # null # both of them is false but javascript move to end to see truthy value but it expretion doesn't have any truthy value so choose the last one

- const guestCorrect = restaurant.numGuests ?? 10; # Nullish: null and undefined (NOT 0 or '') # 0 or '' is not false

- console.log(0 && 'Jonas'); # 0 # because when the one of the values be false so javascript doesn't see rest f expretion
- console.log(7 && 'Jonas'); # 'Jonas' # last true

## For-Of-Loop

- menu = [a, b, c]
- for (const i of menu) console.log(i); # a, b, c

- for (const [i, el] of menu.entries()) { # entries function, get an array with length = 2 for each element of menu that includes: index: element. so we can destructuring this to i and e
  console.log(`${i + 1}: ${el}`); # 1: a    2:b   3:c
}

## Optional Chaining

- console.log(restaurant.openingHours?.mon?.open); # if 'openingHours' doesn't exist javascript does not compile rest of it so you don't get error and then check 'mon' 

- console.log(restaurant.order?.(0, 1) ?? 'Method does not exist'); # for methods first check it then: .(argument). (in this example order)

## Looping Objects

- const Human: { name: 'nima', lastname: 'eslami' }
- const properties = Object.keys(Human); # properties is an array that includes [name, lastname]
- const values = Object.values(openingHours); # values is an array that includes ['nima', 'eslami']

- const entries = Object.entries(openingHours); # the first element of object entries is key and second one is value and we can destructing like arrays 

## Sets

- const ordersSet = new Set(['Pasta', 'Pizza', 'Pizza', 'Risotto', 'Pasta','Pizza'])
- console.log(ordersSet); # ['Pasta', 'Pizza', 'Risotto'] # unique

- ordersSet.has('Bread'); # boolean
- ordersSet.add('Garlic Bread'); # add
- ordersSet.delete('Risotto'); # delete

- const staff = ['Waiter', 'Chef', 'Waiter', 'Manager', 'Chef', 'Waiter'];
- const staffUnique = [...new Set(staff)]; # unique by stack and then pack it into array

## Maps

- unlike objects that keys always are string type, keys in maps can be any types

- const question = new Map([ [1, 'C'], [2, 'Java'],  [3, 'JavaScript'] ]);
- const rest = new Map();
- rest.set('name', 'Classico Italiano'); # adding new element to map (key, value)
- rest.get('name'); # get value
- rest.has('categories');
- rest.delete(2);
- rest.size;

- const a = new Map(Object.entries(question)); # {"1" => "c"}, ...# entries is map 

- console.log(question.get('question'));
- for (const [key, value] of question) {
    if (typeof key === 'number') console.log(`Answer ${key}: ${value}`);
  }
  
- console.log([...question]); # convert to array that each element is array with two element includes key and value

## When We Use Each Structure

- Arrays -> ordered, manipulated
- Sets -> unique, high performance, remove duplicates

- Object -> esier to access with , and [], use function as values
- Map -> better performance, any types for keys, easy to itrate, easy to compute size

## Working with Strings

- const name = 'nima eslami';
- name[0] = 'n'
- name.length = 4
- name.inedexOf('a') = 3
- name.slice(3) = 'a eslami'
- name.slice(3, 7) = 'a es'
- name.slice(airline.lastIndexOf(' ') + 1) = 'eslami'
- name.slice(1, -1) = 'ima eslami'
- name.toLowerCase() = 'nima eslami'
- name.toUpperCase() = 'NIMA ESLAMI'
- name.toLowerCase().trim() # trim and lower case
- name.replace('i', 'e').replace('m', 'n') = 'nena eslami' # replace first i and m
- name.replace(/i/g, 'e') # replace all 'i'
- name.includes('nima');
- name.startsWith('ni');
- 'a+very+nice+string'.split('+') = ['a', 'very', 'nice', 'string']
- const newName = ['Mr.', firstName, lastName].join('-') = 'Mr.-nima-eslami'
- message.padStart(20, '+').padEnd(30, '+'); # the length of message been 30 and add + to start and end of sentence to fill 30 character.