# Chapter 1: Values, Types, and Operators #

With computing, there is only data; whether it's reading, modifying, or creating new data.

Data is stored in bits. Bits are binary, meaning they can be one of two values. The typical abstraction people refer to is 1 and 0, but there is also true and false, a high vs low electric charge, or a shiny vs dull spot on a CD.

All data can be reduced to a sequence of bits.

The following is an example of the number 13 expressed in bits/binary:

```javascript
Value:    0   0   0   0  1  1  0  1
Place:  128  64  32  16  8  4  2  1
```

This binary number equates to 8 + 4 + 1 = 13.

## Values ##

A typical modern computer has upwards of 30 billion bits. In order to work within these large quantities of bits, we separate them into chunks that represent pertinent information. In JavaScript, those chunks are called *values*.

Values can be numbers, text, functions, etc.

To create a value, you merely invoke its name. Wildly convenient.

Every value has to be stored. If you use a large amount of values at the same time, you might run out of memory. Fortunately, this only comes up if you need the values simultaneously.

As soon as you don't need a value, it disappears. The bits that were representing it can be used for something else. This process is referred to as *garbage collection*.

In essence, memory management is handled for you in JavaScript unlike a low-level language, like C.

Below is a practical example of what's happening in memory, while writing JavaScript:

```javascript
var n = 123; // allocates memory for a number
var s = 'azerty'; // allocated memory for a string

var o = {
	a: 1,
	b: null
}; // allocates memory for an object and contained values

var a = [1, null, 'abra']; // allocated memory for an array and contained values

function f(a) {
	return a + 2;
} // allocates a function (which is a callable object)

var d = new Date(); // allocates a Date object

var e = document.createElement('div'); // allocates a DOM element

var s2 = s.substr(0, 3);
/*
 * since strings are immutable values
 * JavaScript may decide to not allocate memory in this instance,
 * but instead just store the [0, 3] range
 */
```

Note: you should still be aware of memory management even though JavaScript handles these things for you. It's still important.

### Numbers ###

JavaScript represents numbers using 64 bits. This means the amount of numbers that can be represented is limited to a degree, but most (and I really mean most) will not need anything larger than a 64-bit number. The number of representations that can exist with 64 bits is 2<sup>64</sup> or about 18 quintillion.

*Overflow* is to use a value that does not fit with the number of bits allocated. For example, lets say we're have an 8-bit number that's only used for positive, whole numbers. That would leave us with a max value of 2<sup>8</sup> or 256. Attempting to represent 257 with this pattern is overflowing.

Not all whole numbers below 18 quintillion fit into a JavaScript number because those bits can also represent negative and fractional numbers.

Number expressions are written as follows:

```javascript
42 // standard whole number
-42 // negative whole number
9.81 // fractional number
-9.81 // negative fractional number
2.998e8 // scientific notation; e = exponent; 2.998 x 10^8 = 299,800,000
```

#### Arithmetic ####

Calculations with whole numbers are guaranteed to be precise. Calculations with fractional numbers are not. Some fractional numbers lose precision when only 64 bits is available to them.

Arithmetic operations take two *operands* and an *operator* and return a new value. Example below:

```javascript
10 + 4 // returns 14
10 + 4 * 11 // returns 54; see precedence
(10 + 4) * 11 // returns 154
```

One arithmetic operator that is not immediately obvious is ```%```, which returns a *remainder* of two operands. This is sometimes referred to as a modulo, the modulus operator, or the remainder operator. Example below:

```javascript
144 % 12 // returns 0 because 144 / 12 is equal to 12 with no remainder
314 % 100 // returns 14 because 314 / 100 is equal to 3 with a remainder of 14
```

#### Special Numbers ####

In JavaScript, there are three values that are considered numbers, but don't behave or look like a normal number.

The first two are ```Infinity``` and ```-Infinity```, which represent positive and negative infinities. It's nonsense really.

The last value is ```NaN```, which stands for "not a number". You will get this value if you attempt any arithmetic that won't yield a meaningful result, such as ```0 / 0``` or ```'boom' * 4```.

### Strings ###

Strings are used to represent text. They are written by enclosing content in quotes. You can use single quotes, double quotes, or backticks as seen below:

```javascript
`Down on the sea`
"Lie on the ocean"
'Float on the ocean'
```

