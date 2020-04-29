# js-cheatsheet
 Syntax cheatsheet and other helpful learning aids for beginners to javascript

## Variables and Constants

Variables are a handy way to store information and give it a name.

The most common syntax to create variables prior to ES2015 was the `var` keyword.
```javascript
var x; // create variable "x" but don't initialize
var name = 'Jolene'; // create variable "name" and initialize value

var x = 42; // legal, even though x is already declared
name = 'Charlene'; // this is a better way to overwrite a value

```

As of ES2015 and afterward, the preferred way to create variables is with the `let` keyword, rather than `var`. This is more strict than `var` in its usage, and is less loosy-goosy about how it can be used (and abused).

```javascript
let x; // same as before, just a new keyword
let name = 'Jolene'; // ditto

let x = 42; // will throw an error, x is already defined
x = 3.14; // this will work, since we're just assigning a value, not completely "re-defining" x
name = 'Charlene'; 
```

Constants are similar to variables, with the exception that they cannot change their value after being created. Since they cannot change their values, they have to be initialized as soon as they are declared, or otherwise an error will be thrown. To declare constants, use the same syntax as you would for variable initialization, but instead of `let` use the keyword `const`.

```javascript
const x; // ERROR! Missing initializer in const declaration
const y = 29; // y is 29 and it always will be

y = 30; // Error, assignment to constant variable

/**
    constants usually use all caps so that programmers
    who encounter them will immediately know that they
    are constants
*/
const SCREEN_WIDTH = "20px"; // that's a small screen, and such a shame, because it'll never get any wider
```

## Numbers

Numbers in javascript behave about like the numbers you're used to from math class. You can do any basic arithmetic operations on them that you're used to (add, subtract, multiply, divide, take the remainder). 

There is also a handy [Math library](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math) that contains a lot of useful functions for doing more advanced stuff with numbers beyond those basic operations.

Spacing around the operators is insignificant/unnecessary, but most style guides seem to suggest that one space on either side of the operator is a good practice.

```javascript
let x = 128;
console.log(x + 128); // addition: 256
console.log(x - 64); // subtraction: 64
console.log(x * 4); // multiplication: 1024
console.log(x / 4); // division: 32
console.log(x % 10); // remainder: 8

/* 
    remainder is also called the modulo operator
    it can take some getting used to but once you're accustomed
    to it it is very handy for some use cases
*/

// evens and odds
console.log(28 % 2); // 0, odd
console.log(19 % 2); // 1, even

// dollars and cents
const pennies = 2040;
let cents = pennies % 100; // 40 cents
let dollars = (pennies - cents) / 100; // 20 dollars

//alternatively, using Math
dollars = Math.floor(pennies / 100);

// days of the week
// imagine that january 1st (day 0 of the year) is on a sunday
// how can you tell what day of the week a given day is?
/*
    Date  | DayNum | Weekday | WeekdayNum
    ========================================
    Jan 1 | 0      | Sun     | 0
    Jan 2 | 1      | Mon     | 1
    Jan 3 | 2      | Tue     | 2
    Jan 4 | 3      | Wed     | 3
    Jan 5 | 4      | Thu     | 4
    Jan 6 | 5      | Fri     | 5
    Jan 7 | 6      | Sat     | 6
    Jan 8 | 7      | Sun     | 0
    ========================================
    Etc...
*/
// what day of the week is day number 250 of the year?
console.log(250 % 7); // 5 (Friday)

```

## Strings

Strings hold text data. Strings can be surrounded by either single quotes `'foo'`, double quote `"bar"`, or backticks `` `baz` ``. When backticks are used, the value inside is called a **template literal**, and it can conveniently have javascript variables and expressions embedded in it so that you don't have to do string concatenation.

```javascript
let firstName = 'Dolly';
let lastName = "Parton";
console.log(`Howdy y'all, I'm ${firstName} ${lastName}. Pleased to meet you!`);

/*
 if you find yourself needing to use an apostrophe in a string,
 you can choose to use double quotes or backticks as the quotes
 around the string, or if using single quotes, you can use 
 backslash (\) to escape the single quote... 
 This is also the case for the other types of quote marks
*/
let whose = "Murray's";
whose = `Sal's`;
whose = 'Joe\'s'; // displays as Joe's
let quote = "And he said to me \"Speak for yourself!\"";
let observation = `You ever notice how it's only programmers that use the "\`" key?`;

// Other string properties

//String length property
console.log("Hello".length); // prints 5

// finding individual characters
console.log("No I in TEAM"[3]); // prints "I"

// fiddling with case
console.log("shouting".toUpperCase()); // SHOUTING
console.log('WHISPERING'.toLowerCase()); // whispering

// slicing
// str.slice(start_index, end_index);
// if you don't supply 2nd arg, slices to the end of string
// negative index means count from the end of the string
console.log("Anybody home?".slice(10,12)); // me
console.log('You better not say "orange"'.slice(-8)); // "orange"

// trim
console.log("    slim    ".trim()); // slim (without spaces)

```

## Arrays

Arrays are useful for holding sequences of data. Some languages have the restriction that arrays can only hold one type of objects at a time (an array of strings, or an array of numbers). Javascript has no such restriction.

```javascript
let records = []; // initializing an empty array
let fruits = ['mandarin', 'banana', 'grape']; // initialize with data

console.log(fruits.length); // 3

records.push("In Rainbows"); // add element to end of array
records.unshift("Hail to the Thief"); // add elem at beginning
records.unshift("Amnesiac"); 

/*
    pop() and shift() remove elements from an array and
    return them.
    pop() removes from the end of the array
    shift() removes from the beginning of the array
*/

records.pop(); // returns 'In Rainbows'
console.log(records); // ["Amnesiac", "Hail to the Thief"]
records.shift(); // returns "Amnesiac"
console.log(records); // ["Hail to the Thief"]

/*
    Accessing array elements is done by using square brackets []
    This is also known as "subscripting"
*/
```

## Objects

## Conditionals and Logic

## Loops

## Functions