---
id: 5eb5c7a6af8fe8847aa0b25d
title: Find largest left truncatable prime in a given base
challengeType: 5
---

## Description
<section id='description'>
A <a href = "http://rosettacode.org/wiki/Truncatable_primes" target = "_blank">truncatable prime</a> is one where all non-empty substrings that finish at the end of the number (right-substrings) are also primes <em>when understood as numbers in a particular base</em>. The largest such prime in a given (integer) base is therefore computable, provided the base is larger than 2.
</section>

## Instructions
<section id='instructions'>
Write a function that takes radix/base as parameter and returns the largest left trunctable prime for the given radix/base.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>getLargestLeftTruncPrime</code> should be a function.
    testString: assert(typeof getLargestLeftTruncPrime == 'function');
  - text: <code>getLargestLeftTruncPrime(3)</code> should return a number.
    testString: assert(typeof getLargestLeftTruncPrime(3) == 'number');
  - text: <code>getLargestLeftTruncPrime(3)</code> should return <code>23</code>.
    testString: assert.equal(getLargestLeftTruncPrime(tests[0]),results[0]);
  - text: <code>getLargestLeftTruncPrime(4)</code> should return <code>4091</code>.
    testString: assert.equal(getLargestLeftTruncPrime(tests[1]),results[1]);
  - text: <code>getLargestLeftTruncPrime(5)</code> should return <code>7817</code>.
    testString: assert.equal(getLargestLeftTruncPrime(tests[2]),results[2]);
  - text: <code>getLargestLeftTruncPrime(6)</code> should return <code>4836525320399</code>.
    testString: assert.equal(getLargestLeftTruncPrime(tests[3]),results[3]);
  - text: <code>getLargestLeftTruncPrime(8)</code> should return <code>14005650767869</code>.
    testString: assert.equal(getLargestLeftTruncPrime(tests[4]),results[4]);


```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function getLargestLeftTruncPrime(radix) {
  // Good luck!
}

```

</div>

### After Test

<div id='js-teardown'>

```js
let tests = [3,4,5,6,8];
let results = [23,4091,7817,4836525320399,14005650767869];

```

</div>

</section>

## Solution
<section id='solution'>


```js
function getLargestLeftTruncPrime(radix) {

  function isPrime(n) {
    if (n < 2) return false;
    if (n == 2 || n == 3) return true;
    if (n%2 == 0 || n%3 == 0) return false;
    var sqrtN = Math.sqrt(n) + 1;
    for (var i = 6; i <= sqrtN; i += 6) {
      if (n % (i - 1) == 0 || n % (i + 1) == 0) return false;
    }
    return true;
  }

  function getNextLeftTruncatablePrimes(n, radix) {
    var probablePrimes = [];
    var baseString = (n == 0) ? "" : n.toString(radix);
    for (var i = 1; i < radix; i++) {
      var p = parseInt(i.toString(radix) + baseString, radix);
      if (isPrime(p)) {
        probablePrimes.push(p);
      }
    }
    return probablePrimes;
  }

  var lastList = null;
  var list = getNextLeftTruncatablePrimes(0, radix);
  while (list.length != 0) {
    lastList = list;
    list = [];
    lastList.forEach(function(n) {
      list.push.apply(list,getNextLeftTruncatablePrimes(n, radix));
    });
  }
  if (lastList == null) {
    return null;
  }
  lastList.sort();
  return lastList[lastList.length - 1];
}

```

</section>
