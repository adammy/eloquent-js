# Part 4: Advanced Reduce #

The reduce() method on the Array.prototype can be used for more complex implementations than just getting a sum of numbers. We can use it to make new arrays or objects.

Our task to explore a more complex implementation of the reduce() method will be to take a text file that is a tab-delimited list and convert it to an object. The list will look like this:

```
mark johansson	waffle iron	80	2
mark johansson	blender	200	1
mark johansson	knife	10	4
Nikita Smith	waffle icon	80	1
Nikita Smith	knife	10	2
Nikita Smith	pot	20	3
```

And the object we want to create from this list will look like this:

```javascript
{
	'mark johansson': [
		{
			name: 'waffle iron',
			price: '80',
			quantity: '2'
		},
		{
			name: 'blender',
			price: '200',
			quantity: '1'
		},
		{
			name: 'knife',
			price: '10',
			quantity: '4'
		}
	],
	'Nikita Smith': [
		{
			name: 'waffle iron',
			price: '80',
			quantity: '1'
		},
		{
			name: 'knife',
			price: '10',
			quantity: '2'
		},
		{
			name: 'pot',
			price: '20',
			quantity: '3'
		}
	]
}
```

We'll start by getting the contents of this file using the fs module (heads up we're using a node environment):

```javascript
import fs from 'fs';

const output = fs.readFileSync('data.txt', 'utf8');

console.log(output);
```

Now we'll use the trim() method on the String.prototype to remove whitespace and we'll use the split() method on the String.prototype to convert each new line instance into a new element of an array:

```javascript
import fs from 'fs';

const output = fs.readFileSync('data.txt', 'utf8')
	.trim()
	.split('\n');

console.log(output);
```

Next, we'll map through that array and use the split() method again, but this time on tabs. This will give use a nested array to work with:

```javascript
import fs from 'fs';

const output = fs.readFileSync('data.txt', 'utf8')
	.trim()
	.split('\n')
	.map(line => line.split('\t'));

console.log(output);
```

Now to use reduce():

```javascript
import fs from 'fs';

const output = fs.readFileSync('data.txt', 'utf8')
	.trim()
	.split('\n')
	.map(line => line.split('\t'))
	.reduce((customers, line) => {
		customers[line[0]] = customers[line[0]] || [];
		customers[line[0]].push({
			name: line[1],
			price: line[2],
			quantity: line[3]
		});
		return customers;
	}, {});

console.log(output);
```

In this example, we set the accumulator to an empty object literal. From there, we add a property that is the person's name. We set that property to itself (if it already exists) or an empty array. From there, we push a new object in the array with the name, price, and quantity properties being set. Finally, we return the accumulator to get the next element added to it.

## Quiz Yourself ##

1. Describe how the reduce() method on the Array.prototype works.
> The reduce() method is used for more complex transformations that aren't possible with other Array.prototype methods. The reduce() method takes two arguments: a callback function (standard) and an initial value for an accumulator. The callback function takes two arguments as well: the accumulator (which on its first iteration is set to the initial value you provided) and the current element in the array. The callback function is intended to return a new value for the accumulator to be used in the next iteration.

Source: https://www.youtube.com/watch?v=1DMolJ2FrNY
