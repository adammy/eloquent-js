# Part 5: Closures #

Functions are closures. That means that the function body has access to variables that are defined outside of the function. Let's start with a simple example:

```javascript
const me = 'Bruce Wayan';
function greet() {
	console.log('Hello, ' + me);
}
greet();
```

Notice how we aren't referring to an argument, but rather we're referring to a variable that isn't in its body, but is still within its *lexical environment*.

This is kind of a bad example though. The real distinction of a closure is the lexical environment. If a function is wrapped inside another function, that inner functions lexical environment becomes that parent function. Let's look at an example:

```javascript
function person(name) {
	const name = name || 'Bruce Wayan';
	function greet() {
		console.log('Hello' + name);
	}
	greet();
}
```

In this example, the greet() functions lexical environment is the person function. This means that greet() has access to the variables defined in person(), including any arguments supplied.

## Quiz Yourself ##

1. Describe how the reduce() method on the Array.prototype works.
> The reduce() method is used for more complex transformations that aren't possible with other Array.prototype methods. The reduce() method takes two arguments: a callback function (standard) and an initial value for an accumulator. The callback function takes two arguments as well: the accumulator (which on its first iteration is set to the initial value you provided) and the current element in the array. The callback function is intended to return a new value for the accumulator to be used in the next iteration.

Source: https://www.youtube.com/watch?v=1DMolJ2FrNY
