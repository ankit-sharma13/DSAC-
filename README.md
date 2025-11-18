#include <iostream>
#include<stdlib.h>
using namespace std;

struct node {
    int data;
    node *left, *right;
};

node* createnode(int value) {
    node* newnode = new node();
    newnode->data = value;
    newnode->left = newnode->right = NULL;
    return newnode;
}

node* binarysearchtree(node* root, int value) {
    if (root == NULL)
        return createnode(value);

    if (value < root->data)
        root->left = binarysearchtree(root->left, value);
    else if (value > root->data)
        root->right = binarysearchtree(root->right, value);

    return root;
}

void inorder(node* root) {
    if (root == NULL)
        return;

    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

int main() {
    node* root = NULL;
    int n, value;

    cout << "How many nodes you want to create?";
    cin >> n;
    cout<<"Enter the values:";

    for (int i = 0; i < n; i++) {
        cin >> value;
        root = binarysearchtree(root, value);
    }

    cout << "Inorder traversal: ";
    inorder(root);
    cout << "\n";

    return 0;
}
