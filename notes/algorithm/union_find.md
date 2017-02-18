# Union-Find

Can be used to implement Kruskal's algorithm which finds the Minimum Spanning Tree.

Here's the Kruskal's algorithm

1. Sort the edges according to their weight
2. For each edge e in the sorted list
  i. Let u, v = e
  ii. if Find(u) != Find(v)
     a. Union(Find(u), Find(v))


The idea behind it is keep on picking edges greedily so that by selecting an edge it doesn't form a circle in the component.

## How to implement Union-Find

### Linked list

Union -> append one linked list to another.
Find -> Find the head of the linked list

Inefficient

### Tree like structure

Union -> Of two nodes where one node points to the other node and the other node becomes the root of the tree.
Find -> Returns the root of the tree

Union -> constant
Find -> O(n) We may as well get a list

### Improvement by Union-by-rank

By doing the union cleverly. In the earlier stage, we just randomly make a root point to the other root. But here, we make the root of the tree with less height point to the root of the tree with larger height.

Thus, the find is at most O(Log n).

Why?
I don't think I understand the proof completely.

### Another improvement on find by Path compression

Where in union, you make the tree with smaller number of nodes point to the tree with larger number of nodes. And in Find, you just modify the tree in a way so that all the nodes that you encountered on your way to find the root, you make them directly point to the root.