# Logical Operators

## Learning Goals

* Describe how to use `!` to negate an expression
* Describe how to convert an expression to a Boolean using `!!`
* Define the `&&` and `||` operators
* Describe how to link conditions using the `&&` and `||` operators

## Introduction

In this lesson, we will continue to expand our toolset for creating Boolean
expressions by learning about logical operators. Using JavaScript's three
logical operators, NOT (`!`), AND (`&&`), and OR (`||`), we'll learn how to
negate and combine expressions. These operators, in combination with the
equality and relational operators we learned earlier, will enable us to create
more complex and sophisticated Boolean expressions.

## Describe How to Use `!` to Negate an Expression

### `!` NOT

In an earlier lesson, we learned about truthy and falsey values in JavaScript.
The logical NOT operator (`!`), also called the _bang operator_, operates on an
expression, returning the opposite of the expression's truthiness. If `x`
resolves to a truthy value, `!x` returns `false`. If `x` is falsey, `!x` returns
`true`:

```js
const truthyValue = 'This value is truthy.';

!truthyValue;
// => false

const falseyValue = 0;

!falseyValue;
// => true
```

## Describe How to Convert an Expression to a Boolean Using `!!`

### `!!`

In an earlier lesson, we passed values into the `Boolean()` _constructor
function_ to check their truthiness. We'll learn all about constructor functions
later in the course; for now, just think of `Boolean()` as a function that takes
in some input, creates a new Boolean from that input, and outputs the created
Boolean.

As a shorter way to convert any value into a Boolean, we can use two NOT
operators:

```js
const truthyValue = 'This value is truthy.';

!truthyValue;
// => false

!!truthyValue;
// => true
```

The JavaScript engine reads from left to right: it sees the first `!` and looks
to the right to check what we're asking it to invert (`!truthyValue`). It then
sees the second `!` and looks to the right _again_, this time finding our
`truthyValue` variable. At this point, the engine resolves `truthyValue` to
`"This value is truthy."`, which (as it tells us) is truthy. It then executes
the inner `!` operator on it. `!truthyValue` returns `false`, so instead of
`!!truthyValue` JavaScript is now evaluating `!false`. Executing the outer `!`
operator on `false` returns `true`.

Try inverting various values in [repl.it](https://repl.it/languages/javascript)
to get a feel for the NOT operator. See what happens when you stack a ton of
them: `!!!!!!!!!truthyValue`.

On to the next!

## Define the `&&` and `||` Operators

### `&&` AND

The logical AND (`&&`) operator takes two expressions:

```js
expression1 && expression2;
```

The return value of the `&&` operator is always **one of the two expressions**.
If the first expression is falsey, `&&` returns the value of the first
expression. If the first expression is truthy, `&&` returns the value of the
second expression.

Again, if the first expression is falsey, `&&` returns that value and exits
_without ever checking the second expression_:

```js
false && 'Anything';
// => false

// 4 * 0 returns 0, which is falsey
4 * 0 && 'Anything';
// => 0
```

If the first expression is truthy, `&&` then returns whatever the second
expression evaluates to:

```js
true && false;
// => false

1 + 1 && 'Whatever';
// => "Whatever"

'The truthiest of truthy strings' && 9 * 9;
// => 81
```

There are three different ways the `&&` operator can be evaluated:

| Left side | Right side     | Return value | Truthiness of return value |
| --------- | -------------- | ------------ | -------------------------- |
| Falsey    | Doesn't matter | Left side    | Falsey                     |
| Truthy    | Falsey         | Right side   | Falsey                     |
| Truthy    | Truthy         | Right side   | Truthy                     |

1. If the left-side expression is falsey, the right-side expression doesn't
   matter at all. The `&&` operator returns the left side's falsey value and
   finishes.
2. If the left-side expression is truthy, the `&&` operator returns the right
   side's value (whether it's truthy or falsey) and finishes.

What this means is that the return value of the expression will be truthy if the
values on either side of the `&&` are *both* truthy, and falsey otherwise.

If you're feeling a little confused, that's ok. This is one of those concepts
that's a bit hard to understand unless you've played around with it in code so
make sure you're testing all of these new operators out in
[repl.it](https://repl.it/languages/javascript) to get a feel for how they work.

### `||` OR

The logical OR (`||`) operator also takes two expressions:

```js
expression1 || expression2;
```

As with `&&`, the return value of the `||` operator is always **one of the two
expressions**. If the first expression is truthy, `||` returns the value of the
first expression. If the first expression is falsey, `||` returns the value of
the second expression.

If the first expression is truthy, that value is immediately returned and the
second expression is never evaluated:

```js
true || 'Whatever';
// => true

1 + 1 || 'Whatever';
// => 2
```

If the first expression is falsey, `||` returns whatever the second expression
evaluates to:

```js
false || 'Whatever';
// => "Whatever"

1 === 2 || 8 * 8;
// => 64

'' || 'Not ' + 'an ' + 'empty ' + 'string';
// => "Not an empty string"
```

There are three different ways the `||` operator can be evaluated:

| Left side | Right side     | Return value | Truthiness of return value |
| --------- | -------------- | ------------ | -------------------------- |
| Truthy    | Doesn't matter | Left side    | Truthy                     |
| Falsey    | Truthy         | Right side   | Truthy                     |
| Falsey    | Falsey         | Right side   | Falsey                     |

1. If the left-side expression is truthy, the right-side expression doesn't
   matter at all. The `||` operator returns the left side's truthy value and
   completes.
2. If the left-side expression is falsey, the `||` operator returns the right
   side's value (regardless of whether it's truthy or falsey) and completes.

What this means is that the return value of the expression will be truthy if
*one or both* of the values on either side of the `||` are truthy, and falsey
otherwise.

Again, make sure you test out all of these outcomes for yourself to get the hang
of them!

## Conclusion

In the last few lessons, we've been introduced to powerful tools for creating
Boolean expressions: comparison operators (equality and relational) and logical
operators. With these tools, we can construct very sophisticated expressions. A
bit later in the course, we will learn how to use these expressions to execute
code conditionally, which will enable us to implement powerful logic in our
programs.

## Resources

* MDN
* [Logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)
* [Review of conditionals, comparisons, and logical operators](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals)
