void main() {
List<int> originalList = [1, 2, 3, 4, 5];
List<int> reversedList = reverseListUsingStack(originalList);

print('Original List: $originalList');
print('Reversed List: $reversedList');
}

List<int> reverseListUsingStack(List<int> inputList) {
List<int> reversedList = [];
Stack<int> stack = Stack();

// Push elements onto the stack
for (int element in inputList) {
stack.push(element);
}

// Pop elements from the stack to reverse the list
while (!stack.isEmpty()) {
reversedList.add(stack.pop());
}

return reversedList;
}

class Stack<T> {
List<T> _items = [];

void push(T item) {
_items.add(item);
}

T pop() {
if (isEmpty()) {
throw StateError('Cannot pop from an empty stack');
}
return _items.removeLast();
}

bool isEmpty() {
return _items.isEmpty;
}
}
-------------------------------------------------
void main() {
String expression1 = "(a + b) * (c - d)";
String expression2 = "((a + b) * (c - d)";

print('Expression 1 is balanced: ${isBalanced(expression1)}');
print('Expression 2 is balanced: ${isBalanced(expression2)}');
}

bool isBalanced(String expression) {
Stack<String> stack = Stack();

for (int i = 0; i < expression.length; i++) {
String char = expression[i];

if (char == '(') {
stack.push(char);
} else if (char == ')') {
if (stack.isEmpty()) {
return false; // Unmatched closing parenthesis
}
stack.pop();
}
}

return stack.isEmpty; // Stack should be empty if parentheses are balanced
}

class Stack<T> {
List<T> _items = [];

void push(T item) {
_items.add(item);
}

T pop() {
if (isEmpty()) {
throw StateError('Cannot pop from an empty stack');
}
return _items.removeLast();
}

bool isEmpty() {
return _items.isEmpty;
}
}
---------------------------------------------
void main() {
// Create a sample linked list
LinkedList linkedList = LinkedList();
linkedList.addNode(1);
linkedList.addNode(2);
linkedList.addNode(3);
linkedList.addNode(4);

// Print the linked list in reverse order
print('Linked List in Reverse Order:');
printInReverse(linkedList.head);
}

class Node {
int data;
Node? next;

Node( this.data) ;
}

class LinkedList {
Node? head;

void addNode(int data) {
Node newNode = Node(data);
if (head == null) {
head = newNode;
} else {
Node? temp = head;
while (temp!.next != null) {
temp = temp.next;
}
temp.next = newNode;
}
}
}

void printInReverse(Node? node) {
if (node == null) {
return;
}

// Recursively call the function for the next node before printing the current node
printInReverse(node.next);

// Print the current node's data
print(node.data);
}
--------------------------------------------
void main() {
// Create a sample linked list
LinkedList linkedList = LinkedList();
linkedList.addNode(1);
linkedList.addNode(2);
linkedList.addNode(3);
linkedList.addNode(4);
linkedList.addNode(5);

// Find and print the middle node of the linked list
Node? middleNode = findMiddleNode(linkedList.head);
print('Middle Node: ${middleNode?.data}');
}

class Node {
int data;
Node? next;

Node( this.data) ;
}

class LinkedList {
Node? head;

void addNode(int data) {
Node newNode = Node(data);
newNode.next = head;
head = newNode;
}
}

Node? findMiddleNode(Node? head) {
if (head == null) {
return null;
}

Node? slowPointer = head;
Node? fastPointer = head;

// Move the slow pointer one step at a time and the fast pointer two steps at a time
while (fastPointer != null && fastPointer.next != null) {
slowPointer = slowPointer!.next;
fastPointer = fastPointer.next!.next;
}

// The slow pointer is at the middle node
return slowPointer;
}
---------------------------------------
void main() {
// Create a sample linked list
LinkedList linkedList = LinkedList();
linkedList.addNode(1);
linkedList.addNode(2);
linkedList.addNode(3);
linkedList.addNode(4);
linkedList.addNode(5);

// Print the original linked list
print('Original Linked List:');
linkedList.printList();

// Reverse the linked list
linkedList.reverse();

// Print the reversed linked list
print('Reversed Linked List:');
linkedList.printList();
}

class Node {
int data;
Node? next;

Node(this.data) ;
}

class LinkedList {
Node? head;

void addNode(int data) {
Node newNode = Node(data);
newNode.next = head;
head = newNode;
}

void reverse() {
Node? current = head;
Node? prev = null;
Node? nextNode;

while (current != null) {
nextNode = current.next;
current.next = prev;
prev = current;
current = nextNode;
}

head = prev;
}

void printList() {
Node? temp = head;
while (temp != null) {
print(temp.data);
temp = temp.next;
}
}
}
-------------------------------------
void main() {
// Create a sample linked list
LinkedList linkedList = LinkedList();
linkedList.addNode(1);
linkedList.addNode(2);
linkedList.addNode(3);
linkedList.addNode(2);
linkedList.addNode(4);
linkedList.addNode(2);
linkedList.addNode(5);

// Print the original linked list
print('Original Linked List:');
linkedList.printList();

// Remove all occurrences of the element 2
linkedList.removeAllOccurrences(2);

// Print the linked list after removal
print('Linked List after Removing All Occurrences of 2:');
linkedList.printList();
}

class Node {
int data;
Node? next;

Node( this.data);
}

class LinkedList {
Node? head;

void addNode(int data) {
Node newNode = Node(data);
newNode.next = head;
head = newNode;
}

void removeAllOccurrences(int target) {
while (head != null && head!.data == target) {
head = head!.next;
}

Node? current = head;

while (current != null && current.next != null) {
if (current.next!.data == target) {
current.next = current.next!.next;
} else {
current = current.next;
}
}
}

void printList() {
Node? temp = head;
while (temp != null) {
print(temp.data);
temp = temp.next;
}
}
}
