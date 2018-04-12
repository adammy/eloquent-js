# Part 2: Map #

The map() method on the Array.prototype is used to transform every element in the array and return a new array.

Let's start with an array of animals because animals are common in enterprise-level software:

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

Now let's say we want to only get back the names of the animals. One solution would be to utilize a for loop like so:

```javascript
let names = [];
for (var i = 0; i < animals.length; i++) {
	names.push(animals[i].name);
}
```

Now let's rewrite this using the map() method:

```javascript
const names = animals.map(animal => animal.name);
```

The map() method accomplishes the same thing as a traditional for loop, but abstracts away the need for a for loop and pushing to a new array.


## Quiz Yourself ##

1. Describe how the map() method on the Array.prototype works.
> The map() method is used to transform every element in the array and return a new array. This transformation of each element happens through a callback function that is provided as an argument. That callback function takes the individual element as an argument.

2. What's the difference between the map() and forEach() method on the Array.prototype?
> The map() method is intended to transform every element and return a completely new array. The forEach() method just loops through every element and does what you specify. The map() method is a *pure function* in that is should not cause *side effects*, whereas the forEach() method is typically used specifically to cause side effects.

Source: https://www.youtube.com/watch?v=bCqtb-Z5YGQ
