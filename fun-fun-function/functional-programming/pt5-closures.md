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

## Emulating Private Properties & Methods with Closures ##

One of the better practical examples of closures is to use it for privatizing data and reducing your footprint on the global namespace. One way to do this is with what is know as the *module pattern*:

```javascript
const counter = (function () {

	let privateCounter = 0;

	// private method that is utilized by the public methods
	function changeBy(val) {
		privateCounter += val;
	}

	// public methods
	return {
		increment: function () {
			changeBy(1);
		},
		decrement: function () {
			changeBy(-1);
		},
		value: function () {
			return privateCounter;
		}
	}

}());

counter.value(); // 0
counter.increment();
counter.increment();
counter.value(); // 2
counter.decrement();
counter.value(); // 1
```

In this example, we create a single lexical environment that is shared by our methods: increment(), decrement(), value(), and changeBy(). The shared lexical environment is created in an anonymous function, which is executed immediately. The private items (privateCounter and changeBy()) are not accessible outside of the anonymous function. Instead, they must be accessed by the three public methods that are returned from the anonymous function. The functions are all closures with the same lexical environment.

## Quiz Yourself ##

1. Describe what a closure is.
> A closure is the combination of a function and the lexical environment within that function was declared. A functions lexical environment gives it access to variables and arguments supplied by a parent function. It is a way of attempting to not flood the global namespace.

Sources:

https://www.youtube.com/watch?v=1DMolJ2FrNY

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
