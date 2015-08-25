#include<iostream>
#include<stdlib.h>
using namespace std;
class linklist {
    class node {
        public :
            int data;
            node * link;
    };
    node * start, *ptr ; 
    public :
        linklist () {
            start = NULL ; 
        }
        void insert();
        void del(int );
        void display();
};
void linklist :: insert() 
{
     node *new_node = new node;
     int x;
     cout << "Enter element \n";
     cin >> x;
     new_node->data = x;
     new_node->link = NULL;
     if ( start == NULL ) {
         start = new_node;
         ptr =start;
     }
    else {
     	ptr->link = new_node ;
     	ptr = new_node;
    }
}
void linklist :: del(int val)
{   node *prev;
    ptr = start ;
    if ( start->data == val ) {
    	start = start->link;
	return ;
    }
    while( ptr -> data != val && ptr != NULL) {
  	prev = ptr;
    	ptr = ptr->link;
    }
    if( ptr == NULL) {
	cout <<  val <<" is not present in list.Please enter valid element\n";
	return;
    }
    else
	prev -> link = ptr -> link;
}
void linklist ::display() 
{
    ptr = start;
    if( ptr == NULL) {
   	cout << "No elements in list \n";
	return ;
    }
    while( ptr != NULL) {
    	cout << ptr -> data << " " ;
     	ptr = ptr -> link;
    }
} 
    
    
int main()
{
    linklist l;
    int choice, val ;
    while (1) {
    	cout <<"Enter 1 to insert\nEnter 2 to delete\nEnter 3 to display elements of linklist\nEnter 4 to exit\n";
	cin>>choice;
	switch(choice) {
	    case 1:
		l.insert(); 
    		break;
	    case 2:
		cout << "Enter element you want to delete\n";
		cin >> val ;
		l.del(val);
		break;
	    case 3:
		l.display();
		break;
	    case 4:
		exit(1);
	    default :
		cout << "Wrong entry\n";
	}
    }
    return 0;
}
