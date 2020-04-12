---
layout: post
date: 2020-04-12
summary: "C++ code to create a binary search tree."
content_description: "C++ code fot binary search tree explained."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Binary Search Tree</span></h1>
    <h4><span>In C++</span></h4>
    <small>12 Apr 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>A</kbd> binary search tree (BST) is a hierarchical data structure with a root node at the top. Every node has at most 2 child nodes. The right-side node has a larger value than the left-side node and every node has 1 parent. A node with no child nodes is called a leaf. Each node in the BST can be a BST in itself and that is known as a subtree which has its root at that specific node.
</p>

<p id="blog_text">
BST is a good way to store numbers. Let's consider an "n" number of digits that you want to store, you could store them in an unsorted array to start with. If you wanted to find an element in this array, you would have to loop through all the items to look for that digit which may result in a O(n) complexity. If you stored those digits in a BST, you can improve the time complexity to O(log(n)). To look up a digit, you can move to the right or left side of the tree according to the values you encounter.
</p>

<p id="blog_text">
A tree is basically a group of nodes that are linked together in a specific and defined way. The node is the unit at which all functions will happen. We will create every node and define what nodes are found on its right and left side.
<br />
To create a node in C++, we will use a struct which has 3 items, the data that it stores, the link to the left-side node and the link to the right-side node.
</p>

<pre>
struct BSTnode {
    int data;
    BSTnode *left;
    BSTnode *right;
};
</pre>

<p id="blog_text">
We will then declare functions that will help us do minimal actions such as creating new nodes, inserting data into a node and searching for a particular node in a tree.
</p>

<pre>
BSTnode *create_node(int);
BSTnode *insert(BSTnode*, int);
bool search(BSTnode*, int);
</pre>

<p id="blog_text">
The return value of the first 2 functions is a pointer to a BSTnode. The search function returns a boolean which lets us know if we were able to find the node we are looking for.
<br />
<br />
Next we will define the function used to create new nodes:
</p>

<pre>
BSTnode* create_node(int data)
{
    BSTnode *node = new BSTnode();
    node->data = data;
    node->left = node->right = NULL;
    return node;
}
</pre>

<p id="blog_text">
In the function above, we create a new BSTnode and assign data to it. We also create pointers to its left and right nodes that will be determined in the next function.
<br />
<br />
The code below shows a function that allows us to insert data into a new node based on the values given. The value of the right node is greater than that in the left node.
</p>

<pre>
BSTnode* insert(BSTnode *node, int data)
{
    if (node == NULL) {
        node = create_node(data);
        return node;
    }
    else if (data <= node->data) {
        node->left = insert(node->left, data);
    }
    else {
        node->right = insert(node->right, data);
    }
    
    return node;
}
</pre>

<p id="blog_text">
To search a BST, we create the recursive function below which will look for our data in every node until it finds it.
</p>

<pre>
bool search(BSTnode *node, int data)
{
    if (node == NULL) return false;
    else if (node->data == data) return true;
    else if (data <= node->data) return search(node->left, data);
    else return search(node->right, data);
}
</pre>

<p id="blog_text">
To put all the code above together, we create a programme that will take input integers from the user and store them in a BST structure. The user will then be asked to enter a number which is used to do a search in the tree we have created.
</p>

<pre>
int main()
{
    int data[10];
    cout << "Enter 10 integers: ";
    for (int i=0; i<10; i++)
        cin >> data[i];

    BSTnode *root_node = NULL;
    for (int i=0; i<sizeof(data); i++)
        root_node = insert(root_node, data[i]);
    
    int number;
    cout << "Enter a number: ";
    cin >> number;
    
    if (search(root_node, number) == true) {
        cout << "Found number in tree!" << endl;
    }
    else {
        cout << "Could not find number in tree!" << endl;
    }
    
    return 0;
}
</pre>


</div>


