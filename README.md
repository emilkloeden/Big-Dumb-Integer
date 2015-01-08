# Big-Dumb-Integer
## Don't use this for anything, really.

Big Dumb Integer (or BDI) is a JavaScript library built as an exercise to allow arbitrary precision integer maths in the language.

BDI was developed as a learning project to aid with solving Project Euler problems in JavaScript. 

There are other libraries out there that provide arbitrary precision mathematics solutions for users of JavaScript that are smaller, and _much, much_ better. The author recommends Peter Olson's https://github.com/peterolson/BigInteger.js and Silent Matt's http://silentmatt.com/biginteger/ alternatives. They were both highly-used sources of inspiration in the building of this project.

### What it does

BDI stores integers in a 'Big' object and supports comparison, addition, subtraction and multiplication of positive and negative integers in base 10. That's right, as yet, there is no support for division. That's because division tends to lend itself to floating point maths and that stuff is _hard_. Maybe one day, when the next Project Euler problem requires it.

### Calling the library
```javascript
var Big = require('Big-Dumb-Integer').Big;
```

### The 'Big' Object
Each 'Big' object is instantiated by calling new Big(number) where number can be:
* a number
* a string
* an array of single digit numbers (negative numbers can be passed if the first value is a string equal to '-'). Only limited checking of this applies.
* another Big object

### Object Properties
#### .sign
Either 'POSITIVE', 'NEGATIVE' or 'NEUTRAL'

#### .number
An array of single digit integer values

### Object Methods
Object methods return new Big object instances, in this way the both leave the original object as is and allow for method chaining.

```javascript
var Big = require('Big-Dumb-Integer').Big;
var a = new Big('-10');
var b = new Big(12);

var c = a.add(b);

console.log(a.toString()); // '-10'
console.log(b.toString()); // '12'
console.log(c.toString()); // '2'
```

#### .abs()
Takes any accepted input and returns a new Big object with the sign 'POSITIVE'. This means it is currently broken for Zero but that bug is required by **.subtract()**.

#### .add(input)
Takes any accepted input adds it to the current Big object and returns a new Big object.

#### .eq(input)
Takes any accepted input and returns `true` if equal to current object or `false` otherwise.

#### .gt(input)
Takes any accepted input and returns `true` if the current object is the greater of the two.

#### .gte(input)
Takes any accepted input and returns `true` if the current object is greater than or equal to the input value.

#### .invert()
Invert Big.**.sign** (multiplies by -1).

#### .listify()
Converts a Big object to an array. Not especially useful.

#### .lt()
Takes any accepted input and returns `true` if the current object is the lesser of the two.

#### .lte(input)
Takes any accepted input and returns `true` if the current object is less than or equal to the input value.

#### .minus(input)
Alias for **.subtract()**

#### .multiply(input)
Takes any accepted input, multiplies it by the current object and returns a new Big object.

#### .numify()
Converts a Big object to a number. Likely to be buggy, not yet tested with large integers.

#### .toString()
Converts a Big object to a String.

#### .plus(input)
Alias for **.add()**.

#### .subtract(input)
Takes any accepted input, subtracts it from the current object and returns a new Big object.

#### .take(input)
Alias for **.subtract()**

#### .trimLeadingZeroes()
A helper method that removes any leading zeroes from **Big.number**. Used in **.subtract()** and **.multiply()** methods.