Certain characters require *escaping* to be used properly in strings. Escaping is done with a backslash (\) followed by some set of characters. Some examples include:
```javascript
'\n' // new line
'\'hello\'' // returns "hello"; a literal single quote
'\\' // returns "\"; a literal backslash
```

Strings have been modeled as a series of bits. JavaScript does this based on the *Unicode* standard. This standard assigns a number to virtually every character you would ever need. If every character is associated with a number, than a string can be described by a sequence of numbers. JavaScript's representation uses 16 bits per string element, which provides up to 2<sup>16</sup> different characters. Unicode defines more characters than 16 bits would allow, so some characters take up two string elements and therefore are afforded 32 bits.

The plus operator (+) can be used on strings for the purpose of concatenation. See below:

```javascript
'con' + 'cat' + 'e' + 'nate' // returns "concatenate"
```

There is one difference of note between the three quoting methodologies: using backticks (\`) creates a *template literal*, which can span multiple lines and allows you to embed expressions and values without using concatenation. Example below:
```javascript
var name = 'Adam';

// Without template literal
'My name is ' + name  // returns "My name is Adam"

// With template literal
`My name is ${name}` // returns "My name is Adam"

// Template literal with an expression to be evaluated
`Half of 100 is ${100 / 2}` // returns "Half of 100 is 50"
```

### Unary Operators ###

All of the operations we've seen thus far use *binary* operators, meaning that they require two operands. A *unary* operator only requires one operand.

The minus operator can serve as a binary or unary operator. In the context of a calculation such as `10 -2`, the operator is binary. When setting a number to be negative `-20`, the operator is unary.

Another example of an unary operator is `typeof`, which returns the type of the operand it's provided as a string. Example below:

```javascript
typeof 2.5 // returns "number"
typeof 'hello' // returns "string"
```

### Boolean Values ####

JavaScript has a *Boolean* type, which can have only one of two values: ```true``` or ```false```.

#### Comparison ####

Comparison operators can be used compare operands against each other and return Boolean values. Comparison operators includes:

* ```>``` - greater than
* ```>=``` - greater than or equal to
* ```<``` - less than
* ```<=``` - less than or equal to
* ```==``` - equal to (uses type coercion)
* ```!=``` - not equal to (uses type coersion)
* ```===``` - equal to (compares value and type)
* ```!==``` - not equal to (compares value and type)

Examples below:

```javascript
3 > 2 // returns true

3 < 2 // returns false

(3 + 3) >= 6 // returns true

// strings can also be compared
// it's ordered by the Unicode bit value
// which is roughly in alphabetical order
'Aardvark' < 'Zoroaster' // returns true

'Itchy' != 'Scratchy' // returns true

'Apple' == 'Orange' // returns false

// using == or != will coerce the type to be the same
// so the second operand gets converted to a string
'true' == true // returns true

// using === or !== will not coerce the type
// resulting in a different outcome
'true' === true // returns false
```

For string comparison, note that the order is uppercase letters, lowercase letters, and non-alphabetic characters.

#### Logical Operators ####

## Quiz Yourself

1. Express the number 45 in binary.
>```javascript
Value:    0   0   1   0  1  1  0  1
Place:  128  64  32  16  8  4  2  1
```

2. Describe *garbage collection*.
> Garbage collection is a form of automatic memory management that abstracts that complexity away from the developer. In this process, values that are no longer needed are automatically thrown out and the bits that represented that value can be used for something else.

3. What is *overflowing*?
> Overflowing is using a value that does not fit with the number of bits allocated for that value. In our context, JavaScript utilizes 64-bit numbers, which includes bits for negative and fractional numbers. It typically should not be a problem as your maximum number is still very large.

4. In what instances are arithmetic calculations guaranteed to return a precise number? What instances are they not? Why?
> Calculations with whole numbers are guaranteed to be precise. Calculations with fractional numbers are not. Some fractional numbers lose precision when only 64 bits is available to them.

5. Describe the *modulus* operator.
> The modulus operator returns the remainder of two operands when they're divided.

6. What is NaN? What type is it?
> NaN stands for "not a number". It is the result of any arithmetic that won't yield a meaningful result, such as ```0 / 0``` or ```'boom' * 4```. It's of type number even though its an abbreviation for "not a number".
