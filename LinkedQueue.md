#include<iostream>
using namespace std;
class linkedqueue{
	
	private:
	struct node{
		
		int item;
		node *next;
	};
	
     	node *rear;
		node *front;	
	    int count;

   public:
   	
   	linkedqueue(){
   		rear = NULL;
   		front = NULL;
   		count = 0;
	   }
   	
	bool isempty (){
		return count == 0;
	}
	
	void enqueue (int element){
		
		node *new_ptr = new node;
		new_ptr -> item = element;
		new_ptr -> next = NULL;
		
		if (isempty()){
			rear = front = new_ptr;
		}
		
		else{
			rear -> next = new_ptr;
			rear = new_ptr;
		}
		
		count++;
	}
	
	
	void dequeue (){
		
		if (isempty())
		cout << "Queue is empty\n";
		
		else if (count == 1) {
			delete front;
			rear = NULL;
			count = 0;
		}
		
		else {
			node *temp = front;
			front = front -> next;
			temp -> next = NULL;
			delete temp;
			count--;
		}
	}
	
	int getfront (){
		if (isempty())
		return -1;
		
		else 
		return front -> item;
	}
	
	int getrear (){
		if(isempty())
		return -1;
		
		else 
		return rear -> item;
	}
	
	
	void display (){
		node *cur = front;
		while (cur != NULL){
			cout << cur -> item << " ";
			cur = cur -> next;
		}
	}
	
	
	void clear (){
	  node *cur;
	  while(front != NULL){
	  	cur = front;
	  	front = front -> next;
	  	delete cur;
	  }
	  rear = NULL;
	  count = 0;	
	}
	
};

int main (){
	linkedqueue q1;
	q1.enqueue(100);
	q1.dequeue();
	cout << q1.isempty() <<  " This mean the queue now is empty \n\n";
	
	q1.enqueue(200);
	q1.enqueue(500);
	q1.enqueue(300);
	q1.enqueue(400);
	q1.enqueue(900);
	q1.display();
	cout << "\nFront is : " << q1.getfront() << "\nRear is : " << q1.getrear() << "\n\n";
	
	q1.dequeue();
	//cout << "\n\n";
	q1.display();
	cout << "\nFront is : " << q1.getfront() << "\nRear is : " << q1.getrear() << "\n\n";
	
	q1.clear();
	cout << q1.isempty() << " This mean the queue now is empty \n\n";
	
	q1.enqueue(1000);
	q1.enqueue(2000);
	q1.enqueue(3000);
	q1.enqueue(5000);
	q1.display();
	cout << "\nFront is : " << q1.getfront() << "\nRear is : " << q1.getrear() << "\n\n";
}
