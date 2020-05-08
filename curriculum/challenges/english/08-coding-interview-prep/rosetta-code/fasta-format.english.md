---
id: 5eb5a7fcbc56bcbf304b5473
title: FASTA format
challengeType: 5
---

## Description
<section id='description'>
In <a href= "https://en.wikipedia.org/wiki/bioinformatics" target="_blank">bioinformatics</a>, long character strings are often encoded in a format called <a href="https://en.wikipedia.org/wiki/FASTA format" target="_blank">FASTA</a>.
A FASTA file can contain several strings, each identified by a name marked by a <code>&gt;</code> (greater than) character at the beginning of the line.
</section>

## Instructions
<section id='instructions'>
Write a function that takes a FASTA file (as a string parameter) such as:

<pre>
>Example1
THERECANBENOSPACE
>Example2
THERECANBESEVERAL
LINESBUTTHEYALLMUST
BECONCATENATED
</pre>

The result for the above input should be:

<pre>
Example1:THERECANBENOSPACE
Example2:THERECANBESEVERALLINESBUTTHEYALLMUSTBECONCATENATED
</pre>

<strong>Note:</strong> The input string will contain '|' as line separators. The output should contain '|' as line separators.</b></p>
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>fasta</code> should be a function.
    testString: assert(typeof fasta == 'function');
  - text: <code>fasta('>FASTA1|THERECANBENOSPACE|>FASTA2|THERECANBESEVERAL|LINESBUTTHEYALLMUST|BECONCATENATED')</code> should return a String.
    testString: assert(typeof fasta(tests[0])=='string');
  - text: <code>fasta('>FASTA1|THERECANBENOSPACE|>FASTA2|THERECANBESEVERAL|LINESBUTTHEYALLMUST|BECONCATENATED')</code> should return <code>'FASTA1:THERECANBENOSPACE|FASTA2:THERECANBESEVERALLINESBUTTHEYALLMUSTBECONCATENATED'</code>
    testString: assert.equal(fasta(tests[0]),results[0]);
  - text: <code>fasta('>ANOTHERFASTA|LINEO|LINET|>WOAH|WOAHH|WOAHH')</code> should return <code>'ANOTHERFASTA:LINEOLINET|WOAH:WOAHHWOAHH'</code>
    testString: assert.equal(fasta(tests[1]),results[1]);
  - text: <code>fasta('>HELLO|WORLD|>HELLOAGAIN|WORLD|WORLDMORE|>HELLOYETAGAIN|WORLDAGAIN|WORLDLINE')</code> should return <code>'HELLO:WORLD|HELLOAGAIN:WORLDWORLDMORE|HELLOYETAGAIN:WORLDAGAINWORLDLINE'</code>
    testString: assert.equal(fasta(tests[2]),results[2]);
  - text: <code>fasta('>FIVELINES|ONE|TWO|THREE|FOUR|FIVE|>THREELINES|ONE|TWO|THREE')</code> should return <code>'FIVELINES:ONETWOTHREEFOURFIVE|THREELINES:ONETWOTHREE'</code>
    testString: assert.equal(fasta(tests[3]),results[3]);
  - text: <code>fasta('>LASTEXAMPLE|LAST|EXAMPLE|>LASTEXAMPLELINE|LAST|EXAMPLE|LINE')</code> should return <code>'LASTEXAMPLE:LASTEXAMPLE|LASTEXAMPLELINE:LASTEXAMPLELINE'</code>
    testString: assert.equal(fasta(tests[4]),results[4]);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function fasta(str) {
  // Good luck!
}

```

</div>

### After Test

<div id='js-teardown'>

```js
const tests=[
  ">FASTA1|THERECANBENOSPACE|>FASTA2|THERECANBESEVERAL|LINESBUTTHEYALLMUST|BECONCATENATED",
  ">ANOTHERFASTA|LINEO|LINET|>WOAH|WOAHH|WOAHH",
  ">HELLO|WORLD|>HELLOAGAIN|WORLD|WORLDMORE|>HELLOYETAGAIN|WORLDAGAIN|WORLDLINE",
  ">FIVELINES|ONE|TWO|THREE|FOUR|FIVE|>THREELINES|ONE|TWO|THREE",
  ">LASTEXAMPLE|LAST|EXAMPLE|>LASTEXAMPLELINE|LAST|EXAMPLE|LINE"];

const results=[
    "FASTA1:THERECANBENOSPACE|FASTA2:THERECANBESEVERALLINESBUTTHEYALLMUSTBECONCATENATED",
    "ANOTHERFASTA:LINEOLINET|WOAH:WOAHHWOAHH",
    "HELLO:WORLD|HELLOAGAIN:WORLDWORLDMORE|HELLOYETAGAIN:WORLDAGAINWORLDLINE",
    "FIVELINES:ONETWOTHREEFOURFIVE|THREELINES:ONETWOTHREE",
    "LASTEXAMPLE:LASTEXAMPLE|LASTEXAMPLELINE:LASTEXAMPLELINE"
  ];

```

</div>

</section>

## Solution
<section id='solution'>


```js
function fasta(str){
	str=str.split("|");
	let format="";

	str.forEach(function (a){
    if(a.startsWith(">")){
      format+="|"+a.substring(1)+":";
    }else{
      format+=a;
    }
	});

	return format.substring(1);
}

```

</section>
