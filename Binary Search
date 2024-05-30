#include <iostream>
#include <queue>
#include <stack>
using namespace std;

struct Node {
  int data;
  Node *left;
  Node *right;
};

class BST {
private:
  Node *root;


  void insertByRecursion(Node *temp, int x) {
    if (temp->data <= x) {
      if (temp->right == nullptr) {
        Node *newNode = new Node;
        newNode->data = x;
        newNode->left = newNode->right = nullptr;
        temp->right = newNode;
      } else {
        insertByRecursion(temp->right, x);
      }
    } else if (temp->data >= x) {
      if (temp->left == nullptr) {
        Node *newNode = new Node;
        newNode->data = x;
        newNode->left = newNode->right = nullptr;
        temp->left = newNode;
      } else {
        insertByRecursion(temp->left, x);
      }
    }
  }

//insertion using loop
void insertusingloop(int x){
  Node* newnode=new Node;
  newnode->data=x;
  newnode->left=newnode->right=nullptr;
  if(root==nullptr) root=newnode;
  Node *temp=root;
  Node* prev;
  while(temp!=nullptr){
    prev=temp;
    if(temp->data<=x)
      temp=temp->right;
    else
      temp=temp->left;
  }
  
  if(prev->data<=x){
    
    prev->right=newnode;
  }
  else{
    prev->left=newnode;
    
  }
  
}

  int Get_hightHelper(Node *temp) {
    if (temp == nullptr)
      return -1;

    int left = Get_hightHelper(temp->left);
    int right = Get_hightHelper(temp->right);

    return 1 + max(left, right);
  }

public:
  BST() : root(nullptr) {}


bool searchByBST(int k){
  if(root==NULL){
    return false;
  }
  Node *temp=root;
  while(temp!=NULL){
    if(temp->data==k) return true;
    else if(temp->data>k) temp=temp->left;
    else temp=temp->right;
  }
  return false;
}

  void insertWithRecursion(int x) {
    if (root == nullptr) {
      Node *newNode = new Node;
      newNode->data = x;
      newNode->left = newNode->right = nullptr;
      root = newNode;
    } else {
      insertByRecursion(root, x);
    }
  }

  // how to calc the hight by recusion

  int GetHight() {
    Node *temp = root;
    if (temp == nullptr) {
      return -1;

    } else
      return Get_hightHelper(temp);
  }
  // BFS

  void DisplayByLevelOrder() {
    if (root == nullptr)
      return;
    queue<Node *> q;
    q.push(root);
    while (!q.empty()) {
      Node *current = q.front();
      cout << current->data << " ";
      q.pop();
      if (current->left != nullptr)
        q.push(current->left);
      if (current->right != nullptr)
        q.push(current->right);
    }
  }


  // DFS

  void DisplayByPreOrderHelper(Node *temp) {
    if (temp == nullptr)
      return;
    cout << temp->data << " ";
    DisplayByPreOrderHelper(temp->left);
    DisplayByPreOrderHelper( temp->right);
  }
  void DisplayByPreOrder() {
    if (root == nullptr)
      return;
    DisplayByPreOrderHelper(root);
  }

  void DisplayByInOrderHelper(Node *temp) {
    if (temp == nullptr)
      return;
    DisplayByInOrderHelper(temp->left);
    cout << temp->data << " ";
    DisplayByPreOrderHelper(temp->right);
  }
  void DisplatBYInOrder() {
    if (root == nullptr)
      return;
    DisplayByInOrderHelper(root);
  }

