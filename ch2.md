# Chapter 2: Program Structure #

We start doing things that can actually be called *programming*. We've only used fragments, but we will start to express meaningful prose.

## Expressions and Statements ##

A fragment of code that produces a value is called an *expression*. Every value that is written literally, such as ```22``` or ```'hello'``` is an expression. An expression can also be other expressions between parenthesis or a binary operator between two expressions, such as ```5 + 1```.

If an expression corresponds to a sentence fragment, a JavaScript *statement* corresponds to a full sentence. A program is a list of statements. The simplest kind of program is an expressions with a semicolon after it, like so:

```javascript
1;
```

## Bindings ##

In order to catch/hold values that can represent program state, we use a thing called a *binding* or *variable*.

A binding points to a value, but that doesn't not mean it's tied to that value forever. The = operator can be used to reassign a bindings value.

Bindings can be made in JavaScript using three keywords, all with their own unique properties: ```var```, ```let```, and ```const```. Example below:

```javascript
var name = 'Adam';
let age = 25;
const awesome = true;
```

Imagine bindings as tentacles, rather than boxes. They do not contain values, but that they grasp them. This means that two bindings can refer to the same value.

## Binding Names ##

## The Environment ##

## Functions ##

## The console.log Function ##

## Return Values ##

## Control Flow ##

## Conditional Execution ##

## While and Do Loops ##

## Indenting Code ##

## For Loops ##

## Breaking Out of a Loop ##

## Updating Bindings Succinctly ##

## Dispatching on a Value with Switch ##

## Capitalization ##

## Comments ##

## Summary ##

## Exercises ##

### Looping a Triangle ###

### FizzBuzz ###

### Chess Board ###

## Quiz Yourself

1. Express the number 45 in binary.
> 00101101

2. Describe *garbage collection*.
> Garbage collection is a form of automatic memory management that abstracts that complexity away from the developer. In this process, values that are no longer needed are automatically thrown out and the bits that represented that value can be used for something else.
