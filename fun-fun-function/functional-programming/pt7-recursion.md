# Part 7: Recursion #

Recursion is quite simply a function that calls itself... until it doesn't by meeting some *base case*.

Let's write an example of recursion that counts down from ten:

```javascript
const countDownFrom = num => {
	console.log(num);
	return countDownFrom(--num);
}

countDownFrom(10);
```

This will count down, but there's a problem with this. This recursive function will not stop. I will go on forever until you overload the *call stack*, which is basically a list of the subroutines (i.e. functions) that are executing. In order to address this, we provide this recursive function with a *base case* like so:

```javascript
const countDownFrom = num => {
	console.log(num);
	if (num === 0) return;
	return countDownFrom(--num);
}

countDownFrom(10);
```

This will look to see if the num value gets to zero and it will then stop calling itself.

Random I wanted to feel cool moment: this can also be written as a one liner using a *ternary operator* like so:

```javascript
const countDownFrom = num => (num === 0) ? null : countDownFrom(--num);
```

Now this problem can normally be solved with a for loop; and it should. Recursion can mimic a for loop in a way, but in some instances, a for loop can't mimic the power of recursion. Example:

```javascript
const categories = [
	{
		id: 'animals',
		parent: null
	},
	{
		id: 'mammals',
		parent: 'animals'
	},
	{
		id: 'cats',
		parent: 'mammals'
	},
	{
		id: 'dogs',
		parent: 'mammals'
	},
	{
		id: 'chihuahua',
		parent: 'dogs'
	},
	{
		id: 'labrador',
		parent: 'dogs'
	},
	{
		id: 'persian',
		parent: 'cats'
	},
	{
		id: 'siamese',
		parent: 'cats'
	}
];

const makeTree = (categories, parent) => {
	let node = {};

	categories
		.filter(c => c.parent === parent)
		.forEach(c => node[c.id] = makeTree(categories, c.id));

	return node;
}
```

This example will return a tree like structure of the categories; nesting them when there is a parent property.

## Quiz Yourself ##

1. Describe what recursion is.
> Recursion is quite simply a function that calls itself... until it doesn't by meeting some *base case*.

2. Describe a practical example of recursion.

Source: https://www.youtube.com/watch?v=k7-N8R0-KY4
