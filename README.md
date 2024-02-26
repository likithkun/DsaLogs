<h2>Jan 15</h2> 

started with linked list.


### Q1.  Construct a LL from a vector 

```cpp
Node* constructLL(vector<int>& arr) {
    //declare a new node as head
    Node* head = new Node(arr[0]);
    //temp initially pointing to head
    Node* mover = head ;
    // iterate and add elements individually 
    for(int i = 1; i< arr.size(); i++){
	Node* temp = new Node(arr[i]);
	mover->next = temp;
	mover = mover->next;
	}
    //return the on pointing to head
    return head; 
   }
```

### Q2. Inserting a node in a linked list 
```
/*iterate till the positon create a new node 
add the desired value make the prev node point to
the newly created node ... and the new node will 
point to the next node ..*/
```
	
### Q3. Delete a node in LL
```
/* les say the node to delete is node x..
copy the data from x+1 node to x node and 
make the x node point to x+2 node.*/
```
	

<h2>Jan 18</h2> 


### Q1. Merge two sorted LL (solve in IOT lab )

```cpp
/*You take two pointer make sure that the l1 is always 
pointing to the smaller lx->val , iterate through l1
when u find a val at l1 greater than l2-> val make the
prev point to the smaller val of l2 (till now you have 
maintained a value prev to l1 0.. swap l1 and l2
so that l1 always points to the smaller element continue 
till one of the list exhauts.. */

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    if(l1 == NULL) return l2;
    if(l2 == NULL) return l1;

    if(l1->val > l2->val) swap(l1,l2);
    ListNode* res = l1;

    while(l1 != NULL && l2 != NULL ){

	ListNode* temp = NULL;
	while(l1 != NULL && l1->val <= l2-> val){
	    temp = l1;
	    l1 = l1->next;
	}

	temp->next = l2;
	swap(l1,l2);
    }
    return res;
}
/*You take two pointer make sure that the l1 is always 
pointing to the smaller lx->val , iterate through l1
when u find a val at l1 greater than l2-> val make the
prev point to the smaller val of l2 (till now you have 
maintained a value prev to l1 0.. swap l1 and l2
so that l1 always points to the smaller element continue 
till one of the list exhauts.. */

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    if(l1 == NULL) return l2;
    if(l2 == NULL) return l1;

    if(l1->val > l2->val) swap(l1,l2);
    ListNode* res = l1;

    while(l1 != NULL && l2 != NULL ){

	ListNode* temp = NULL;
	while(l1 != NULL && l1->val <= l2-> val){
	    temp = l1;
	    l1 = l1->next;
	}

	temp->next = l2;
	swap(l1,l2);
    }
    return res;
}
```

### Q2. Delete Nth node from behind of a LL
```cpp
/*Nth from behind is len - n + 1 th node from the begining
Declare two pointers pointing to head move only  the 
fast pointer n positions from the start.. then move both 
the slow pointer and fast pointer in steps of one until 
the fast pointer hits the end . now the slow pointer is 
nth position from behind.*/

ListNode* removeNthFromEnd(ListNode* head, int n) {
	
	ListNode* fast = head;
	ListNode* slow = head;
	ListNode* prev = nullptr;  // Keep track of the previous node

	// Move fast n nodes ahead
	for (int i = 0; i < n; i++) {
		if (fast == nullptr) {
		    // Handle the case where n is greater than the length of the list
		    return head;
		}
		fast = fast->next;
	}

	// Move both pointers until fast reaches the end
	while (fast != nullptr) {
		prev = slow;
		slow = slow->next;
		fast = fast->next;
	}

	// Remove the nth node from the end
	if (prev == nullptr) {
		// If prev is null, it means the head needs to be removed
		ListNode* newHead = head->next;
		delete head;
		return newHead;
	} else {
		prev->next = slow->next;
		delete slow;
		return head;
}
```
	
### Q3. Add two numbers represented as LL

```cpp
/*
The LL given are in reverse order so you do basic 
arithmetic math .. use carry what you need to be carefull of 
is the number aren't gonna contain equal number of digits ...
create a new LL and store the sum in it .. then obviously return
it.*/

ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    ListNode *dummy = new ListNode(); 
    ListNode *temp = dummy; 
    int carry = 0;
    while( (l1 != NULL || l2 != NULL) || carry) {
	int sum = 0; 
	if(l1 != NULL) {
	    sum += l1->val; 
	    l1 = l1 -> next; 
	}
	
	if(l2 != NULL) {
	    sum += l2 -> val; 
	    l2 = l2 -> next; 
	}
	
	sum += carry; 
	carry = sum / 10; 
	ListNode *node = new ListNode(sum % 10); 
	temp -> next = node; 
	temp = temp -> next; 
    }
    return dummy -> next; 
 }
 ```
	 
### Q4. Delete given Node ,

```cpp
/*Think out of the box you don't exactly need to delete the 
node you can transfer the next nodes value to current and
delete the next and pretend the given node was deleted .*/

void deleteNode(ListNode* t) {
	t->num = t->next->num;
	ListNode* dell = t->next;
	t->next = t->next->next;
	delete(dell);
	return;
}
```
	
	
	


	
	
	
	
	


	 

	 
	
	
	
