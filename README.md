#include <iostream>
using namespace std;
// Create a node
struct Node {
 int data;
 struct Node* next = NULL;
};
Node * insertAtBeginning(struct Node* head_ref, int new_data) {
 // Allocate memory to a node
 struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
 // insert the data
 new_node->data = new_data;
 new_node->next = head_ref;
 // Move head to new node
 return head_ref = new_node;
}
// Insert a node after a node
void insertAfter(struct Node* prev_node, int new_data) {
 if (prev_node == NULL) 
{cout << "the given previous node cannot be NULL";
 return;
 }
 struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
 new_node->data = new_data;
 new_node->next = prev_node->next;
 prev_node->next = new_node;
}
// Insert at the end
void insertAtEnd(struct Node* head_ref, int new_data) {
 struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
 struct Node* last = head_ref; /* used in step 5*/
 new_node->data = new_data;
 new_node->next = NULL;
 if (head_ref == NULL) {
 head_ref = new_node;
 return;
 }
 while (last->next != NULL) last = last->next;
last->next = new_node;
 return;
}
// Delete a node
Node* deleteNode(struct Node* head_ref, int key) {
 struct Node *temp = head_ref, *prev;
 // Find the key to be deleted
 while (temp != NULL && temp->data != key) {
 prev = temp;
 temp = temp->next;
 }
 // If the key is not present
 if (temp == head_ref){
 head_ref = head_ref->next;
 return head_ref;
 }
 // Remove the node
 prev->next = temp->next;
 free(temp);return head_ref;
}
// Search a node
bool searchNode(struct Node** head_ref, int key) {
 struct Node* current = *head_ref;
 while (current != NULL) {
 if (current->data == key) return true;
 current = current->next;
 }
 return false;
}
// Print the linked list
void printList(struct Node* node) {
 while (node != NULL) {
 cout << node->data << " ";
 node = node->next;
 }}
// Driver program
int main() {
 struct Node* head = NULL;
 head = insertAtBeginning(head, 2);
 head = insertAtBeginning(head, 3);
 insertAtEnd(head, 1);
 insertAtEnd(head, 4);
 insertAfter(head->next, 5);
 cout << "Linked list: ";
 printList(head);
 cout << "\nAfter deleting an element: ";
 head = deleteNode(head, 3);
 printList(head);
 int item_to_find = 3;
 if (searchNode(&head, item_to_find)) {
 cout << endl << item_to_find << " is found";
 } else {
 cout << endl << item_to_find << " is not found";
}
// sortLinkedList(head);
 cout << "\nLinked List: ";
 printList(head);
}
