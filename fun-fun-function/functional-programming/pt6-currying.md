# Part 6: Currying #

Currying is when a function doesn't take all of its arguments up front. Instead, it wants you to give it the first argument and then the function returns another function, which is supplied with the second argument and so on. The function at the end of this chain will return the value you actually want.

Let's start with this simple function that returns a string based on some arguments supplied:

```javascript
let dragon = (name, size, element) => `${name} is a ${size} dragon that breathes ${element}!`;

console.log(dragon('fluffykins', 'small', 'lightning'));
```

Now here is the same function using currying:

```javascript
let dragon =
	name =>
		size =>
			element =>
				`${name} is a ${size} dragon that breathes ${element}!`;

console.log(dragon('fluffykins')('small')('lightning'));
```

The idea of currying is that your function can pass through the application and gradually receive your arguments. An example where the arguments aren't supplied immediately could look something like this:

```javascript
let fluffykins = dragon('fluffykins');

console.log(fluffykins('small')('lightning'));
```

In this example, ```fluffykins``` becomes reusable and I can avoid repetition if it needs to be used again.

You can also make standard functions utilize currying if you write your own function to do so or utilize a library like lodash. See example below:

```javascript
import _ from 'lodash';

let dragon = (name, size, element) => `${name} is a ${size} dragon that breathes ${element}!`;
dragon = _.curry(dragon);

console.log(dragon('fluffykins')('small')('lightning'));
```

## Quiz Yourself ##

1. Describe what currying is.
> Currying is when a function doesn't take all of its arguments up front. Instead, it wants you to give it the first argument and then the function returns another function, which is supplied with the second argument and so on. The function at the end of this chain will return the value you actually want.

2. Describe a practical example of currying.

Source: https://www.youtube.com/watch?v=iZLP4qOwY8I
