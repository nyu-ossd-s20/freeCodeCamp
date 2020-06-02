---
id: 5ed6dbd4084ddd52c4a2fb94
title: Four bit adder
challengeType: 5
---

## Description
<section id='description'>
Simulate a four-bit adder "chip".
This "chip" can be realized using four <a href="https://en.wikipedia.org/wiki/Adder_(electronics)#Full_adder" target="_blank">1-bit full adder</a>s.</p>
Each of these 1-bit full adders can be built with two <a href="https://en.wikipedia.org/wiki/Adder_(electronics)#Half_adder" target="_blank">half adder</a>s and an <em>or</em> <a href="https://en.wikipedia.org/wiki/Logic_gate" target="_blank">gate</a>. Finally, a half adder can be made using a <em>xor</em> gate and an <em>and</em> gate.
The <em>xor</em> gate can be made using two <em>not</em>s, two <em>and</em>s and one <em>or</em>.
<strong>Not</strong>, <strong>or</strong> and <strong>and</strong>, the only allowed "gates" for the task, can be "imitated" by using the <a href="http://rosettacode.org/wiki/Bitwise_operations" target="_blank">bitwise operators.</a>
</section>

## Instructions
<section id='instructions'>
Write a function that takes two 4-bit binary numbers as strings and returns the sum as a string. The addition should to be done as stated above.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>fourBitAdder</code> should be a function.
    testString: assert(typeof fourBitAdder=='function');
  - text: <code>fourBitAdder("0000","0001")</code> should return a string.
    testString: assert(typeof fourBitAdder('0000','0001')=='string');
  - text: <code>fourBitAdder('0000', '0001')</code> should return <code>'0001'</code>.
    testString: assert.equal(fourBitAdder('0000', '0001'),'0001');
  - text: <code>fourBitAdder('1010', '0101')</code> should return <code>'1111'</code>.
    testString: assert.equal(fourBitAdder('1010', '0101'),'1111');
  - text: <code>fourBitAdder('0100', '0001')</code> should return <code>'0101'</code>.
    testString: assert.equal(fourBitAdder('0100', '0001'),'0101');
  - text: <code>fourBitAdder('0110', '0100')</code> should return <code>'1010'</code>.
    testString: assert.equal(fourBitAdder('0110', '0100'),'1010');
  - text: <code>fourBitAdder('1111', '1111')</code> should return <code>'1110'</code>.
    testString: assert.equal(fourBitAdder('1111', '1111'),'1110');

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function fourBitAdder(a, b) {
  // Good luck!
}

```

</div>

</section>

## Solution
<section id='solution'>


```js
function fourBitAdder(a, b) {
	function acceptedBinFormat(bin) {
		if (bin == 1 || bin === 0 || bin === '0')
		    return true;
		else
		    return bin;
	}

	function arePseudoBin() {
		var args = [].slice.call(arguments), len = args.length;
		while(len--)
		    if (acceptedBinFormat(args[len]) !== true)
		        throw new Error('argument must be 0, \'0\', 1, or \'1\', argument ' + len + ' was ' + args[len]);
		return true;
	}
	function not(a) {
		if (arePseudoBin(a))
		    return a == 1 ? 0 : 1;
	}

	function and(a, b) {
		if (arePseudoBin(a, b))
		    return a + b < 2 ? 0 : 1;
	}

	function nand(a, b) {
		if (arePseudoBin(a, b))
		    return not(and(a, b));
	}

	function or(a, b) {
		if (arePseudoBin(a, b))
		    return nand(nand(a,a), nand(b,b));
	}

	function xor(a, b) {
		if (arePseudoBin(a, b))
		    return nand(nand(nand(a,b), a), nand(nand(a,b), b));
	}

	function halfAdder(a, b) {
		if (arePseudoBin(a, b))
		    return { carry: and(a, b), sum: xor(a, b) };
	}

	function fullAdder(a, b, c) {
		if (arePseudoBin(a, b, c)) {
		    var h0 = halfAdder(a, b),
		        h1 = halfAdder(h0.sum, c);
		    return {carry: or(h0.carry, h1.carry), sum: h1.sum };
		}
	}
    if (typeof a.length == 'undefined' || typeof b.length == 'undefined')
        throw new Error('bad values');

    var inA = Array(4),
        inB = Array(4),
        out = Array(4),
        i = 4,
        pass;

    while (i--) {
        inA[i] = a[i] != 1 ? 0 : 1;
        inB[i] = b[i] != 1 ? 0 : 1;
    }

    pass = halfAdder(inA[3], inB[3]);
    out[3] = pass.sum;
    pass = fullAdder(inA[2], inB[2], pass.carry);
    out[2] = pass.sum;
    pass = fullAdder(inA[1], inB[1], pass.carry);
    out[1] = pass.sum;
    pass = fullAdder(inA[0], inB[0], pass.carry);
    out[0] = pass.sum;
    return out.join('');
}

```

</section>
