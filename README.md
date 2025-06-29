# pointer 

<pre>
'''
#include<stdio.h>
#include<math.h>
int main()
{
float a[10], *ptr, mean, std, sum=0, sumstd=0;
int n,i;//declaration of variables
printf("Enter the number of elements\n");
scanf("%d",&n);
printf("Enter the array elements\n");
for(i=0;i<n;i++)
{
scanf("%f",&a[i]);
}
ptr=a;
for(i=0;i<n;i++)
{
sum=sum+ *ptr;
ptr++;
}
mean=sum/n;
ptr=a;
for(i=0;i<n;i++)
{
sumstd=sumstd + pow((*ptr - mean),2); ptr++;
}
std= sqrt(sumstd/n);
printf("Mean=%.3f\t",mean);
printf("Standard deviation=%.3f\t",std);
return 0;
}



# string


#include<stdio.h>
int Length(char s1[]);
int compare(char s1[], char s2[]);
void concat(char s1[], char s2[]);
int main()
{
char s1[200], s2[100];
int len,res,count;
printf("\n Enter the String s1: ");
gets(s1);
printf("\n Enter the String s2 :");
gets(s2);
len = Length(s1);
printf("\n Length of the String s1 is : %d", len);
len = Length(s2);
printf("\n Length of the String s2 is : %d", len);
res = compare(s1, s2);
if(res == 0)
printf("\n Both the Strings are Equal \n");
else
printf("\n The Strings are not Equivalent \n");
concat(s1, s2);
printf("\n Concatenated string is :%s", s1);
getch();
return(0);
}
int Length(char s1)
{
intlen = 0;
while (s1[len] != '\0') 
len++;
return (len);
}
//Function to compare two strings
int compare(char s1[], char s2[])
{
int count = 0;
while(s1[count] == s2[count])
{
if(s1[count] == '\0' || s2[count] == '\0')break;
elsecount++;
}
if(s1[count] == '\0' && s2[count] == '\0')return 0;
else return -1;
}

void concat(char s1[], char s2[])
{
int i, j;
i = strlen(s1);
for (j = 0; s2[j] != '\0'; i++, j++) s1[i]
= s2[j]; //copy content of s2 to s1
s1[i] = '\0'; 
}
'''
</pre>


# matrix multiplication


# dbms

#include <stdio.h>
#include <string.h>

#define MAX_RECORDS 100


struct Record {
    int id;
    char name[50];
    int age;
};

int main() {
    struct Record records[MAX_RECORDS];
    int count = 0; 
    int choice, i, id, found;

    while (1) {
        printf("\n--- Simple DBMS Menu ---\n");
        printf("1. Create Record\n");
        printf("2. Read All Records\n");
        printf("3. Update Record\n");
        printf("4. Delete Record\n");
        printf("5. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                if (count < MAX_RECORDS) {
                    printf("Enter ID: ");
                    scanf("%d", &records[count].id);
                    printf("Enter Name: ");
                    scanf("%s", records[count].name);
                    printf("Enter Age: ");
                    scanf("%d", &records[count].age);
                    count++;
                    printf("Record created.\n");
                } else {
                    printf("Record limit reached.\n");
                }
                break;

            case 2:
                if (count > 0) {
                    printf("\n--- Records ---\n");
                    for (i = 0; i < count; i++) {
                        printf("ID: %d | Name: %s | Age: %d\n", records[i].id, records[i].name, records[i].age);
                    }
                } else {
                    printf("No records found.\n");
                }
                break;

            case 3:
                if (count == 0) {
                    printf("No records to update.\n");
                    break;
                }
                printf("Enter ID of record to update: ");
                scanf("%d", &id);
                found = 0;
                for (i = 0; i < count; i++) {
                    if (records[i].id == id) {
                        printf("Enter new Name: ");
                        scanf("%s", records[i].name);
                        printf("Enter new Age: ");
                        scanf("%d", &records[i].age);
                        printf("Record updated.\n");
                        found = 1;
                        break;
                    }
                }
                if (!found) {
                    printf("Record not found.\n");
                }
                break;

            case 4:
                if (count == 0) {
                    printf("No records to delete.\n");
                    break;
                }
                printf("Enter ID of record to delete: ");
                scanf("%d", &id);
                found = 0;
                for (i = 0; i < count; i++) {
                    if (records[i].id == id) {
                        // Shift remaining records left
                        for (int j = i; j < count - 1; j++) {
                            records[j] = records[j + 1];
                        }
                        count--;
                        printf("Record deleted.\n");
                        found = 1;
                        break;
                    }
                }
                if (!found) {
                    printf("Record not found.\n");
                }
                break;

            case 5:
                return 0;

            default:
                printf("Invalid choice.\n");
        }
    }

    return 0;
}


# calendar


#include <stdio.h>
#define MAX_EVENTS 10

struct Event {
    char date[11];
    char title[50];
    char reminder[100];
};
int main() {
    struct Event events[MAX_EVENTS];
    int count = 0;
    int choice;
    while (1) {
        printf("\n--- Simple Calendar Menu ---\n");
        printf("1. Add Event\n");
        printf("2. View Events\n");
        printf("3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                if (count >= MAX_EVENTS) {
                    printf("Event list full.\n");
                    break;
                }
                printf("Enter date (YYYY-MM-DD): ");
                scanf("%s", events[count].date);
                printf("Enter event title (one word): ");
                scanf("%s", events[count].title);
                printf("Enter reminder (one word): ");
                scanf("%s", events[count].reminder);
                count++;
                printf("Event added.\n");
                break;
            case 2:
                if (count == 0) {
                    printf("No events scheduled.\n");
                } else {
                    printf("\nYour Events:\n");
                    for (int i = 0; i < count; i++) {
                        printf("Date: %s | Title: %s | Reminder: %s\n",
                               events[i].date, events[i].title, events[i].reminder);
                    }
                }
                break;
            case 3:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice.\n");
        }
    }

    return 0;
}
