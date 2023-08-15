# OOP

## Constructor Function

- const Person = function (firstName, birthYear) { # constructor object
    // Instance properties
    this.firstName = firstName;
    this.birthYear = birthYear;
  }
- const jonas = new Person('Jonas', 1991); # create Object

## ProtoTypes

- prototype use because we can declare properties and methods on prototype object, so all objects access to it isread of declare in each of them
- constructor functions have prototype property which is an object that we define methods an properties on it
- object.__proto__ # points to an object's Prototype

- Diagram: |Constructor Function (Person)| ---(.protptype)---> |Prototype| <---(.__proto__)--- |Object (jonas)|

- Person.prototype.calcAge = function () { # create method on protype property of Person
    console.log(2037 - this.birthYear);
  };
- Person.prototype.species = 'Homo Sapiens'; # set properties on prototype

- jonas.__proto__ # includes properties
- Person.prototype # is prototype of jonas
- jonas.__proto__.__proto__ # access to prototype of  jonas's prototype like: hasOwnProperty, isPrototypeOf, and another methods
- Person.prototype.constructor = Person # go back to person

- Person.hey = function () {} # declare static method. static methods are attach to constructor and not in  prototype of objects so the objects can not access to them


- jonas.hasOwnProperty('species') = false # it is not own property of object
- jonas.hasOwnProperty('firstName') = true

- const arr = [3, 6, 6, 5, 6, 9, 9];
- arr.__proto__; # show all methods of array

## ES6 Classes

- new form of declare classes

- class PersonCl {
    constructor(fullName, birthYear) { # costructor
      this.fullName = fullName;
      this.birthYear = birthYear;
    }

    calcAge() {	# Methods will be added to .prototype property
      console.log(2037 - this.birthYear);
    }

    get age() { # getter #you can use age like this: jonas.age (instead of jonas.age())
      return 2037 - this.birthYear;
    }

    set fullName(name) { # use setter with existed property (you can use it to handle set name (hear by having space)
      if (name.includes(' ')) this._fullName = name;
      else alert(`${name} is not a full name!`);
    }

    get fullName() { # getter
      return this._fullName;
    }

    static hey() { # static method (call it: PersonCl.hey)
      console.log('Hey there 👋');
      console.log(this);
    }
  }

  ## Object.create()

- const PersonProto = {
    calcAge() {
      console.log(2037 - this.birthYear);
    },

    init(firstName, birthYear) {
      this.firstName = firstName;
      this.birthYear = birthYear;
    },
  };

- const sarah = Object.create(PersonProto); # pass Object protype that we want to inherit
- sarah.init('Sarah', 1979);
- sarah.calcAge();
- sarah.__proto__ === PersonProto = true;

## Inheritance Between "Classes": Constructor Functions

- const Person = function (firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  };

- Person.prototype.calcAge = function () {
    console.log(2037 - this.birthYear);
  };

- const Student = function (firstName, birthYear, course) {
    Person.call(this, firstName, birthYear); # super from parent
    this.course = course;
  };

- students prototype inherts person prototype.
- Student.prototype = Object.create(Person.prototype); # pass Object protype that we want to inherit so student prototype object inherits from peron prototype object
- Student.prototype.constructor = Student

## Inheritance Between "Classes": ES6 Classes

- class StudentCl extends PersonCl {
    constructor(fullName, birthYear, course) {
      // Always needs to happen first!
      super(fullName, birthYear); # super parents properties
      this.course = course; # set own property
    }

    introduce() {
      console.log(`My name is ${this.fullName} and I study ${this.course}`);
    }
  }

## Inheritance Between "Classes": Object.create

- const StudentProto = Object.create(PersonProto); # at first StudentProto inherits from PersonProto
- StudentProto.init = function (firstName, birthYear, course) {
    PersonProto.init.call(this, firstName, birthYear);
    this.course = course;
  };

- StudentProto.introduce = function () {
    console.log(`My name is ${this.firstName} and I study ${this.course}`);
  };

- const jay = Object.create(StudentProto); # then pass Object protype that we want to inherit. So: jay ---inhert---> StudentProto ---inherit---> PersonProto

- jay.init('Jay', 2010, 'Computer Science'); # like before
- jay.calcAge();
- jay.introduce();

## public, private, protected

- use _ before methods and properties say they are private (conventional)
-  _approveLoan(val) {  #private method (conventional)
     return true;
  }

- - use _var and put getmethod for it to public it. (conventional)
- getMovements() {
    return this._movements;
  }

## Inheritance Between "Classes": ES6 Classes

- class StudentCl extends PersonCl {
    constructor(fullName, birthYear, course) {
      // Always needs to happen first!
      super(fullName, birthYear); # super parents properties
      this.course = course; # set own property
    }

    introduce() {
      console.log(`My name is ${this.fullName} and I study ${this.course}`);
    }
  }

## Inheritance Between "Classes": Object.create

- const StudentProto = Object.create(PersonProto); # at first StudentProto inherits from PersonProto
- StudentProto.init = function (firstName, birthYear, course) {
    PersonProto.init.call(this, firstName, birthYear);
    this.course = course;
  };

- StudentProto.introduce = function () {
    console.log(`My name is ${this.firstName} and I study ${this.course}`);
  };

- const jay = Object.create(StudentProto); # then pass Object protype that we want to inherit. So: jay ---inhert---> StudentProto ---inherit---> PersonProto

- jay.init('Jay', 2010, 'Computer Science'); # like before
- jay.calcAge();
- jay.introduce();

## public, private, protected

- use _ before methods and properties say they are private (conventional)
-  _approveLoan(val) {  #private method (conventional)
     return true;
  }

- - use _var and put getmethod for it to public it. (conventional)
- getMovements() {
    return this._movements;
  }