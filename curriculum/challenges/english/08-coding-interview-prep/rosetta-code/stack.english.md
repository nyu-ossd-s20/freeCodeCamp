---
title: Stack
id: 5ea9c709645b540cb1a764a3
challengeType: 5
---

## Description
<section id='description'>
A <b>stack</b> is a container of elements with a <i>last in frist out</i> (LIFO) access policy.<br />

The stack is accessed through its <b>top</b><br />

The basic stack operations are: 
<ul>
    <li> <i> push </i> stores a new element onto the stack top; </li>
    <li> <i> pop </i> returns the last pushed stack element, while removign it from the stack; </li>
    <li> <i> empty </i> tests if the stack contains no elements </li>
    <p>Sometimes the last pushed stack element is made accessible for immutable access (for read) or mutuable access (for write): </p><br />
    <li> <i> top </i> (sometimes called peek to keep with the p theme) returns the topmost element without modifying the stack. </li>
</ul>
Stacks allow a very simple hardware implementation. <br />
They are common in almost all processors. <br />
In programming, stacks are also very popular popular for their way (<b>LIFO</b>) of resource management, usually memory. <br />
Nested scopes of language objects are naturally implemented by a stack (sometimes by multiple stacks). <br />
This is a classical way to implement local variables of a re-entrant of recursive subprogram. Stacks are also used to describe a formal computational framework. <br />

See <a href='https://en.wikipedia.org/wiki/Pushdown_automaton#Stack_automaton'>stack machine.</a><br />

Many algorithms in pattern matching, compiler construction (e.g <a href='https://en.wikipedia.org/wiki/Recursive_descent_parser'>recursive descent parsers</a>), and machine learning (e.g based on <a href='https://en.wikipedia.org/wiki/Tree_traversal'> tree traversal </a>) have a natural representation in terms of stacks. 

</section>

## Instructions
<section id='instructions'>

Create a stack supporting the basic operations: push, pop, empty.

</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>genFizzBuzz</code> should be a function.
    testString: assert(typeof genFizzBuzz=='function');
  - text: <code>genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 6)</code> should return a string.
    testString: assert(typeof genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 6)=='string');
  - text: <code>genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 6)</code> should return <code>"Fizz"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 6), "Fizz");
  - text: <code>genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 10)</code> should return <code>"Buzz"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 10), "Buzz");
  - text: <code>genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 12)</code> should return <code>"Buzz"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 12), "Buzz");
  - text: <code>genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 13)</code> should return <code>"13"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 13), '13');
  - text: <code>genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 15)</code> should return <code>"BuzzFizz"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Buzz"],[5, "Fizz"]], 15), "BuzzFizz");
  - text: <code>genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 15)</code> should return <code>"FizzBuzz"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Fizz"],[5, "Buzz"]], 15), "FizzBuzz");
  - text: <code>genFizzBuzz([[3, "Fizz"],[5, "Buzz"],[7, "Baxx"]], 105)</code> should return <code>"FizzBuzzBaxx"</code>.
    testString: assert.equal(genFizzBuzz([[3, "Fizz"],[5, "Buzz"],[7, "Baxx"]], 105), "FizzBuzzBaxx");

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function genFizzBuzz(rules, num) {
  // Good luck!
}
```

</div>

</section>

## Solution
<section id='solution'>


```js
function genFizzBuzz(rules, num) {
  let res='';
  rules.forEach(function (e) {
    if(num % e[0] == 0)
      res+=e[1];
  })

  if(res==''){
    res=num.toString();
  }

  return res;
}




```

</section>


