# C - Binary trees
![img](https://miro.medium.com/max/1200/1*CMGFtehu01ZEBgzHG71sMg.png)

This is a project by [Will Meilahn](https://github.com/WillMeilahn) at [Holberton School](https://www.holbertonschool.com) in Tulsa, Oklahoma.

## Description
>Binary Trees are data structures that store and organize data hierarchically, each node having a left and right child pointer. Different types like Binary Search Tree and Decision Trees exist with various uses. Common operations include insertion, deletion, search, and traversals like in-order, pre-order, and post-order. Careful implementation choice, considering pros and cons, is essential.

## Resources
### Read or Watch:

- [Binary Tree](https://en.wikipedia.org/wiki/Binary_tree) (note the first line: **Not to be confused with B-tree.**)
- [Data Structure And Algorithms - Tree](https://www.tutorialspoint.com/data_structures_algorithms/tree_data_structure.htm)
- [Tree Traversal](https://www.tutorialspoint.com/data_structures_algorithms/tree_traversal.htm)
- [Binary Search Tree](https://en.wikipedia.org/wiki/Binary_search_tree)
- [Data structures: Binary Tree](https://www.youtube.com/watch?v=H5JubkIy_p8)

## General

#### [- What Is a Binary Tree](https://en.wikipedia.org/wiki/Binary_tree)

A binary tree in C is a data structure used for storing data in a hierarchical manner where each node contains two pointers: 
- one to the `left child`
- one to the `right child`

#### [- What Is The Difference Between a Binary Tree And a Binary Search Tree](https://www.geeksforgeeks.org/difference-between-binary-tree-and-binary-search-tree/)

A `binary search tree` (BST) has an order property where nodes on the left of a particular node have a value less than it, and nodes on the right have a value greater than it. Whereas a `binary tree` doesn't have this order property.

#### [- What Is The Possible Gain In Terms Of Time Complexity Compared To Linked Lists](https://www.geeksforgeeks.org/time-complexities-of-different-data-structures/)

Binary trees have a time complexity gain compared to linked lists as operations can be performed in `O(log n)` instead of `O(n)`.

#### [- What Are The Depth, The Height, The Size Of a Binary Tree](https://www.geeksforgeeks.org/height-and-depth-of-a-node-in-a-binary-tree)

- The `depth` is the distance of a node from the root
- The `height` is the distance of a node to the farthest leaf
- The `size` is the total number of nodes.

#### [- What Are The Different Traversal Methods To Go Through a Binary Tree](https://www.freecodecamp.org/news/binary-search-tree-traversal-inorder-preorder-post-order-for-bst)

The commonly used traversal methods for going through a binary tree are: 
- `in-order`: visits the left subtree first, the root node, and finally the right subtree.
- `Pre-order`: visits the root node first, the left subtree, and finally the right subtree.
- `post-order`: visits the left subtree first, the right subtree, and finally the root node.

#### [- What Is a Complete, Full, Perfect, Balanced Binary Tree](https://www.geeksforgeeks.org/types-of-binary-tree/)

  - A `complete binary tree` is one where all levels are filled except possibly the last one. 
  - A `full binary tree` is a tree where all internal nodes have exactly two children and leaves are at the same level.
  - A `perfect binary tree` is a full and complete binary tree 
  - A `balanced binary tree` is a tree where the difference in height between the left and right subtrees is less than a certain threshold.

## Requirements

- Allowed editors: `vi`, `vim`, `emacs`
- All your files will be compiled on Ubuntu 20.04 LTS using `gcc`, using the options -Wall -Werror -Wextra -pedantic -std=gnu89
- All your files should end with a new line
- A `README.md` file, at the root of the folder of the project, is mandatory
- Your code should use the `Betty` style. It will be checked using [betty-style.pl](https://github.com/hs-hq/Betty/blob/main/betty-style.pl) and [betty-doc.pl](https://github.com/hs-hq/Betty/blob/master/betty-doc.pl)
- You are not allowed to use global variables
- No more than five functions per file
- You are allowed to use the standard library
- In the following examples, the `main.c` files are shown as examples. You can use them to test your functions, but you don’t have to push them to your repo (if you do, we won’t consider them). We will use our own `main.c` files at compilation. Our `main.c` files might be different from the ones shown in the examples
- The prototypes of all your functions should be included in your header file called [binary_trees.h](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/binary_trees.h)
- Don’t forget to push your header file
- All your header files should be included guarded

## Data Structures

#### Basic Binary Tree
```c++
/**
 * struct binary_tree_s - Binary tree node
 *
 * @n: Integer stored in the node
 * @parent: Pointer to the parent node
 * @left: Pointer to the left child node
 * @right: Pointer to the right child node
 */
struct binary_tree_s
{
    int n;
    struct binary_tree_s *parent;
    struct binary_tree_s *left;
    struct binary_tree_s *right;
};

typedef struct binary_tree_s binary_tree_t;
```

#### Binary Search Tree
```c++
typedef struct binary_tree_s bst_t;
```

#### AVL Tree
```c++
typedef struct binary_tree_s avl_t;
```

#### Max Binary Heap
```c++
typedef struct binary_tree_s heap_t;
```

## Print Function
To match the examples in the tasks, you are given this [function](https://github.com/hs-hq/0x1C.c)

-----------------------------
# Tasks

#### [0. New Node](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/0-binary_tree_node.c)
Write a function that creates a binary tree node

- Prototype: `binary_tree_t *binary_tree_node(binary_tree_t *parent, int value)`;
- Where `parent` is a pointer to the parent node of the node to create
- And `value` is the value to put in the new node
- When created, a node does not have any child
- Your function must return a pointer to the new node, or `NULL` on failure

<details>
<summary>File Compilation / Test</summary>
<br>

```c++
willmeilahn@/tmp/binary_trees$ cat 0-main.c 

#include <stdlib.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);

    root->left = binary_tree_node(root, 12);
    root->left->left = binary_tree_node(root->left, 6);
    root->left->right = binary_tree_node(root->left, 16);

    root->right = binary_tree_node(root, 402);
    root->right->left = binary_tree_node(root->right, 256);
    root->right->right = binary_tree_node(root->right, 512);

    binary_tree_print(root);
    return (0);
}

willmeilahn@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 0-main.c 0-binary_tree_node.c -o 0-node

willmeilahn@/tmp/binary_trees$ ./0-node
       .-------(098)-------.
  .--(012)--.         .--(402)--.
(006)     (016)     (256)     (512)
```
</details>

---------------------------

#### [1. Insert Left](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/1-binary_tree_insert_left.c)
Write a function that inserts a node as the left child of another node

- Prototype: `binary_tree_t *binary_tree_insert_left(binary_tree_t *parent, int value)`;
- Where `parent` is a pointer to the node to insert the left child in
- And `value` is the value to store in the new node
- Your function must return a pointer to the created node, or `NULL` on failure or if `parent` is `NULL`
- If `parent` already has a left child, the new node must take its place, and the old left child must be set as the left child of the new node.

<details>
<summary>File Compilation / Test</summary>
<br>

```c++
willmeilahn@/tmp/binary_trees$ cat 1-main.c

#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_print(root);
    printf("\n");
    binary_tree_insert_left(root->right, 128);
    binary_tree_insert_left(root, 54);
    binary_tree_print(root);
    return (0);
}

willmeilahn@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 1-main.c 1-binary_tree_insert_left.c 0-binary_tree_node.c -o 1-left

willmeilahn@/tmp/binary_trees$ ./1-left
  .--(098)--.
(012)     (402)

       .--(098)-------.
  .--(054)       .--(402)
(012)          (128)           
```
</details>

-----------------------

#### [2. Insert Right](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/2-binary_tree_insert_right.c)
Write a function that inserts a node as the right child of another node

- Prototype: `binary_tree_t *binary_tree_insert_right(binary_tree_t *parent, int value)`;
- Where `parent` is a pointer to the node to insert the right child in
- And `value` is the value to store in the new node
- Your function must return a pointer to the created node, or `NULL` on failure or if `parent` is `NULL`
- If `parent` already has a right child, the new node must take its place, and the old right child must be set as the right child of the new node.

<details>
<summary>File Compilation / Test</summary>
<br>

```c++
willmeilahn@/tmp/binary_trees$ cat 2-main.c 

#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_print(root);
    printf("\n");
    binary_tree_insert_right(root->left, 54);
    binary_tree_insert_right(root, 128);
    binary_tree_print(root);
    return (0);
}

willmeilahn@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 2-main.c 2-binary_tree_insert_right.c 0-binary_tree_node.c -o 2-right

willmeilahn@/tmp/binary_trees$ ./2-right 
  .--(098)--.
(012)     (402)

  .-------(098)--.
(012)--.       (128)--.
     (054)          (402)
```
</details>

-----------------

#### [3. Delete](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/3-binary_tree_delete.c)
Write a function that deletes an entire binary tree

- Prototype: `void binary_tree_delete(binary_tree_t *tree)`;
- Where `tree` is a pointer to the root node of the tree to delete
- If `tree` is `NULL`, do nothing

<details>
<summary>File Compilation / Test</summary>
<br>

```c++
willmeilahn@/tmp/binary_trees$ cat 3-main.c 

#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_insert_right(root->left, 54);
    binary_tree_insert_right(root, 128);
    binary_tree_print(root);
    binary_tree_delete(root);
    return (0);
}

willmeilahn@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 3-main.c 3-binary_tree_delete.c 0-binary_tree_node.c 2-binary_tree_insert_right.c -o 3-del

willmeilahn@/tmp/binary_trees$ valgrind ./3-del
==13264== Memcheck, a memory error detector
==13264== Copyright (C) 2002-2013, and GNU GPL'd, by Julian Seward et al.
==13264== Using Valgrind-3.10.1 and LibVEX; rerun with -h for copyright info
==13264== Command: ./3-del
==13264== 
  .-------(098)--.
(012)--.       (128)--.
     (054)          (402)
==13264== 
==13264== HEAP SUMMARY:
==13264==     in use at exit: 0 bytes in 0 blocks
==13264==   total heap usage: 9 allocs, 9 frees, 949 bytes allocated
==13264== 
==13264== All heap blocks were freed -- no leaks are possible
==13264== 
==13264== For counts of detected and suppressed errors, rerun with: -v
==13264== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)
```
</details>

-----------------------------

#### [4. Is Leaf](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/4-binary_tree_is_leaf.c)
Write a function that checks if a node is a leaf

- Prototype: `int binary_tree_is_leaf(const binary_tree_t *node)`;
- Where `node` is a pointer to the node to check
- Your function must return `1` if `node` is a leaf, otherwise `0`
- If `node` is `NULL`, return `0`

<details>
<summary>File Compilation / Test</summary>
<br>

```c++
willmeilahn@/tmp/binary_trees$ cat 4-main.c 

#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;
    int ret;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_insert_right(root->left, 54);
    binary_tree_insert_right(root, 128);
    binary_tree_print(root);

    ret = binary_tree_is_leaf(root);
    printf("Is %d a leaf: %d\n", root->n, ret);
    ret = binary_tree_is_leaf(root->right);
    printf("Is %d a leaf: %d\n", root->right->n, ret);
    ret = binary_tree_is_leaf(root->right->right);
    printf("Is %d a leaf: %d\n", root->right->right->n, ret);
    return (0);
}

willmeilahn@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 4-binary_tree_is_leaf.c 4-main.c 0-binary_tree_node.c 2-binary_tree_insert_right.c -o 4-leaf

willmeilahn@/tmp/binary_trees$ ./4-leaf 
  .-------(098)--.
(012)--.       (128)--.
     (054)          (402)
Is 98 a leaf: 0
Is 128 a leaf: 0
Is 402 a leaf: 1
```
</details>

--------------------

#### [5. Is Root](https://github.com/WillMeilahn/holbertonschool-binary_trees/blob/main/5-binary_tree_is_root.c)
Write a function that checks if a given node is a root