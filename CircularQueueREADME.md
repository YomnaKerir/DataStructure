#include<iostream>
#include<cmath>
#include<cassert>
using namespace std;
class queue {
	int rear;
	int front;
	int *arr;
	int maxsize;
	int count;
	
	public:
		
		queue (int size){
			if (size < 0)
			maxsize = abs(size);
			
			else
			maxsize = size;
			
		 front = 0;
		 count = 0;
		 arr = new int[maxsize];
		 rear = maxsize - 1;
		}
		
		bool isempty(){
			return count == 0;
		}
		
		bool isfull (){
			return count == maxsize;
		}
		
		void enqueue (int element){
			if (isfull())
			cout << "Sorry, Qeueu is full\n";
			
			else{
				
				rear = (rear + 1) % maxsize;
				arr[rear] = element;
				count++;
			}
		}
		
		void dequeue (){
			if(isempty())
			cout << "Sorry , queue is empty\n";
			
			else{
				
				front = (front + 1) % maxsize;
				count--;
			}
		}
		
		int getfront(){
			assert (! isempty());
			return arr[front];
		}
		
		int getrear(){
			assert(! isempty());
			return arr[rear];
		}
		
		int search (int element){
			int pos = -1;
			if( !isempty ()){
				for(int i = front; i != rear; i = (i + 1) % maxsize){
					if (arr[i] == element){
						pos = i;
						break;
					}
				}
				
				if (pos == -1){
					if (arr[rear] == element)
					pos = rear;
				}
				else 
				cout << "Queue is empty\n";
			}
			return pos;
		}
		
		void display (){
			if(isempty())
			cout << "Sorry, queue is empty\n";
			
			else{
				
				for (int i = front; i != rear ; i = (i + 1) % maxsize){
					cout << arr[i] << " ";
				}
				cout << arr[rear] << endl;
			}
		}
};
int main (){
	queue q1(5);
	q1.enqueue(120);
	q1.enqueue(150);
	q1.enqueue(900);
	q1.enqueue(2000);
	q1.enqueue(3000);
	q1.display();
	q1.enqueue(4000);
 
    int index = q1.search(4000);
    if (index == -1)
    cout << "Not Found\n";
    
    else 
    cout << "Found at index " << index; 
}
