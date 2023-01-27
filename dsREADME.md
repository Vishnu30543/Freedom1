# Freedom1
#include<stdio.h>
#include<stdlib.h>
void insertatfirst();
void insertatpos();
void insertatlast();
void deleteatfirst();
void deleteatpos();
void deleteatlast();
void display();
struct node
{
	int data;
	struct node *next;
};
struct node *head=NULL;

int main()
{
	int choise;
	while(1)
	{
		printf("1) Insert at First\n2) Insert at Position\n3) Insert at Last\n");
		printf("4) Delete at First\n5) Delete at Position (Position)\n6) Delete at Last\n");
		printf("7) Exit");
		printf("\nEnter your choise : ");
		scanf("%d",&choise);
		if(choise==1)
			insertatfirst();
		else if(choise==2)
			insertatpos();
		else if(choise==3)
			insertatlast();
		else if(choise==4)
			deleteatfirst();
		else if(choise==5)
			deleteatpos();
		else if(choise==6)
			deleteatlast();
		else if(choise==7)
			break;										
	}
}

void insertatfirst()
{
	int value;
	struct node *newnode;
	newnode=(struct node *)malloc(sizeof(struct node));
	printf("\nEnter value ");
	scanf("%d",&value);
	newnode->data=value;
	if(head==NULL)
	{
		newnode->next=NULL;
		head=newnode;
	}
	else
	{
		newnode->next=head;
		head=newnode;
	}
	display();
}
void insertatpos()
{
	int value,i,pos;
	struct node *newnode;
	newnode=(struct node *)malloc(sizeof(struct node));
	printf("\nEnter value ");
	scanf("%d",&value);
	newnode->data=value;
	printf("\nEnter position ");
	scanf("%d",&pos);
	if(head==NULL && pos==1)
	{
		newnode->next=NULL;      //insertatfirst();
		head=newnode;
	}
	else
	{
		struct node *t,*p;
		t=head;
		for(i=1; i<pos-1; i++)
		{
			t=t->next;
			if(t==NULL)
			{
				printf("\nPosition not found\n");
			}
		}
		newnode->next=t->next->next;
		t->next=newnode;
	}
	display();
}
void insertatlast()
{
	int value;
	struct node *newnode;
	newnode=(struct node *)malloc(sizeof(struct node));
	printf("\nEnter value ");
	scanf("%d",&value);
	newnode->data=value;
	if(head==NULL)
	{
		newnode->next=NULL;
		head=newnode;
	}
	else
	{
		int i;
		struct node *t;
		while(t->next!=NULL)
		{
			t=t->next;
		}
		t->next=newnode;
		newnode->next=NULL;
	}
	display();
}
void deleteatfirst()
{
	if(head==NULL)
	{
		printf("\nList is Empty\n");
		// return;
	}
	else if(head->next==NULL)
	{
		printf("%d is Cleared\n",head->data);
		head=NULL;
		free(head);
	}
	else
	{
		struct node *t;
		t=head;
		printf("\n%d is Cleared\n",head->data);
		head=head->next;
		free(t);
	}
	display();
}
void deleteatpos()
{
	if(head==NULL)
	{
		printf("\nList is Empty\n");
		// return;
	}
	else if(head->next==NULL)
	{
		printf("%d is Cleared\n",head->data);
		head=NULL;
		free(head);
	}
	else
	{
		int i,pos;
		struct node *t,*p;
		t=head;
		printf("\nEnter position ");
		scanf("%d",&pos);
		for(i=1; i<pos-1; i++)
		{
			t=t->next;
			if(t==NULL)
			{
				printf("\nPosition not found\n");
			}
		}
		p=t->next;
		t->next=p->next;
		printf("\n%d is Cleared\n",p->data);
		free(p);
	}
	display();
}
void deleteatlast()
{
	if(head==NULL)
	{
		printf("\nList is Empty\n");
		// return;
	}
	else if(head->next==NULL)
	{
		printf("%d is Cleared\n",head->data);
		head=NULL;
		free(head);
	}
	else
	{
		struct node *t,*p;
		while(t->next->next!=NULL)
		{
			t=t->next;
		}
		p=t->next;
		printf("\n%d is Cleared\n",p->data);
		free(p);
	}
	display();
}
void display()
{
	struct node *t;
	t=head;
	printf("\nElements : ");
	while(t!=NULL)
	{
		printf(" %d",t->data);
		t=t->next;
	}
	printf("\n");
}

