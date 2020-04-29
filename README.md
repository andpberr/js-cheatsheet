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
    This is also known as "subscripting" or "indexing"

    Indices for arrays in javascript start at 0
*/
let myArray = [
    'raining',
    'cats',
    'and',
    'dogs'
];

console.log(myArray[1]); // 'cats'

// slicing works similar to string slicing
console.log(myArray.slice(1));
// ['cats', 'and', 'dogs']

// Arrays of strings can be concatenated with a separator using join()
myArray.join(' '); // "raining cats and dogs"

let csv = ['name','age','height','weight'];
csv.join(','); // 'name,age,height,weight'

/*
    Array elements can be any type of data
    Including other arrays
*/
let ticTacToe = [
    ['O', 'X', '_'],
    ['O', '_', '_'],
    ['_', 'X', '_']
];

// indexing can be thought of from the "outside inward"
// so ticTacToe[0] is the first subArray of ticTacToe
ticTacToe[1][1] = 'X'; // X wins the game!
console.log(ticTacToe);
/* 
[
    ['O','X','_'],
    ['O','X','_'],
    ['_','X','_']   
]

*/

```

## Objects

While arrays are used to hold sequences of data elements, objects contain a collection of named data elements. This can be handy when working with complex types of data that have many attributes.

```javascript
/*
  Imagine you're digitally storing a collection of
  vinyl records using javascript. Since you know
  arrays, you can use arrays to represent records
  and their attributes (artist, title, etc)
*/
let myRecords = [
    //title, artist, vinylColor, numSongs, numDiscs
    ['A Moon Shaped Pool', 'Radiohead', 'gray', 10, 1],
    ['Hail to the Thief', 'Radiohead', 'black', 14, 2],
    ['Deltron 3030', 'Deltron 3030', 'black', 21, 2]
];

// as your program grows, it will be increasingly
// difficult to keep track of the fact that 
// record[0] is the title
// record[1] is the artist name
// record[2] is the color of the vinyl
// etc...
// Also, cases like Deltron 3030 make it unclear
// which field is the title and which is the artist

// Eventually it would become second nature,
// but the overhead of having to memorize
// the numbering scheme is something we 
// can avoid with objects

// What if the array instead looked like this?
myRecords = [
    {
        title: 'A Moon Shaped Pool',
        artist: 'Radiohead',
        vinylColor: 'gray',
        tracks: 10,
        discs: 1
    },

    {
        title: 'Hail to the Thief',
        artist: 'Radiohead',
        vinylColor: 'black',
        tracks: 14,
        discs: 2
    },

    {
        title: 'Deltron 3030',
        artist: 'Deltron 3030',
        vinylColor: 'black',
        tracks: 21,
        discs: 2
    }
];

// Now each record is represented by an object,
// which has named fields instead of numbered 
// array indices
let amsp = myRecords[0];
console.log(amsp['vinylColor']); // 'gray'

// besides the square bracket notation, you can
// also access attributes of objects with dot notation
amsp.title; // no quotes
amsp['title']; // bracket notation needs a string in quotes

// objects can be given new attributes
amsp.favoriteSong = 'Identikit';

// you can assign multiple attributes at once 
// using Object.assign()
let dish = {hotdog:1, hotdogBun:1};
let toppings = {mustard: '2 squirts', onion:'half cup', relish: '1 squirt'};
Object.assign(dish, toppings);

console.log(dish);
/*
{
    hotdog:1,
    hotdogBun:1,
    mustard: '2 squirts',
    onion:'half cup',
    relish: '1 squirt'
}
*/

// If using ES2015, you can use the spread operator
// to do multiple attribute assignment as well
dish = {...dish, ...toppings}; // equivalent to above Object.assign() call

```

## Conditionals and Logic

Occasionally you'll need your code to do different things depending on what kinds of conditions there are.

```javascript
let outfit = {
    top:'t-shirt', 
    bottom: 'jeans', 
    shoes:'sneakers'
};

// random temperature between 50 and 80
let temperature = Math.floor(Math.random()*30)+50;

if (temperature < 60) {
    outfit.outerwear = 'light jacket';
} else if (temperature < 76) {
    // do nothing, my outfit is on point
} else {
    // 76 or hotter? better go change
    outfit.shirt = 'tanktop';
    outfit.bottom = 'shorts';
}
```

## Loops

### `while` loop

`while` executes its body over and over again until the condition passed is no longer true.

```javascript
let fillet = {type: 'mahi', temperature: 34};

function bake(food) {
    food.temperature += 1;
}

// bake the mahi fillet until it's reached a safe temp
while (fillet.temperature <= 145) {
    bake(fillet);
}

```

### `do` loop (or `do...while` loop)

A `do...while` loop executes the code within itself before checking the condition. A `do...while` loop will always run its code at least once.

You should brush your teeth before bed until you're minty fresh. You may have just eaten a peppermint patty, so you already feel minty fresh, but you should brush your teeth anyway. This is a dumb example but I'm running out of ideas. Also, `do...while` loops are pretty much the least-used in practice.
```javascript
do {
    brushTeeth();
} while (!mintyFresh);

```

### `for` loop

The `for` loop is probably the most common type of loop. You'll find yourself using it and encountering it more than `while` and `do...while` loops.

Syntax for a `for` loop is as follows:
<pre>
for (<span style="border:1px dotted green">setup</span>; <span style="border:1px dotted green">condition</span>;<span style="border:1px dotted green">increment</span>) {
    <span style="border:1px dotted green">loop body</span>
}
</pre>

Let's look at some examples:

```javascript
let thanksgiving = [
    'beans',
    'greens',
    'potatoes',
    'tomatoes'
];

for (let i = 0; i < thanksgiving.length; ++i) {
    console.log(`Let's eat ${thanksgiving[i]}!`);
}

// the above for loop pattern of iterating 
// through all the elements in an array is so common
// that javascript offers a more concise syntax for 
// it... the "for of" loop

// the thanksgiving loop can be rewritten as
for (let food of thanksgiving) {
    console.log(`Let's eat ${food}!`);
}

// another type of for loop you may see is the
// "for in" loop... it can be used to iterate
// through the attributes of an object

// using our mahi fillet object from earlier, the
// below loop prints:
// type = mahi
// temperature = 145
for (let attr in fillet) {
    console.log(`${attr} = ${fillet[attr]}`);
}
```

## Functions