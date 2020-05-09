---
id: 5eb71b99c576aa2b608c4905
title: Find the missing permutation
challengeType: 5
---

## Description
<section id='description'>
A permutation of a set is an ordered arrangement of the set's elements. All the permutations of a set is all the possible arrangements of those elements.
For example, the string (a set of characters) "ABC" has the permutations "ABC", "ACB", "BAC", "BCA", "CAB", and "CBA".
</section>

## Instructions
<section id='instructions'>
Write a function that takes a string and an array as parameters. The array contains some of the permutations of the string.
The function should return the missing permutations.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>permute</code> should be a function.
    testString: assert(typeof permute == "function");
  - text: <code>permute('AB',['AB'])</code> return an array.
    testString: assert(Array.isArray(permute('AB',tests[0].slice())));
  - text: <code>permute('AB',['AB'])</code> should return <code>['BA']</code>.
    testString: assert.deepEqual(permute('AB',tests[0].slice()),results[0]);
  - text: <code>permute('AB',['BA'])</code> should return <code>['AB']</code>.
    testString: assert.deepEqual(permute('AB',tests[1].slice()),results[1]);
  - text: <code>permute('ABC',['BAC', 'CAB', 'CBA'])</code> should return <code>['ABC', 'ACB', 'BCA']</code>.
    testString: assert.deepEqual(permute('ABC',tests[2].slice()),results[2]);
  - text: <code>permute('ABC',['ABC', 'BCA'])</code> should return <code>['ACB', 'BAC', 'CAB', 'CBA']</code>.
    testString: assert.deepEqual(permute('ABC',tests[3].slice()),results[3]);
  - text: <code>permute('ABCD',['ABDC','ADBC','BADC','BACD','ABCD', 'CABD', 'ACDB', 'DACB', 'BCDA', 'ACBD', 'ADCB', 'CDAB'])</code> should return <code>['BCAD','BDCA','BDAC','CADB','CBAD','CBDA','CDBA','DABC','DBCA','DBAC','DCBA','DCAB']</code>.
    testString: assert.deepEqual(permute('ABCD',tests[4].slice()),results[4]);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function permute (str, perms) {
  // Good luck!
}

```

</div>

### After Test

<div id='js-teardown'>

```js
const tests=[
  ['AB'],
  ['BA'],
  [ 'BAC', 'CAB', 'CBA' ],
  [ 'ABC', 'BCA' ],
  [ 'ABDC','ADBC','BADC','BACD','ABCD', 'CABD', 'ACDB', 'DACB', 'BCDA', 'ACBD', 'ADCB', 'CDAB']
];

const results=[
  ['BA'],
  ['AB'],
  [ 'ABC', 'ACB', 'BCA' ],
  [ 'ACB', 'BAC', 'CAB', 'CBA' ],
  [ 'BCAD','BDCA','BDAC','CADB','CBAD','CBDA','CDBA','DABC','DBCA','DBAC','DCBA','DCAB' ]
];


```

</div>

</section>

## Solution
<section id='solution'>


```js
function permute(str,perms){
  var x,v=str;
    for(var p = -1, j, k, f, r, l = v.length, q = 1, i = l + 1; --i; q *= i);
    for(x = [new Array(l), new Array(l), new Array(l), new Array(l)], j = q, k = l + 1, i = -1;
        ++i < l; x[2][i] = i, x[1][i] = x[0][i] = j /= --k);
    for(r = new Array(q); ++p < q;)
        for(r[p] = new Array(l), i = -1; ++i < l; !--x[1][i] && (x[1][i] = x[0][i],
            x[2][i] = (x[2][i] + 1) % l), r[p][i] = 0 ? x[3][i] : v[x[3][i]])
            for(x[3][i] = x[2][i], f = 0; !f; f = !f)
                for(j = i; j; x[3][--j] == x[2][i] && (x[3][i] = x[2][i] = (x[2][i] + 1) % l, f = 1));

    var all = r.map(function(elem) {return elem.join('')});

    var missing = all.filter(function(elem) {return perms.indexOf(elem) == -1});
    return missing;
};

```

</section>
