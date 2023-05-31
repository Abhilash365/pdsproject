# pdsproject

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <malloc.h>

#define MAX_TICKETS 120
#define size 5
#define MAX_SIZE 20

// to book a ticket
int ticketNumber;
struct Ticket
{
	char name[50];
	int age[100];
	char boarding[500];
	char isCancelled;
	char destination[50];
	int date[3];
	int seatno;
};

struct TrainTicketSystem
{
	struct Ticket tickets[MAX_TICKETS];
	int numTickets;
};

void bookTicket(struct TrainTicketSystem *system)
{

	struct Ticket newTicket;
	newTicket.seatno = system->numTickets + 1;

	printf("-----------------------------------------------------------------------------");
	printf("\nTr.No\tName\t\t\tDestinations\t\tCharges\t\tTime\n");
	printf("-----------------------------------------------------------------------------");
	printf("\n50001\tIITBhubaneswar Express\tBhubaneswarto Cuttack    \tFare=150/-\t\t9am");
	printf("\n50002\tIITBhubaneswar Express\tBhubaneswar To Khurda    \tFare=150/-\t\t12pm");
	printf("\n50003\tIITBhubaneswar Express\tBhubaneswar To Sompet   \tFare=260/\t\t8am");
	printf("\n50004\tIITBhubaneswar Express\tBhubaneswar To Ichapuram\tFare=250/-\t\t11am");
	printf("\n50005\tIITBhubaneswar Express\tBhubaneswar To Brahampur  \tFare=225/\t\t7am");
	printf("\n50006\tIITBhubaneswar Express\tBhubaneswar To Balugon    \tFare=200/-\t\t9.30am");
	printf("\n50007\tIITBhubaneswar Express\t BhubaneswarTo Chatrapur  \tFare=150/-\t\t1pm");
	printf("\n");

	printf("Enter your name: ");
	fgets(newTicket.name, sizeof(newTicket.name), stdin);
	newTicket.name[strcspn(newTicket.name, "\n")] = '\0';

	printf("enter your age: ");
	fgets(newTicket.age, sizeof(newTicket.age), stdin);
	newTicket.age[strcspn(newTicket.age, "\n")] = '\0';

	printf("Enter the boarding station: ");
	fgets(newTicket.boarding, sizeof(newTicket.boarding), stdin);
	newTicket.boarding[strcspn(newTicket.boarding, "\n")] = '\0';

	printf("Enter the destination station: ");
	fgets(newTicket.destination, sizeof(newTicket.destination), stdin);
	newTicket.destination[strcspn(newTicket.destination, "\n")] = '\0';

	printf("Enter the date(dd/mm/yy) format: ");
	fgets(newTicket.date, sizeof(newTicket.date), stdin);
	newTicket.date[strcspn(newTicket.date, "\n")] = '\0';

	printf("Train number is : 10001\n");

	if (strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Cuttack") == 0 || strcmp(newTicket.boarding, "Cuttack") == 0 && strcmp(newTicket.destination, "Bhubaneswar") == 0)
		printf("Fare=180/-\n");

	else if (strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Khurda") == 0 || strcmp(newTicket.boarding, "Khurda") == 0 && strcmp(newTicket.destination, "Bhubaneswar") == 0)
		printf("Fare=150/-\n");
	else if (strcmp(newTicket.boarding, "Sompet") == 0 && strcmp(newTicket.destination, "Bhubaneswar") == 0 || strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Sompet") == 0)
		printf("Fare=260/-\n");

	else if (strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Ichapuram") || strcmp(newTicket.boarding, "Ichapuram") == 0 && strcmp(newTicket.destination, "Bhubaneswar") == 0)

		printf("Fare=250/-\n");

	else if (strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Brahampur") || strcmp(newTicket.boarding, "Brahampur") == 0 && strcmp(newTicket.destination, "Bhubaneswar") == 0)
		printf("Fare=225/-\n");

	else if (strcmp(newTicket.boarding, "Balugon") == 0 && strcmp(newTicket.destination, "Bhubaneswar") || strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Balugon") == 0)
		printf("Fare=200/-\n");

	else if (strcmp(newTicket.boarding, "Bhubaneswar") == 0 && strcmp(newTicket.destination, "Chatrapur") || strcmp(newTicket.boarding, "Chatrapur") == 0 && strcmp(newTicket.destination, "Bhubaneswar") == 0)

		printf("Fare=150/-\n");
	else
	{
		printf("Sorry, Your Destination can't Be Reached\n");
	}

	newTicket.isCancelled = 0;

	system->tickets[system->numTickets++] = newTicket;

	printf("Ticket booked successfully!\n Your seat number is %d.\n", newTicket.seatno);
}

// to cancel ticket
void cancelTicket(struct TrainTicketSystem *system)
{
	if (system->numTickets == 0)
	{
		printf("No tickets booked yet.\n");
		return;
	}
	printf("-----------------------------------------------------------------------------");
	printf("\nTr.No\tName\t\t\tDestinations\t\tCharges\t\tTime\n");
	printf("-----------------------------------------------------------------------------");
	printf("\n50001\tIITBhubaneswar Express\tBhubaneswarto Cuttack    \tFare=150/-\t\t9am");
	printf("\n50002\tIITBhubaneswar Express\tBhubaneswar To Khurda    \tFare=150/-\t\t12pm");
	printf("\n50003\tIITBhubaneswar Express\tBhubaneswar To Sompet   \tFare=260/\t\t8am");
	printf("\n50004\tIITBhubaneswar Express\tBhubaneswar To Ichapuram\tFare=250/-\t\t11am");
	printf("\n50005\tIITBhubaneswar Express\tBhubaneswar To Brahampur  \tFare=225/\t\t7am");
	printf("\n50006\tIITBhubaneswar Express\tBhubaneswar To Balugon    \tFare=200/-\t\t9.30am");
	printf("\n50007\tIITBhubaneswar Express\t BhubaneswarTo Chatrapur  \tFare=150/-\t\t1pm");
	printf("\n");

	printf("Enter the seat number to cancel (1-%d): ", system->numTickets);
	int seatno;
	scanf("%d", &seatno);
	getchar();

	if (seatno < 1 || ticketNumber > system->numTickets)
	{
		printf("Invalid seat number.\n");
		return;
	}

	struct Ticket *ticket = &system->tickets[seatno - 1];

	if (ticket->isCancelled)
	{
		printf("Ticket is already cancelled.\n");
		return;
	}

	ticket->isCancelled = 1;

	printf("Ticket cancellation successful!\n");
}

// reserving

typedef struct NODE
{
	int reg_no;
	int age;
	char destination[MAX_SIZE];
	char boarding[MAX_SIZE];
	char name[MAX_SIZE];
	char date[MAX_SIZE];
	struct NODE *next;
} node;

node *deq();
void create();
int reserve();
int cancel(int);
void enq(node *);
void display();

node *start;
node *front;
node *rear;
int count = 0;
int num = 0;

void create()
{
	start = (node *)malloc(sizeof(node));
	start->reg_no = 1;
	printf("-----------------------------------------------------------------------------");
	printf("\nTr.No\tName\t\t\tDestinations\t\tCharges\t\tTime\n");
	printf("-----------------------------------------------------------------------------");
	printf("\n50001\tIITBhubaneswar Express\tBhubaneswarto Cuttack    \tFare=150/-\t\t9am");
	printf("\n50002\tIITBhubaneswar Express\tBhubaneswar To Khurda    \tFare=150/-\t\t12pm");
	printf("\n50003\tIITBhubaneswar Express\tBhubaneswar To Sompet   \tFare=260/\t\t8am");
	printf("\n50004\tIITBhubaneswar Express\tBhubaneswar To Ichapuram\tFare=250/-\t\t11am");
	printf("\n50005\tIITBhubaneswar Express\tBhubaneswar To Brahampur  \tFare=225/\t\t7am");
	printf("\n50006\tIITBhubaneswar Express\tBhubaneswar To Balugon    \tFare=200/-\t\t9.30am");
	printf("\n50007\tIITBhubaneswar Express\t BhubaneswarTo Chatrapur  \tFare=150/-\t\t1pm");
	printf("\n");

	printf("Name: ");
	scanf("%s", start->name);
	printf("Age : ");
	scanf("%d", &start->age);
	printf("Enter Boarding:");
	scanf("%s", start->boarding);
	printf("Enter destination:");
	scanf("%s", start->destination);
	printf("Date:");
	scanf("%s", start->date);
	start->next = NULL;
	num++;
}

int reserve()
{

	if (start == NULL)
	{
		create();
		return 1;
	}

	else
	{
		node *temp, *new_node, *prev;

		new_node = (node *)malloc(sizeof(node));

		printf("Name: ");
		scanf("%s", new_node->name);
		printf("Age : ");
		scanf("%d", &(new_node->age));
		printf("Boarding:");
		scanf("%s", new_node->boarding);
		printf("Destination:");
		scanf("%s", new_node->destination);
		printf("Date:");
		scanf("%s", new_node->date);

		new_node->next = NULL;

		temp = start;
		int i = 1;
		if (temp->reg_no == 0)
		{
			temp->reg_no = 1;
			strcpy(temp->name, new_node->name);
			temp->age = new_node->age;
			num++;
			return 1;
		}
		while (temp->next != NULL)
		{
			if (temp->reg_no != i++)
				break;

			prev = temp;
			temp = temp->next;
		}

		if (num < size)
		{
			num++;
			i++;
			if (temp->reg_no == (prev->reg_no + 1) || i == 2) // If all gaps were filled
			{
				new_node->reg_no = i;
				temp->next = new_node;
				return i;
			}
			else // Filling the gaps
			{
				new_node->next = temp;
				prev->next = new_node;
				new_node->reg_no = (temp->reg_no) - 1;
				printf("reg = %d\n", new_node->reg_no);
				return new_node->reg_no;
			}
		}

		else
		{
			enq(new_node);
			return 0;
		}
	}
}

int cancel(int reg)
{
	node *ptr, *preptr, *new;
	ptr = start;
	preptr = NULL;
	if (start == NULL)
		return -1;

	if (ptr->next == NULL && ptr->reg_no == reg) // If only 1 person in reservation
	{
		start = NULL;
		num--;
		free(ptr);
		return 1;
	}

	else
	{
		if (reg == 1)
		{
			ptr->reg_no = 0;
			new = deq(reg);
			if (new != NULL)
			{
				ptr->reg_no = 1;
				strcpy(ptr->name, new->name);
				ptr->age = new->age;
				num++;
				return 1;
			}
		}

		else
		{
			while (ptr->reg_no != reg && ptr->next != NULL)
			{
				preptr = ptr;
				ptr = ptr->next;
			}

			if (ptr->next == NULL && ptr->reg_no != reg)
				return -1;
			else
				preptr->next = ptr->next;

			free(ptr);
			new = deq(reg);
			num--;
			if (new != NULL)
			{
				node *waiting = start;
				while (waiting->reg_no != (new->reg_no - 1))
					waiting = waiting->next;

				new->next = waiting->next;
				waiting->next = new;
				num++;

				return 1;
			}
		}
	}
}

void enq(node *new_node)
{
	if (rear == NULL)
	{
		rear = new_node;
		rear->next = NULL;
		front = rear;
	}
	else
	{
		node *temp;
		temp = new_node;
		rear->next = temp;
		temp->next = NULL;
		rear = temp;
	}
	count++;
}

node *deq(int reg)
{
	node *front1;
	front1 = front;
	if (front == NULL)
		return NULL;
	else

		count--;
	if (front->next != NULL)
	{
		front = front->next;
		front1->next = NULL;
		front1->reg_no = reg;
		return front1;
	}
	else
	{
		front = NULL;
		rear = NULL;
		front1->reg_no = reg;
		return front1;
	}
}

void display()
{
	node *temp;
	temp = start;
	printf("-----------------------------------------------------------------------------");
	printf("\nTr.No\tName\t\t\tDestinations\t\tCharges\t\tTime\n");
	printf("-----------------------------------------------------------------------------");
	printf("\n50001\tIITBhubaneswar Express\tBhubaneswarto Cuttack    \tFare=150/-\t\t9am");
	printf("\n50002\tIITBhubaneswar Express\tBhubaneswar To Khurda    \tFare=150/-\t\t12pm");
	printf("\n50003\tIITBhubaneswar Express\tBhubaneswar To Sompet   \tFare=260/\t\t8am");
	printf("\n50004\tIITBhubaneswar Express\tBhubaneswar To Ichapuram\tFare=250/-\t\t11am");
	printf("\n50005\tIITBhubaneswar Express\tBhubaneswar To Brahampur  \tFare=225/\t\t7am");
	printf("\n50006\tIITBhubaneswar Express\tBhubaneswar To Balugon    \tFare=200/-\t\t9.30am");
	printf("\n50007\tIITBhubaneswar Express\t BhubaneswarTo Chatrapur  \tFare=150/-\t\t1pm");

	while (temp != NULL)
	{
		if (temp->reg_no != 0)
		{
			printf("\nRegistration Number: %d\n", temp->reg_no);
			printf("Name : %s\n", temp->name);
			printf("Age : %d\n\n", temp->age);
		}
		temp = temp->next;
	}
}

int main()
{
	int choice, status = 0, canc = 0, reg = 0;
	start = NULL;

	rear = NULL;
	front = NULL;
	struct TrainTicketSystem ticketSystem;
	ticketSystem.numTickets = 0;

	while (1)
	{
		printf("\n==== Train Ticket Management System ====\n");
		printf("1. Book Ticket\n");
		printf("2. Cancel Ticket\n");
		printf("3. Reserve Ticket\n");
		printf("4. Display Reserved Trains\n");
		printf("5. Exit\n");

		int choice;
		printf("Enter your choice (1-5): ");
		scanf("%d", &choice);
		getchar(); // consume the newline character
		switch (choice)
		{
		case 1:
			bookTicket(&ticketSystem);
			break;

		case 2:
			cancelTicket(&ticketSystem);
			break;

		case 3:
			status = reserve();
			if (status == 0)
				printf("\nBooking Full!! \nYou are added to waiting list. Waiting list number %d", count);
			else
				printf("\nBooking Successful!!! Enjoy your journey! Your Reg No. is %d\n", status);
			break;

		case 4:
			display(&ticketSystem);
			break;
		case 5:
			printf("Thank you for using the Train Ticket Management System!\n");
			exit(0);

		default:
			printf("Invalid choice. Please try again.\n");
			break;
		}
	}
}
