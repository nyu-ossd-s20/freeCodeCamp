---
id: 5ed539cad85cad123bbaf6fb
title: Forward difference
challengeType: 5
---

## Description
<section id='description'>
The first-order forward difference of a list of numbers <strong>A</strong> is a new list  <strong>B</strong>, where <strong>B<sub>n</sub> = A<sub>n+1</sub> - A<sub>n</sub></strong>.
The goal of this challenge is to repeat this process up to the desired order.
</section>

## Instructions
<section id='instructions'>
Write a function that produces a list of numbers which is the  <strong>n<sup>th</sup></strong> order forward difference, given a non-negative integer (specifying the order) and a list of numbers.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>forwardDifference</code> should be a function.
    testString: assert(typeof forwardDifference=='function');
  - text: <code>forwardDifference()</code> should return a array.
    testString: assert(Array.isArray(forwardDifference(1,tests[0])));
  - text: <code>forwardDifference(1, [90, 47, 58, 29, 22])</code> should return <code>[-43, 11, -29, -7]</code>.
    testString: assert.deepEqual(forwardDifference(1,tests[0]),results[0]);
  - text: <code>forwardDifference(1, [32, 55, 5, 55, 7])</code> should return <code>[23, -50, 50, -48]</code>.
    testString: assert.deepEqual(forwardDifference(1,tests[1]),results[1]);
  - text: <code>forwardDifference(2, [33, 11, 65, 22, 51, 86])</code> should return <code>[76, -97, 72, 6]</code>.
    testString: assert.deepEqual(forwardDifference(2,tests[2]),results[2]);
  - text: <code>forwardDifference(2, [43, 12, 45, 89, 34, 14, 63])</code> should return <code>[64, 11, -99, 35, 69]</code>.
    testString: assert.deepEqual(forwardDifference(2,tests[3]),results[3]);
  - text: <code>forwardDifference(3, [12, 43, 67, 13, 46, 56, 87])</code> should return <code>[-71, 165, -110, 44]</code>.
    testString: assert.deepEqual(forwardDifference(3,tests[4]),results[4]);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function forwardDifference(n, xs) {
  // Good luck!
}

```

</div>

### After Test

<div id='js-teardown'>

```js
const tests = [[90, 47, 58, 29, 22],
              [32, 55, 5, 55, 7],
              [33, 11, 65, 22, 51, 86],
              [43, 12, 45, 89, 34, 14, 63],
              [12, 43, 67, 13, 46, 56, 87]];

const results = [[-43, 11, -29, -7],
                [23, -50, 50, -48],
                [76, -97, 72, 6],
                [64, 11, -99, 35, 69],
                [-71, 165, -110, 44]];

```

</div>

</section>

## Solution
<section id='solution'>


```js
function forwardDifference(n, xs) {
  for (var i = 0; i < n; i++) {
    xs = xs.map( function (e,i) {
      if (i == 0) {
        return 0;
      } else {
        return e - xs[i-1];
      }
    });
    xs.shift();
  }
  return xs;
}

```

</section>
