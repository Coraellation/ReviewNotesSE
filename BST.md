Binary Search Trees
======

```Tree```: Graph with node called a root with no parent; all other parents have one parent
```Binary Tree```: Each node can have at most two children

### BST vs. BT

- BST: Keys of all nodes in left substree < current node's key
- BST: Keys of all nodes in right substree > current node's key
- Saying left->key < key < right->key is not enough; a BT may satisfy this as well
- Heap is a kind of BT, but not a BST

###### BST Node Sample
This Node stores a string value.
```cpp
struct BST_Node{
	string key;
	BST_Node* left;
	BST_Node* right;	
};
```

###### BST Lookup (has) using Recursion
```cpp
bool BST_has(const BST& root, string key){
	if (root == NULL){
		return false;
	}else if (root->key == key){
		return true;
	}else if (key < root->key){
		return BST_has(root->left, key);
	}else{
		return BST_has(root->right, key);
	}
}
```
###### BST Insertion

Similar to BST Lookup
```cpp
void BST_insert(BST& root, string key){
	if (root == NULL){
		root = new BST_Node;
		root->key = key;
		root->left = NULL;
		root->right = NULL;
	}else if (key < root->key){
		BST_insert(root->left, key);
	}else{
		BST_insert(root->right, key);
	}
}
```
###### Inorder Traversal BST Print

```cpp
void BST_print(const BST& root){
	if (root != NULL){
		BST_print(root->left);
		cout << root->key << endl;
		BST_print(root->right);
	}
}
```
### Complexity

N Nodes, height k

Operation | Complexity | Why
----------|------------|-----
Print     | O(N)       |All nodes are visited
Lookup    | Worst Case: k (present), k+1 (not present)| Gone through entire height of tree




