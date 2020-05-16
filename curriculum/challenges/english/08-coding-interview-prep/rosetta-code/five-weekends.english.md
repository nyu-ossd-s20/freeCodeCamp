---
id: 5ebf3a28380e86eaad4d1511
title: Five weekends
challengeType: 5
---

## Description
<section id='description'>
Months with 31 days that start on a Friday will have 5 full weekends (5 Fridays, 5 Saturdays, and 5 Sundays). For example, May 2020 has 5 full weekends.
</section>

## Instructions
<section id='instructions'>
Write a function that counts the number of months with 5 full weekends for a given year range. The year range is passed as parameter to the function.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>fiveWeekends</code> should be a function.
    testString: assert(typeof fiveWeekends=='function');
  - text: <code>fiveWeekends(2000,2018)</code> should return a number.
    testString: assert(typeof fiveWeekends(2000,2018)=='number');
  - text: <code>fiveWeekends(2000,2018)</code should return <code>17</code>.
    testString: assert.equal(fiveWeekends(2000,2018),17);
  - text: <code>fiveWeekends(1900,2100)</code should return <code>201</code>.
    testString: assert.equal(fiveWeekends(1900,2100),201);
  - text: <code>fiveWeekends(1950,2000)</code should return <code>52</code>.
    testString: assert.equal(fiveWeekends(1950,2000),52);
  - text: <code>fiveWeekends(2010,2015)</code should return <code>6</code>.
    testString: assert.equal(fiveWeekends(2010,2015),6);
  - text: <code>fiveWeekends(1500,2000)</code should return <code>502</code>.
    testString: assert.equal(fiveWeekends(1500,2000),502);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function fiveWeekends(startYear, endYear) {
  // Good luck!
}

```

</div>

</section>

## Solution
<section id='solution'>


```js
function fiveWeekends(startYear, endYear) {
  function startsOnFriday(month, year){
   return new Date(year, month, 1).getDay() === 5;
  }

  function has31Days(month, year){
    return new Date(year, month, 31).getDate() === 31;
  }

  function checkMonths(year){
   var month, count = 0;
   for (month = 0; month < 12; month += 1){
    if (startsOnFriday(month, year) && has31Days(month, year)){
     count += 1;
    }
   }
   return count;
  }
 var year,monthTotal = 0,total = 0;

 for (year = startYear; year <= endYear; year += 1){
  monthTotal = checkMonths(year);
  total += monthTotal;
 }
 return total;
}

```

</section>
