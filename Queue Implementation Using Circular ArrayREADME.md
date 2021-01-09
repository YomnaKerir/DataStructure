#include<iostream>
#include<cassert>
using namespace std;
const int maxsize = 100;
class circularqueue {
	
	int rear;
	int front;
	int count;
	int arr[maxsize];
	public:
		
		circularqueue(){
			front = 0;
			rear = maxsize -1;
			count = 0;
		}
		
		bool isempty(){
			return count == 0;
		}
		
		bool isfull(){
			return count == maxsize;
		}
		
		void enqueue (int element){
			if (isfull())
			cout << "Sorry, Queue is full\n";
			
			else{
				rear = (rear + 1) % maxsize;
				arr[rear] = element;
				count++;
			}
		}
		
		void dequeue (){
			if(isempty())
			cout << "Sorry , Queue is empty\n";
			
			else{
				front = (front + 1) % maxsize;
				count--;
			}
		}
		
		int getfront (){
			assert (!isempty());
			return arr[front];
		}
		
		int getrear (){
			assert (!isempty());
			return arr[rear];
		}
		
		void print (){
			for (int i = front; i != rear + 1; i = (i + 1) % maxsize){
				cout << arr[i] << endl;
			}
		}
};

int main (){
	
	circularqueue Q1;
	Q1.enqueue(10);
	Q1.enqueue(20);
	Q1.enqueue(30);
	Q1.print();
	cout << "The front before dequeue is : " << Q1.getfront() << endl;
	Q1.dequeue();
	
	cout << "\nThe front now is : " << Q1.getfront();
	cout << "\nThe elements in queue now are  : " << endl;
	Q1.print(); 
	
}
