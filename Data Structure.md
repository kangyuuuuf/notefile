# Data Structure

## Heaps

#### Introduction

A. heap allows your to store elements and query the most important elements qucikly. Followed by the rule: **The parent has higher priority than any of its children.** 

- Data structure: array
- Worst-case performance: $O(n\log n)$

#### Implement

**Insertion:** We will put the element at the end of array, call the fuction **heapify up** to make the emelemt in to the right position.

~~~c++
template <class T, class Compare>
void heap<T, Compare>::heapifyUp(size_t currentIdx)
{
    if (currentIdx == root())
        return;
    size_t parentIdx = parent(currentIdx);
    if (higherPriority(_elems[currentIdx], _elems[parentIdx])) {
        std::swap(_elems[currentIdx], _elems[parentIdx]);
        heapifyUp(parentIdx);
    }
}
~~~

**Removal**: We move the highest priority element by remove the root and move the rightmost leaf in its place. Then, call the function **heaping down** to the the rightmost leaf which is in the root.

~~~c++
template <class T, class Compare>
void heap<T, Compare>::heapifyDown(size_t currentIdx)
{   if(!hasAChild(currentIdx)) {
        return;
    }
    size_t childIdx = maxPriorityChild(currentIdx);
    if(higherPriority(_elems[childIdx], _elems[currentIdx])) {
        std::swap(_elems[currentIdx], _elems[childIdx]);
        heapifyDown(childIdx);
    }
}
~~~

 We can implment complete trees with arrays with the start index of 1 or 0. The index of 1 is recommened since it will be hard to think when the index is 0. If the start of heap is the index of 1, we have:

​	The parents is at the$\lfloor a/2 \rfloor$'th index.

​	The left and right child are at $a/2$'th index and $2a+1$'th index respectivitly.

## Hash Table

#### Introduction

To perform hashing, we need two things:

- **Hash fuction:** Converts a key into smaller number and uses that number as an index in the table.

- **Hash table:** An array that stores values according to the index.

There is a example of hash function.

~~~c++
template <>
unsigned int hash(const std::string& key, int size)
{
      // Bernstein Hash
      unsigned int h = 0;
      for (size_t i = 0; i < key.length(); ++i)
          h = 33 * h + key[i];
      return h % size;
 }
~~~

#### Hash Collisions

When a hash fuction put two keys into one index, a hash collision happen, and we have two types of hash storing.

##### Separeate Chaining

We can let the cells of our hash table point to several linked lists of values which have the same output from hash fuction. We always insert the new value as the start of linked list. If we want to find a value, we need to find the right index of this value($O(1)$)), and find the right value from linked list($O(n)$).

- Data Structure: array/vector + linked list
- Worst-case performance to find a value: $O(n)$
- Performace to instert a value: $O(1)$

##### Linear Probing

Without creating any additional memory, we can just find the next avaliable entry if the first one is occupied.

- Data Structure: array
- Best-case performance to find a value: $O(1)$
- Worest-case performance to find a value: $O(n)$
- Worest-case performance to insert a value:$O(n)$
- Best-case performance to insert a value:$O(1)$

## B-Trees

#### Introduction

A B-Tree is a self balancing **Binary Search Tree(BST)**. B-Tree has the following properties:

- M denotes tha max number of child nodes a node can point to
- The max number of keys per niode is M-1
- The root node is either a leaf node or an internal node with 2 to M children and 1 to M-1 keys
- The rest of the internal nodes have between M/2 and M children
- All leaves are at the same depth, which makes the tree balanced

#### Implement

**Find** has the following step:

1. Go through each index of the current node's array of keys
2. If the key is in this node's arrat of keys, return the key
3. If the key is not in this node you habe two options:
   - Find the next biggest key and go to then ith child of that node
   - Find the next smallest key and go the (ith + 1) child
4. If you get to the leaf node where the data value should be and don't see it in the arrya of keys then this vlaue is not in the tree.

**Insertion** is just find the right position to put the value in, and it will followed by **Splitting Nodes**.

**Splitting Nodes** has the following step:

1. When you try to insert into node, N1, you notice that the amount of keys is now greater than M-1.
2. Now You must take the middle key and put it in the parent node’s keys
3. Now all keys that were in the array of N1 that are greater than the thrown up key are put into a node that is the (i + 1), where i is the index of the thrown up key, child of the parent node. The rest are put into the Node that is the ith child of the parent tree. If a Node does not exist for that child but is a valid child to place ,Since there is space in the parent, you can create the child Node and populate it.

#### Runtime & Data structure

- Data structure: tree node + array
- Performance of search: $O(\log n)$
- Performance of combining/splitting of keys: $O(M)$
- Performance of insert/delete: $O((M/\log M)*\log N)$

## AVL Tree

#### Introduction

AVL is just stand for the names of investors. This is the visualized graph: [Interactive AVL Simulator](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html). It is a self-balancing binary seach tree(BST) that allow you to store and query data in logarithmic time.

#### Implement

AVL tree use left rotation, right rotation, left-right rotation, and right-left rotation to keep the balance.

Code of left rotation:

~~~c++
template <class K, class V>
void AVLTree<K, V>::rotateLeft(Node*& t)
{
    functionCalls.push_back("rotateLeft"); // Stores the rotation name (don't remove this)
    // your code here
    Node* copy1 = t;
    Node* copy2 = t->right->left;
    t = t->right;
    t ->left = copy1;
    t ->left->right = copy2;

}
~~~

Code of left-right rotation:

~~~c++
template <class K, class V>
void AVLTree<K, V>::rotateLeftRight(Node*& t)
{
    functionCalls.push_back("rotateLeftRight"); // Stores the rotation name (don't remove this)
    // Implemented for you:
    rotateLeft(t->left);
    rotateRight(t);
}
~~~

#### Runtime & Data Structure

- Data Structure: tree node
- Performance of insert: $O(h)$/$O(\log n)$
- Performance of delete: $O(\log n)$

Node: the run time of rotation is $O(1)$

