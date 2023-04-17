# PhoneBook-Management-System-
PhoneBook Management System In C programming Project
#include <stdio.h>
#include <string.h>

#define MAX_CONTACTS 100 // Maximum number of contacts

struct Contact {
    char name[50];
    char phone[20];
    char email[50];
    char address[50];
};

int main() {
    struct Contact contacts[MAX_CONTACTS];
    int num_contacts = 0;
    int choice, i;
    char search_name[50];
    //char email[50];

    while (1) {
        printf("Phonebook Management System\t\n");
        printf("1. Add a new contact\n");
        printf("2. Edit an existing contact\n");
        printf("3. Delete a contact\n");
        printf("4. Search for a contact\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: // Add a new contact
                if (num_contacts >= MAX_CONTACTS) {
                    printf("Phonebook is full!\n");
                } else {
                    struct Contact new_contact;
                    printf("Enter name: ");
                    scanf("%s", new_contact.name);
                    printf("Enter phone number: ");
                    scanf("%s", new_contact.phone);
                    printf("Enter email: ");
                    scanf("%s",new_contact.email);
                    printf("Enter address: ");
                    scanf("%s",new_contact.address);
                    contacts[num_contacts] = new_contact;
                    num_contacts++;
                    printf("Contact added successfully!\n");
                }
                break;

            case 2: // Edit an existing contact
                printf("Enter name to edit: ");
                scanf("%s", search_name);
                for (i = 0; i < num_contacts; i++) {
                    if (strcmp(contacts[i].name, search_name) == 0) {
                        printf("Enter new phone number: ");
                        scanf("%s", contacts[i].phone);
                        printf("Contact edited successfully!\n");
                        break;
                    }
                }
                if (i == num_contacts) {
                    printf("Contact not found!\n");
                }
                break;

            case 3: // Delete a contact
                printf("Enter name to delete: ");
                scanf("%s", search_name);
                for (i = 0; i < num_contacts; i++) {
                    if (strcmp(contacts[i].name, search_name) == 0) {
                        for (int j = i; j < num_contacts - 1; j++) {
                            contacts[j] = contacts[j + 1];
                        }
                        num_contacts--;
                        printf("Contact deleted successfully!\n");
                        break;
                    }
                }
                if (i == num_contacts) {
                    printf("Contact not found!\n");
                }
                break;

            case 4: // Search for a contact
                printf("Enter name to search: ");
                scanf("%s", search_name);
                for (i = 0; i < num_contacts; i++) {
                    if (strcmp(contacts[i].name, search_name) == 0) {
                        printf("Name: %s\nPhone: %s\nEmail: %s\nAddress: %s\n",contacts[i].name, contacts[i].phone,contacts[i].email,contacts[i].address);
                        break;
                    }
                }
                if (i == num_contacts) {
                    printf("Contact not found!\n");
                }
                break;

            case 5: // Exit
                printf("Thank you for using Phonebook Management System!\n");
                return 0;

            default:
                printf("Invalid choice!\n");
        }
    }
    return 0;
}
