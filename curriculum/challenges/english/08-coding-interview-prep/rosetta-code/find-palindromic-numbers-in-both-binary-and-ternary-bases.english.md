---
id: 5eb6f8171cb818c994468b19
title: Find palindromic numbers in both binary and ternary bases
challengeType: 5
---

## Description

<section id='description'>
A palindrome is a phrase or a sequence of numbers that is the same forwards and backwards. Examples include "racecar" and 1001.
<a href="https://oeis.org/A060792" target="_blank">Sequence A060792</a> of the Online Encyclopedia of Integer Sequences describes numbers that are palindromic in <em>both</em> base 2 and base 3. For example, 6443 is 1100111110011 in base 2 and 100010001 in base 3, making it palindromic in both bases.
</section>

## Instructions

<section id='instructions'>
Write a function that returns the first five numbers (non-negative integers) that are palindromes in both base 2 and base 3.
Use zero (0) as the first number found, even though some other definitions ignore it.
The function should return the decimal form of the numbers as an array.
</section>

## Tests

<section id='tests'>

```yml
tests:
  - text: <code>binTernPalin</code> should be a function.
    testString: assert(typeof binTernPalin == 'function');
  - text: <code>binTernPalin()</code> should return an Array.
    testString: assert(Array.isArray(binTernPalin()));
  - text: <code>binTernPalin()</code> should return <code>[0, 1, 6643, 1422773, 5415589]</code>.
    testString: assert.deepEqual(binTernPalin(),[0, 1, 6643, 1422773, 5415589]);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function binTernPalin() {
  // Good luck!
}

```

</div>

</section>

## Solution

<section id='solution'>

```js
function binTernPalin(){
    // GENERIC FUNCTIONS
    // range :: Int -> Int -> [Int]

    const range = (m, n) =>

        Array.from({

            length: Math.floor(n - m) + 1

        }, (_, i) => m + i);


    // compose :: (b -> c) -> (a -> b) -> (a -> c)

    const compose = (f, g) => x => f(g(x));

    // reverse :: [a] -> [a]

    const reverse = xs =>

        typeof xs === 'string' ? (

            xs.split('')

            .reverse()

            .join('')

        ) : xs.slice(0)

        .reverse();


    // take :: Int -> [a] -> [a]

    const take = (n, xs) => xs.slice(0, n);


    // drop :: Int -> [a] -> [a]

    const drop = (n, xs) => xs.slice(n);


    // quotRem :: Integral a => a -> a -> (a, a)

    const quotRem = (m, n) => [Math.floor(m / n), m % n];


    // length :: [a] -> Int

    const length = xs => xs.length;

    // BASES AND PALINDROMES

    // show, showBinary, showTernary :: Int -> String

    const show = n => n.toString(10);

    const showBinary = n => n.toString(2);

    const showTernary = n => n.toString(3);


    // readBase3 :: String -> Int

    const readBase3 = s => parseInt(s, 3);


    // base3Palindrome :: Int -> String

    const base3Palindrome = n => {

        const s = showTernary(n);

        return s + '1' + reverse(s);

    };


    // isBinPal :: Int -> Bool

    const isBinPal = n => {

        const

            s = showBinary(n),

            [q, r] = quotRem(s.length, 2);

        return (r !== 0) && drop(q + 1, s) === reverse(take(q, s));

    };


    // solutions :: [Int]

    const solutions = [0, 1].concat(range(1, 50000)

        .map(compose(readBase3, base3Palindrome))

        .filter(isBinPal));


    return solutions;
}

```

</section>
