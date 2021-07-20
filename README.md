
#include<stdio.h>
#include<stdlib.h>

struct Node{
	int data;
	struct Node *next;
	struct Node *prev;
};
struct Node *start = NULL;

//function to insert element at end
void insertAtEnd(int d){
	struct Node *temp = NULL;
	temp = (struct Node*)malloc(sizeof(struct Node));
	temp->data = d;
	temp->next = NULL;
	if(start == NULL){
		temp->next = NULL;
		temp->prev = start;
		start = temp;
	}
	else{
		struct Node *t = NULL;
		t=start;
		while(t->next!= NULL){
			t=t->next;
		}
		temp->prev = t;
		t->next = temp;
		printf("%d",temp->data);
	}
}
//function to insert element at begining
void insertAtBegin(int d){
	struct Node *temp = NULL;
	temp = (struct Node*) malloc(sizeof(struct Node));
	temp->data = d;
	if(start == NULL){
		temp->prev = start;
		temp->next = NULL;
		start = temp;
	}
	else{
		temp->next = start;
		start = temp;
		temp->prev = start;
	}
}
//function to display the lists
void Display(){
	struct Node *t=NULL;
	if(start == NULL){
		printf("No elements are inside the linked list");
	}
	else{
		printf("Entered");
		t=start;
		while(t != NULL){
			printf("\n Data:%d",t->data);
			t=t->next;
		}
	}
}

//delete at first
void deleteAtBegin(){
	if(start == NULL){
		printf("There are no elements to delete");
	}
	else{
		struct Node *temp = NULL;
		temp = start;
		start = temp->next;
		temp->prev = start;
	}
}

//delete at the end function
void deleteAtEnd(){
	if(start == NULL){
		printf("No elements");
	}
	else if(start->next == NULL){
		start = NULL;
		free(start);
		printf("\tDELETED");
	}
	else{
		struct Node *t=NULL;
		t=start;
		while(t->next!=NULL){
			t=t->next;
		}
		t->prev->next = NULL;
		free(t);
	}
}
//main
int main(){
	int data,ch;
	do{
		printf("\n1.Insert\n2.Display\n3.Exit \n4.Insert at Begin \n5.Delete at Begin\n6.Delete at End\n");
		printf("\nChoose the option:");
		scanf("%d",&ch);
		switch(ch){
			case 1:
				printf("\nEnter the data:");
				scanf("%d",&data);
				insertAtEnd(data);
				break;
			case 2:
				Display();
				break;
			case 4:
				printf("\nEnter the data:");
				scanf("%d",&data);
				insertAtBegin(data);
				break;
			case 5:
				deleteAtBegin();
				break;
			case 6:
				deleteAtEnd();
				break;
		}
	}while(ch!=3);
	return 0;
}
