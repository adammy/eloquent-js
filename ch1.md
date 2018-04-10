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

Not all whole numbers below 18 quintillion fit into a JavaScript number because those bits can also represent negative and non-whole numbers.
