# Library-management-system-
C program 
#include <stdio.h>
#include <string.h>

struct Book {
    int id;
    char name[50];
    char author[50];
    int quantity;
};

int main() {
    struct Book b[100];
    int choice, count = 0, i, searchId, found;

    do {
        printf("\n===== LIBRARY MANAGEMENT SYSTEM =====\n");
        printf("1. Add Book\n");
        printf("2. Display Books\n");
        printf("3. Search Book\n");
        printf("4. Issue Book\n");
        printf("5. Return Book\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {

        case 1:
            printf("\nEnter Book ID: ");
            scanf("%d", &b[count].id);
            printf("Enter Book Name: ");
            scanf(" %[^\n]", b[count].name);
            printf("Enter Author Name: ");
            scanf(" %[^\n]", b[count].author);
            printf("Enter Quantity: ");
            scanf("%d", &b[count].quantity);
            count++;
            printf("Book added successfully!\n");
            break;

        case 2:
            printf("\n--- Book List ---\n");
            for (i = 0; i < count; i++) {
                printf("ID: %d | Name: %s | Author: %s | Qty: %d\n",
                       b[i].id, b[i].name, b[i].author, b[i].quantity);
            }
            break;

        case 3:
            found = 0;
            printf("\nEnter Book ID to search: ");
            scanf("%d", &searchId);
            for (i = 0; i < count; i++) {
                if (b[i].id == searchId) {
                    printf("Book Found!\n");
                    printf("Name: %s\nAuthor: %s\nQuantity: %d\n",
                           b[i].name, b[i].author, b[i].quantity);
                    found = 1;
                    break;
                }
            }
            if (!found)
                printf("Book not found!\n");
            break;

        case 4:
            printf("\nEnter Book ID to issue: ");
            scanf("%d", &searchId);
            for (i = 0; i < count; i++) {
                if (b[i].id == searchId && b[i].quantity > 0) {
                    b[i].quantity--;
                    printf("Book issued successfully!\n");
                    break;
                }
            }
            break;

        case 5:
            printf("\nEnter Book ID to return: ");
            scanf("%d", &searchId);
            for (i = 0; i < count; i++) {
                if (b[i].id == searchId) {
                    b[i].quantity++;
                    printf("Book returned successfully!\n");
                    break;
                }
            }
            break;

        case 6:
            printf("Thank you! Exiting...\n");
            break;

        default:
            printf("Invalid choice!\n");
        }

    } while (choice != 6);

    return 0;
}
