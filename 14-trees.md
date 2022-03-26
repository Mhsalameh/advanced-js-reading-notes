# Trees

A tree data structure can be defined recursively as a collection of nodes, where each node is a data structure consisting of a value and a list of references to nodes. The start of the tree is the "root node" and the reference nodes are the "children". No reference is duplicated and none points to the root.

## Terms

- Node
  - A Tree node is a component which may contain its own values, and references to other nodes
- Root
  - The root is the node at the beginning of the tree
- K
  - A number that specifies the maximum number of children any node may have in a k-ary tree. In a binary tree, k = 2.
- Left
  - A reference to one child node, in a binary tree
- Right
  - A reference to the other child node, in a binary tree
- Edge
  - The edge in a tree is the link between a parent and child node
- Leaf
  - A leaf is a node that does not have any children
- height
  - The height of a tree is the number of edges from the root to the furthest leaf

## Traversals

- Depth First: Depth first traversal is where we prioritize going through the depth (height) of the tree first. There are multiple ways to carry out depth first traversal, and each method changes the order in which we search/print the root. Here are three methods for depth first traversal:

  - Pre-order: root >> left >> right
  - In-order: left >> root >> right
  - Post-order: left >> right >> root

- Breadth First: Breadth first traversal iterates through the tree by going through each level of the tree node-by-node.
  - Traditionally, breadth first traversal uses a queue (instead of the call stack via recursion) to traverse the width/breadth of the tree.

## Binary Trees

- Trees can have any number of children per node, but Binary Trees restrict the number of children to two (hence our left and right children).
- There is no specific sorting order for a binary tree. Nodes can be added into a binary tree wherever space allows.

## K-ary Trees

- If Nodes are able have more than 2 child nodes, we call the tree that contains them a K-ary Tree. In this type of tree we use K to refer to the maximum number of children that each Node is able to have.

## bookmarks

- [trees](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/Trees.html)
- [youtube](https://www.youtube.com/watch?v=1-l_UOFi1Xw)