  void DisplayByPostOrderHelper(Node *temp) {
    if (temp == nullptr)
      return;
    DisplayByPostOrderHelper(temp->left);
    DisplayByPostOrderHelper(temp->right);
    cout << temp->data << " ";
  }
  void DislayByPostOrder() {
    if (root == nullptr)
      return;
    DisplayByPostOrderHelper(root);
  }
//delete using loop
void deletUsingLoop(int x) {
  Node *parent = nullptr;
  Node *current = root;

  // Find the node to be deleted and its parent
  while (current != nullptr && current->data != x) {
    parent = current;
    if (x < current->data) {
      current = current->left;
    } else {
      current = current->right;
    }
  }

  // If the node was not found, return
  if (current == nullptr) {
    return;
  }

  // Case 1: Node has no children (leaf node)
  if (current->left == nullptr && current->right == nullptr) {
    if (current == root) {
      root = nullptr;
    } else if (parent->left == current) {
      parent->left = nullptr;
    } else {
      parent->right = nullptr;
    }
    delete current;
  }
  // Case 2: Node has only one child
  else if (current->left == nullptr) {
    if (current == root) {
      root = current->right;
    } else if (parent->left == current) {
      parent->left = current->right;
    } else {
      parent->right = current->right;
    }
    delete current;
  } else if (current->right == nullptr) {
    if (current == root) {
      root = current->left;
    } else if (parent->left == current) {
      parent->left = current->left;
    } else {
      parent->right = current->left;
    }*
    delete current;
  }
  // Case 3: Node has two children
  else {
    // Find the in-order predecessor (maximum value in the left subtree)
    Node *predParent = current;
    Node *pred = current->left;
    while (pred->right != nullptr) {
      predParent = pred;
      pred = pred->right;
    }

    // Replace current node's data with in-order predecessor's data
    current->data = pred->data;

    // Delete the in-order predecessor
    if (predParent != current) {
      predParent->right = pred->left;
    } else {
      predParent->left = pred->left;
    }
    delete pred;
  }
}




//delete using recursion

  Node *deletHelper(Node *temp, int x) {
    if (temp == nullptr)
      return temp;
    if (temp->data < x) {
      temp->right = deletHelper(temp->right, x);
    } else if (x < temp->data) {
      temp->left = deletHelper(temp->left, x);
    } else {
      if (temp->left == nullptr && temp->right == nullptr) {
        return nullptr;

      } else if ((temp->left == nullptr || temp->right == nullptr) &&
                 temp->left != temp->right) {
        if (temp->left == nullptr) {
          Node *temp1 = temp->right;
          delete temp;
          return temp1;
        } else {
          Node *temp1 = temp->left;
          delete temp;
          return temp1;
        }

      } else {
        int maxval = getMax(temp->left);
        temp->data = maxval;
        temp->left = deletHelper(temp->left, maxval);
      }
    }
    return temp;
  }
void delet(int x) { root = deletHelper(root, x); }

int getMax(Node *temp) {
  if (temp == nullptr)
    return -1;
  if (temp->right == nullptr)
    return temp->data;
  return getMax(temp->right);
}
//traverse using stack 
void DisplaybyPreOrder() {
  if (root == nullptr) return;

  stack<Node*> nodeStack;
  nodeStack.push(root);

  while (!nodeStack.empty()) {
    Node* temp = nodeStack.top();
    nodeStack.pop();
    cout << temp->data << " ";

    if (temp->right) nodeStack.push(temp->right);
    if (temp->left) nodeStack.push(temp->left);
  }
}

void DisplayByInOrder() {
  if (root == nullptr) return;

  stack<Node*> nodeStack;
  Node* temp = root;

  while (temp != nullptr || !nodeStack.empty()) {
    while (temp != nullptr) {
      nodeStack.push(temp);
      temp = temp->left;
    }

    temp = nodeStack.top();
    nodeStack.pop();
    cout << temp->data << " ";
    temp = temp->right;
  }
}

void DisplayByPostOrder() {
  if (root == nullptr) return;

  stack<Node*> nodeStack1, nodeStack2;
  nodeStack1.push(root);

  while (!nodeStack1.empty()) {
    Node* temp = nodeStack1.top();
    nodeStack1.pop();
    nodeStack2.push(temp);

    if (temp->left) nodeStack1.push(temp->left);
    if (temp->right) nodeStack1.push(temp->right);
  }

  while (!nodeStack2.empty()) {
    Node* temp = nodeStack2.top();
    nodeStack2.pop();
    cout << temp->data << " ";
  }
}

  
};

int main() {
  BST bst;
  bst.insertWithRecursion(10);
  bst.insertWithRecursion(5);

  bst.insertWithRecursion(1);
  bst.insertWithRecursion(7);
  bst.insertWithRecursion(6);
  bst.insertWithRecursion(14);
  bst.insertWithRecursion(12);
  bst.insertWithRecursion(16);
  //   cout<<bst.GetHight();
  // bst.DisplayByLevelOrder();
  bst.delet(12);
  bst.DislayByPostOrder();
  return 0;
}

