---
id: 5ec0181a380e86eaad4d1512
title: Floyd-Warshall algorithm
challengeType: 5
---

## Description
<section id='description'>
The <a href="https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm" target="_blank">Floyd–Warshall algorithm</a> is an algorithm for finding shortest paths in a weighted graph with positive or negative edge weights.
</section>

## Instructions
<section id='instructions'>
Find the lengths of the shortest paths between all pairs of vertices of the given directed graph. Your code may assume that the input has already been checked for loops, parallel edges and negative cycles.
Write a function that takes an array and a number as parameters. The array will contain 3 elements : the third element in the array is the weight of the edge between the vertices denoted by the first and second element. For example: [1,2,3] = The weight of the edge between vertices 1 and 2 is 3. The number parameter denotes the total number of vertices in the graph.
The function should return an array of length equal to the number of vertices. Each array element should also be an array that contains the shortest distances to the other vertices.
For example: Let's assume that the function returns [[5,3], [5,3], [4,6]]. The first element is [5,3] which have the shortest distances from the vertex 1 to the other vertices. The shortest distance between 1 and 2 is 5. The shortest distance between 1 and 3 is 3. Similarly the second element represent the shortest distance from vertex 2 to other vertices, i.e. From 2 to 1 shortest distance is 5 and From 2 to 3 it is 3.</p>
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>floydWarshall</code> should be a function.
    testString: assert(typeof floydWarshall=='function');
  - text: <code>floydWarshall([[1,2,2], [1,3,1], [2,3,4], [3,1,1]], 3)</code> should return an array.
    testString: assert(Array.isArray(floydWarshall(tests[0].slice(),3)));
  - text: <code>floydWarshall([[1,2,2], [1,3,1], [2,3,4], [3,1,1]], 3)</code> should return <code>[[2, 1], [5, 4], [1, 3]]</code>.
    testString: assert.deepEqual(floydWarshall(tests[0].slice(), 3),results[0]);
  - text: <code>floydWarshall([[1,2,2], [2,1,2], [1,3,1], [3,1,1], [2,3,4], [3,2,4]], 3)</code> should return <code>[[2, 1], [2, 3], [1, 3]]</code>.
    testString: assert.deepEqual(floydWarshall(tests[1].slice(), 3),results[1]);
  - text: <code>floydWarshall([[1,2,1], [2,3,2], [3,1,3]], 3)</code> should return <code>[[1, 3], [5, 2], [3, 4]]</code>.
    testString: assert.deepEqual(floydWarshall(tests[2].slice(), 3),results[2]);
  - text: <code>floydWarshall([[1,2,6], [1,3,2], [2,4,1], [3,4,4], [4,1,2]], 4)</code> should return <code>[[6, 2, 6], [3, 5, 1], [6, 12, 4], [2, 8, 4]]</code>.
    testString: assert.deepEqual(floydWarshall(tests[3].slice(), 4),results[3]);
  - text: <code>floydWarshall([[1, 3, 2], [2, 1, 4], [2, 3, 3], [3, 4, 2], [4, 2, 1]], 4)</code> should return <code>[[5, 2, 4], [4, 3, 5], [7, 3, 2], [5, 1, 4]]</code>.
    testString: assert.deepEqual(floydWarshall(tests[4].slice(), 4),results[4]);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function floydWarshall(weights, numVertices) {
  // Good luck!
}

```

</div>

### After Test

<div id='js-teardown'>

```js
let tests=[
  [[1,2,2], [1,3,1], [2,3,4], [3,1,1]],
  [[1,2,2], [2,1,2], [1,3,1], [3,1,1], [2,3,4], [3,2,4]],
  [[1,2,1], [2,3,2], [3,1,3]],
  [[1,2,6], [1,3,2], [2,4,1], [3,4,4], [4,1,2]],
  [[1, 3, 2], [2, 1, 4], [2, 3, 3], [3, 4, 2], [4, 2, 1]]
]
let results=[
  [[2, 1], [5, 4], [1, 3]],
  [[2, 1], [2, 3], [1, 3]],
  [[1, 3], [5, 2], [3, 4]],
  [[6, 2, 6], [3, 5, 1], [6, 12, 4], [2, 8, 4]],
  [[5, 2, 4], [4, 3, 5], [7, 3, 2], [5, 1, 4]],
]


```

</div>

</section>

## Solution
<section id='solution'>


```js
function floydWarshall(weights,numVertices) {
  var dist = new Array(numVertices);
  for(var i=0;i<numVertices;i++){
    dist[i]=new Array(numVertices);
    dist[i].fill(9999999);
  }

  weights.forEach(function(w){
      dist[w[0] - 1][w[1] - 1] = w[2];
  })

  var next = new Array(numVertices);
  for(var i=0;i<numVertices;i++)
    next[i]=new Array(numVertices);

  for (var i = 0; i < next.length; i++) {
      for (var j = 0; j < next.length; j++)
          if (i != j)
              next[i][j] = j + 1;
  }

  for (var k = 0; k < numVertices; k++)
      for (var i = 0; i < numVertices; i++)
          for (var j = 0; j < numVertices; j++)
              if (dist[i][k] + dist[k][j] < dist[i][j]) {
                  dist[i][j] = dist[i][k] + dist[k][j];
                  next[i][j] = next[i][k];
              }

  for(var i=0;i<dist.length;i++){
    dist[i].splice(i,1)
  }
  return dist;
}

```

</section>
