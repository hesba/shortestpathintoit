<script setup>
function dijkstra(graph, start, end) {
  const distance = {};
  const previous = {};
  const unvisited = new Set();
  const visited = new Set();

  // Initialize distances and unvisited set
  for (const node in graph) {
    if (node === start) {
      distance[node] = 0;
    } else {
      distance[node] = Infinity;
    }
    previous[node] = null;
    unvisited.add(node);
  }

  while (unvisited.size > 0) {
    // Find the node with the smallest distance
    let current = null;
    for (const node of unvisited) {
      if (current === null || distance[node] < distance[current]) {
        current = node;
      }
    }

    // Mark the current node as visited
    unvisited.delete(current);
    visited.add(current);

    // Update distances to neighbors of the current node
    for (const [neighbor, weight] of Object.entries(graph[current])) {
      if (visited.has(neighbor)) {
        continue;
      }
      let newDistance = distance[current] + weight;
      if (newDistance < distance[neighbor]) {
        distance[neighbor] = newDistance;
        previous[neighbor] = current;
      }
    }
  }

  // Reconstruct the shortest path from start to end
  const path = [];
  let current = end;
  while (previous[current] !== null) {
    path.unshift(current);
    current = previous[current];
  }
  if (path.length === 0) {
    return null; // No path found
  }
  path.unshift(current);

  return { distance: distance[end], path };
}

const graph = {
  A: { A: 0, B: 246.3, C: 489.6, D: 389, E: 626.1 },
  B: { B: 0, C: 378.9, D: 316.6, E: 450.9, X: 402.5 },
  C: { A: 518.6, B: 414.2, C: 0, D: 516.9, E: 378.2 },
  D: { A: 337, C: 413.2, D: 0, E: 440.5, X: 234.7 },
  E: { A: 650.2, B: 485, C: 376.1, D: 496.2, E: 0, X: 328.9 },
  X: { A: 551.6, B: 462.6, C: 610.1, D: 236.9, E: 315.8, X: 0 },
};

const result = dijkstra(graph, "A", "X");
console.log(result); // { distance: 623.7, path: [ 'A', 'D' ,'X' ] }
</script>
<template>
  <h1>{{ "distance: " + result.distance + " path: " + result.path }}</h1>
</template>
