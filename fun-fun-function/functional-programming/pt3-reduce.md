# Part 3: Reduce #

The reduce() method on the Array.prototype can be used to implement any kind of list transformation. It's used if none of the preexisting transformation methods, i.e. map(), filter(), etc, will find your needs.

Let's start with an array of orders:

```javascript
const orders = [
	{ amount: 250 },
	{ amount: 400 },
	{ amount: 100 },
	{ amount: 325 }
];
```

Now let's say we want to get back the total of all the orders. One solution would be to utilize a for loop like so:

```javascript
let totalAmount = 0;
for (var i = 0; i < orders.length; i++) {
	totalAmount += orders[i].amount;
}
```

Now let's rewrite this using the reduce() method:

```javascript
const totalAmount = orders.reduce((sum, order) => sum + order.amount, 0);
```

This is different from every other array method we've used so far, so let's review those differences. The first difference is the callback function takes two arguments: an *accumulator* and the individual element we've looped to. The second difference is the that the reduce() method itself also takes two arguments: the first being the aforementioned callback function and the second being the initial value of your accumulator. As the array is looped through, the accumulator will change in value based on what you return. In our example, the accumulator is continually being set to itself plus the value of the next order.

## Quiz Yourself ##

1. Describe how the reduce() method on the Array.prototype works.
> The reduce() method is used for more complex transformations that aren't possible with other Array.prototype methods. The reduce() method takes two arguments: a callback function (standard) and an initial value for an accumulator. The callback function takes two arguments as well: the accumulator (which on its first iteration is set to the initial value you provided) and the current element in the array. The callback function is intended to return a new value for the accumulator to be used in the next iteration.

Source: https://www.youtube.com/watch?v=Wl98eZpkp-c
