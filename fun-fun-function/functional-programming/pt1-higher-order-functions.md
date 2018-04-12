# Part 1: Higher-Order Functions #

In JavaScript, functions are values (mind blown). It's the reason the example below works:

```javascript
const triple = function (x) {
	return x * 3;
}

const waffle = triple;

waffle(30); // 90
```

Functions can be assigned to variables because they are values. Other variables can reference the variable that references the function because they are values. Functions can also be passed into other functions as arguments because they are values.

Functions that take other functions as arguments are called *higher-order functions*. The filter() method on Array.prototype is a good example of a higher-order function.

Let's start with an array of animals:

```javascript
const animals = [
	{ name: 'Flufflykins', species: 'rabbit' },
	{ name: 'Caro', species: 'dog' },
	{ name: 'Hamilton', species: 'dog' },
	{ name: 'Harold', species: 'fish' },
	{ name: 'Ursula', species: 'cat' },
	{ name: 'Jimmy', species: 'fish' }
];
```

Now let's say we want to only get back the animals that are dogs because we're writing enterprise-level software damnit. One solution would be to utilize a for loop like so:

```javascript
let dogs = [];
for (let i = 0; i < animals.length; i++) {
	if (animals[i].species === 'dog') {
		dogs.push(animals[i]);
	}
}
```

Now let's rewrite this using the filter() method:

```javascript
const dogs = animals.filter(animal => animal.species === 'dog');
```

Looking at the filter() method, we can see that it takes one arguments: a function. This type of function is called a *callback function*. Filter will loop through each animal in the array and pass its value to the callback function. It expects the callback function to return ```true``` or ```false``` based on some specified condition we define in the callback function. In this case, that condition is ```animal.species === 'dog'```. If the condition is true, the particular item/animal will pass through to the new array. Otherwise, it will not. After going through all of the elements/animals, the filter() method will return a new array of all elements/animals that passed the condition.

You can see the filter() example is much shorter than the traditional for loop. It's because the problem is broken down into small functions. In this case, the filter() method will run the for loop and push elements into a new array. The callback function provides the condition for whether or not the element should pass to that new array. The problem is broken up into smaller functions leaving a cleaner and more concise codebase.

Because functions are values, we can also rewrite this solution by passing a variable to the filter() method vs a full anonymous function:

```javascript
const isDog = animal => animal.species === 'dogs';

const dogs = animals.filter(isDog);
```

This example would operate in the same way as the previous example, but we broke the problem down even further. We can now utilize the ```isDog``` variable in other cases and not just the filter() method. An example could be as simple as us wanting all animals that are not dogs. In that case we could write the same thing, but precede the logical not operator (!) before ```isDog``` like so:

```javascript
const notDogs = animals.filter(!isDog);
```

One more example of an Array.prototype method that is similar to filter() is the find() method. Find will operate similarly to filter, but it will only return the first element it finds that meet the provided condition. If we wanted to find the animal named 'Caro', we could do that like so:

```javascript
const caro = animals.find(animal => animal.name === 'Caro');
```

The benefit to all of this is the ability to divide code into small, simple functions and compose them together using higher-order functions. Small, simple functions are easy to test, easy to debug, and they take less time to reason about and write.

## Quiz Yourself ##

1. Functions are not values. True or false.
> False. Functions are values in the way that numbers or strings are values.

2. Describe *higher-order functions*.
> A higher-order function is a function that takes other functions as arguments.

3. Functions that are supplied to higher-order functions as arguments are commonly referred to as what?
> They are referred to as *callback functions*.

4. Describe how the filter() method on the Array.prototype works.
> The filter() method is meant to return a new array of elements that pass a condition provided by a callback function. The method takes a callback function as an argument. That callback function takes the individual element as an argument. The callback function should return ```true``` or ```false``` to determine in the element has met the condition.

5. What is the difference between filter() and find() on the Array.prototype?
> The filter() method will return a new array of all elements that pass a specified condition. The find() method will only return the first element it finds that meets the specified condition.

5. Describe the benefits of higher-order functions.
> Higher-order functions provide us with the ability to divide code into small, simple functions and compose them together. Small, simple functions are easy to test, easy to debug, and they take less time to reason about and write.

Source: https://www.youtube.com/watch?v=BMUiFMZr7vk
