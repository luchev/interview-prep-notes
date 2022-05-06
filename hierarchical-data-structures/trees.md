# Trees



### Trees

A tree is a hierarchical data structure. A tree has one root node (one starting element) and all other elements are children/grandchildren/etc. of this root element.

![](https://i.imgur.com/5ownlqQ.jpg)

The root in the picture above is 2. Its children are 7 and 5. 5 is a child of the root 2 and also the parent of 9.

#### How does the tree stay connected

There are 2 ways to keep the Nodes in the tree connected.

1. Each parent has pointers to its children. (The classic widely used approach)
2. Each node has a pointer to its parent. (Not widely used in most algorithms, but still very useful in some particular problems)
3. 1 and 2 combined - Each node has pointers to its children and a pointer to its parent. This makes the traversal of the tree very easy in each direction, but also takes more memory.

#### Node of a binary tree

```
struct Node {
    int data;
    Node* left = nullptr;
    Node* right = nullptr;
};
```

#### Node of a tree with variable number of children

```
struct Node {
    int data;
    vector<Node*> children;
};
```

#### Traversals

**Preorder (DFS)**

Preorder traversal is also known as DFS (Depth First Search).

Time complexity $$\mathcal{O}(n)$$, where `n` is the number of nodes in the tree.

The order in which we visit nodes is

1. Current node
2. Children of the node in order from left to right

```
void DFS(Node* current) {
    if (current == nullptr) {
        return;
    }

    cout << current->data; // do something with the node

    DFS(current->left);
    DFS(current->right);
}
```

**Postorder**

Time complexity $$\mathcal{O}(n)$$, where `n` is the number of nodes in the tree.

The order in which we visit nodes is

1. Children of the node in order from left to right
2. Current node

```
void Postorder(Node* current) {
    if (current == nullptr) {
        return;
    }

    Postorder(current->left);
    Postorder(current->right);

    cout << current->data; // do something with the node
}
```

**Inorder traversal**

Time complexity $$\mathcal{O}(n)$$, where `n` is the number of nodes in the tree.

The order in which we visit nodes is

1. Left child
2. Current node
3. Right child

```
void Postorder(Node* current) {
    if (current == nullptr) {
        return;
    }

    Postorder(current->left);
    cout << current->data; // do something with the node
    Postorder(current->right);
}
```

**Level order**

Level order is also known as WFS (Width First Search) or BFS (Breadth First Search).

Time complexity $$\mathcal{O}(n)$$, where `n` is the number of nodes in the tree.

The order in which we visit nodes is

1. All the nodes of level 1 (the root)
2. All the nodes of level 2 from left to right (the children of the root)
3. All the nodes of level 3 from left to right
4. etc.

**Morris order**

Morris order is an inorder traversal algorithm which does not use extra space for recursion or a stack. However it changes the tree during traversal and then reverts it to its original state.

https://en.wikipedia.org/wiki/Tree\_traversal#Morris\_in-order\_traversal\_using\_threading

#### Tree variations

**Generalized tree**

A tree where each node stores whatever data we need and has an arbitrary number of children.

```
struct Node {
	int data;
    std::vector<Node*> children;
}
```

**Trie**

**Segment Tree**

**Merge Tree**

**K-D Tree**

**BSP Tree**

**Merkle Tree**

**Treap**

**Threaded Binary Tree**

**Strict Binary Tree**

**Full Binary Tree**

**Complete Binary Tree**

### Binary Search Trees

#### BST

A binary search tree is a tree with the following properties

1. Each node has at most 2 children (left and right)
2. The value of the left child of a node is smaller than the value of the parent
3. The value of the right child of a node is bigger than the value of the parent

```
struct BST {
    int data;
    BST* left;
    BST* right;
}
```

**Complexity**

| BST operation | Average case          | Worst case         |
| ------------- | --------------------- | ------------------ |
| insert(key)   | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(n)$$ |
| remove(key)   | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(n)$$ |
| find(key)     | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(n)$$ |
| findMin()     | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(n)$$ |
| findMax()     | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(n)$$ |

The order in which we receive the data is important! If we receive ordered array \[1, 2, 3, 4, ...] we will constantly add in the right subtree. Therefore we will hit the worst case $$\mathcal{O}(n)$$ per operation.

#### AVL Tree

AVL Tree is a BST tree which also has information on each node what is the height of the node. This allows it to balance itself and always keep the height as small as possible.

```
struct BST {
    int data;
    int height;
    BST* left;
    BST* right;
}
```

**Complexity**

| BST operation | Average case          | Worst case            |
| ------------- | --------------------- | --------------------- |
| insert(key)   | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(logn)$$ |
| remove(key)   | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(logn)$$ |
| find(key)     | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(logn)$$ |
| findMin()     | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(logn)$$ |
| findMax()     | $$\mathcal{O}(logn)$$ | $$\mathcal{O}(logn)$$ |

The order in which we receive the data doesn’t matter because the tree balances itself to always have the smallest possible height.

**Balancing**

Balancing is done using the height kept in the nodes. To use the height a Balance Factor (BF) is calculated on each node. $$BF = height(leftSubTree) - height(rightSubTree)$$. Depending on the value of the balance factor there are the following 2 situations:

1. $$|BF| \leq 1$$ - If the balance factor is between -1 and 1 then the node is balanced.
2. $$|BF| > 1$$ - if the balance factor less than -1 or more than 1 (e.g -2 or 2), the node is not balanced and we must balance it.

If a node is unbalanced we can have 4 rotations that we can do:

1. RR (Right Right) - For the current node the **right** subtree is heavier. For the **right child** of the current node the **right** subtree is heavier.
2. RL (Right Left) - For the current node the **right** subtree is heavier. For the **right child** of the current node the **left** subtree is heavier.
3. LL (Left Left) - For the current node the **left** subtree is heavier. For the **left child** of the current node the **left** subtree is heavier.
4. LR (Left Right) - For the current node the **left** subtree is heavier. For the **left child** of the current node the **right** subtree is heavier.

**Code**

**Height and balance calculation**

```
void calculateHeight() {
    height = 0;
    if (left) {
        height = max(height, left->height + 1);
    }
    if (right) {
        height = max(height, right->height + 1);
    }
}

int leftHeight() const {
    if (left) {
        return left->height + 1;
    }
    return 0;
}

int rightHeight() const {
    if (right) {
        return right->height + 1;
    }
    return 0;
}

void recalculateHeights() {
    if (left) {
        left->calculateHeight();
    }
    if (right) {
        right->calculateHeight();
    }
    this->calculateHeight();
}

int balance() const {
    return leftHeight() - rightHeight();
}
```

**Rotations**

```
void rotateRight() {
    if (!left) {
        return;
    }

    Node* leftRight = this->left->right;
    Node* oldRight = this->right;

    swap(this->data, this->left->data);
    this->right = this->left;
    this->left = this->left->left;
    this->right->left = leftRight;
    this->right->right = oldRight;
}

void rotateLeft() {
    if (!right) {
        return;
    }

    Node* rightLeft = this->right->left;
    Node* oldLeft = this->left;

    swap(this->data, this->right->data);
    this->left = this->right;
    this->right = this->right->right;
    this->left->left = oldLeft;
    this->left->right = rightLeft;
}
```

**Check at each node when going up/down the recursion when inserting/deleting/etc.**

```
void fixTree() {
    if (balance() < -1) { // Right is heavier
        if (right->balance() <= -1) { // RR
            this->rotateLeft();
            recalculateHeights();
        }
        else if (right->balance() >= 1) { // RL
            right->rotateRight();
            this->rotateLeft();
            recalculateHeights();
        }
    }
    else if (balance() > 1) { // Left is heavier
        if (left->balance() >= 1) { // LL
            this->rotateRight();
            recalculateHeights();
        }
        else if (left->balance() <= -1) { // LR
            left->rotateLeft();
            this->rotateRight();
            recalculateHeights();
        }
    }
}}
```

**Modify insert**

```
Node* _insert(int value, Node* current) {
	// insert from BST
    current->calculateHeight();
    current->fixTree();
    return current;
}
```

**Modify remove**

```
Node* _remove(int value, Node* current) {
	// remove from BST
    current->calculateHeight();
    current->fixTree();
    return current;
}
```
