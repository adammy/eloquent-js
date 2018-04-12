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

The ```var``` keyword is the way bindings were declared in pre-2015 JavaScript. Going forward, using ```let``` and ```const``` is preferred, but it's still good to know the quirks of ```var``` for legacy code.

```var``` and ```let``` are used to declare bindings that can be assigned and/or reassigned at a later point. ```var``` has *function scope*, while ```let``` has *block scope*. More about this in the next chapter.

```const``` is used to declare a binding that has a *constant* value. This means that its value must be set upon initialization and that the value cannot be changed.

## Binding Names ##

Binding names can be any word. Digits can be a part of a binding name, but the name cannot start with a digit. Binding names can include dollar signs ($) and underscores (_), but no other special character is allowed.

*Keywords* are words in the programming language that have special meaning, including ```let```, ```const```, or ```for```. Keywords cannot be used for binding names.

Examples of appropriately-declared binding names below:

```javascript
const name = 'Adam MacDonald';
const firstName = 'Adam';
const age = 25;
let greeting1 = 'hello';
let greeting2 = 'awesome sauce';
```

## The Environment ##

The collection of bindings and their values that exist at a given time is called the *environment*. An in-depth example of an environment could be a browser. The browser has functions to interact with the currently-loaded website, to read mouse input, etc. It also has bindings and functions that you have initialized.

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
