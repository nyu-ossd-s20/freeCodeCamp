---
id: 5ebf1cc40200128fa50561c5
title: Find the last Sunday of given month
challengeType: 5
---

## Description
<section id='description'>

</section>

## Instructions
<section id='instructions'>
Write a function that returns the date of the last Sunday of a given month of a given year. The month and year are the parameters of the function. The date should be returned as a string in the format 'yyyy-mm-dd'.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>lastSundayOfMonth </code> is a function.
    testString: assert(typeof lastSundayOfMonth === 'function');
  - text: <code>lastSundayOfMonth(6, 2013)</code> should return a <code>string</code>.
    testString: assert(typeof lastSundayOfMonth(6, 2013) === 'string');
  - text: <code>lastSundayOfMonth(6,2013)</code> should return <code>2013-06-30</code>.
    testString: assert.equal(lastSundayOfMonth(6, 2013), '2013-06-30');
  - text: <code>lastSundayOfMonth(2,2013)</code> should return <code>2013-02-24</code>.
    testString: assert.equal(lastSundayOfMonth(2, 2013), '2013-02-24');
  - text: <code>lastSundayOfMonth(9,1999)</code> should return <code>1999-09-26</code>.
    testString: assert.equal(lastSundayOfMonth(9, 1999), '1999-09-26');
  - text: <code>lastSundayOfMonth(12,2010)</code> should return <code>2010-12-26</code>.
    testString: assert.equal(lastSundayOfMonth(12, 2010), '2010-12-26');
  - text: <code>lastSundayOfMonth(11,2005)</code> should return <code>2005-11-27</code>.
    testString: assert.equal(lastSundayOfMonth(11, 2005), '2005-11-27');

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function lastSundayOfMonth (month, year) {
  // Good luck!
}

```

</div>

</section>

## Solution
<section id='solution'>


```js
function lastSundayOfMonth(month, year) {
  const lastDay = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
  const dates = [];

  if (year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0)) lastDay[1] = 29;
  const date = new Date(Date.UTC());
  date.setUTCFullYear(year, month - 1, lastDay[month - 1]);
  date.setUTCDate(date.getUTCDate() - date.getUTCDay());
  return date.toISOString().substring(0, 10);
}

```

</section>
