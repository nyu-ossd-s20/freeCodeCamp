---
id: 5ec01a3f380e86eaad4d1513
title: Formatted numeric output
challengeType: 5
---

## Description
<section id='description'>
Express a number in decimal as a fixed-length string with leading zeros.
For example, the number <strong>7125</strong> could be expressed as <strong>00007125</strong>. Here, the number is 7125 and the fixed length is 8.</p>
</section>

## Instructions
<section id='instructions'>
Write a function that takes the fixed length and the number as the parameters. The function should return the appropriate string.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>format</code> should be a function.
    testString: assert(typeof format=='function');
  - text: <code>format(33,5)</code> should return a string.
    testString: assert(typeof format(33,5)=='string');
  - text: <code>format(33,5)</code> should return <code>"00033"</code>.
    testString: assert.equal(format(33,5),'00033');
  - text: <code>format(123,5)</code> should return <code>"00000123"</code>.
    testString: assert.equal(format(123,8),'00000123');
  - text: <code>format(2044,4)</code> should return <code>"2044"</code>.
    testString: assert.equal(format(2044,4),'2044');
  - text: <code>format(2044,8)</code> should return <code>"00002044"</code>.
    testString: assert.equal(format(2044,8),'00002044');
  - text: <code>format(336544,10)</code> should return <code>"0000336544"</code>.
    testString: assert.equal(format(336544,10),'0000336544');

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function format(n, num) {
  // Good luck!
}

```

</div>

</section>

## Solution
<section id='solution'>


```js
function format(n,num) {
  return ("00000000000000000000" + n).slice(-num);
}

```

</section>
