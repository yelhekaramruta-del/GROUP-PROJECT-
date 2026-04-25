# GROUP-PROJECT-
(Bank Management system)
#include <stdio.h>
#include <string.h>

struct Account {
    int accNo;
    char name[50];
    char password[20];
    float balance;
    float loan;
};

int main() {
    struct Account acc[100];
    int count = 0;
    int choice, i;
    float amount;
    int accNumber;
    char pass[20];

    while (1) {
        printf("\n========== BANK MANAGEMENT SYSTEM ==========\n");
        printf("1. Add New Account\n");
        printf("2. Deposit Money\n");
        printf("3. Withdraw Money\n");
        printf("4. Apply for Loan\n");
        printf("5. Show Balance\n");
        printf("6. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        if (choice == 1) {
            printf("\n--- Add New Account ---\n");

            printf("Enter Account Number: ");
            scanf("%d", &accNumber);

            int exists = 0;
            for (i = 0; i < count; i++) {
                if (acc[i].accNo == accNumber) {
                    exists = 1;
                    break;
                }
            }

            if (exists) {
                printf("Account Number Already Exists! Try another.\n");
                continue;
            }
            acc[count].accNo = accNumber;

            printf("Enter Account Holder Name: ");
            scanf(" %s", acc[count].name);

            printf("Set Password: ");
            scanf(" %s", acc[count].password);

            acc[count].balance = 0;
            acc[count].loan = 0;

            printf("Account Created Successfully!\n");
            count++;
        }

        else if (choice == 2) {
            printf("\n--- Deposit Money ---\n");

            printf("Enter Account Number: ");
            scanf("%d", &accNumber);

            printf("Enter Password: ");
            scanf(" %s", pass);

            int found = 0;

            for (i = 0; i < count; i++) {
                if (acc[i].accNo == accNumber &&
                    strcmp(acc[i].password, pass) == 0) {

                    printf("Enter amount to deposit: ");
                    scanf("%f", &amount);

                    acc[i].balance += amount;

                    printf("Deposit Successful!\n");
                    printf("New Balance: %.2f\n", acc[i].balance);

                    found = 1;
                    break;
                }
            }

            if (!found)
                printf("Account Not Found or Wrong Password!\n");
        }
        else if (choice == 3) {
            printf("\n--- Withdraw Money ---\n");

            printf("Enter Account Number: ");
            scanf("%d", &accNumber);

            printf("Enter Password: ");
            scanf(" %s", pass);

            int found = 0;

            for (i = 0; i < count; i++) {
                if (acc[i].accNo == accNumber &&
                    strcmp(acc[i].password, pass) == 0) {

                    printf("Enter amount to withdraw: ");
                    scanf("%f", &amount);

                    if (amount <= acc[i].balance) {
                        acc[i].balance -= amount;

                        printf("Withdrawal Successful!\n");
                        printf("Remaining Balance: %.2f\n", acc[i].balance);
                    } else {
                        printf("Insufficient Balance!\n");
                    }

                    found = 1;
                    break;
                }
            }

            if (!found)
                printf("Account Not Found or Wrong Password!\n");
        }

        else if (choice == 4) {
            printf("\n--- Loan Section ---\n");

            printf("Enter Account Number: ");
            scanf("%d", &accNumber);

            printf("Enter Password: ");
            scanf(" %s", pass);

            int found = 0;

            for (i = 0; i < count; i++) {
                if (acc[i].accNo == accNumber &&
                    strcmp(acc[i].password, pass) == 0) {

                    printf("Enter loan amount: ");
                    scanf("%f", &amount);

                    acc[i].loan += amount;
                    acc[i].balance += amount;

                    printf("Loan Approved!\n");
                    printf("Total Loan: %.2f\n", acc[i].loan);
                    printf("Updated Balance: %.2f\n", acc[i].balance);

                    found = 1;
                    break;
                }
            }

            if (!found)
                printf("Account Not Found or Wrong Password!\n");
        }

        else if (choice == 5) {
            printf("\n--- Show Balance ---\n");

            printf("Enter Account Number: ");
            scanf("%d", &accNumber);

            printf("Enter Password: ");
            scanf(" %s", pass);

            int found = 0;

            for (i = 0; i < count; i++) {
                if (acc[i].accNo == accNumber &&
                    strcmp(acc[i].password, pass) == 0) {

                    printf("\n========== ACCOUNT DETAILS ==========\n");
                    printf("Account Number : %d\n", acc[i].accNo);
                    printf("Account Holder : %s\n", acc[i].name);
                    printf("Balance        : %.2f\n", acc[i].balance);
                    printf("Loan Amount    : %.2f\n", acc[i].loan);
                    printf("====================================\n");

                    found = 1;
                    break;
                }
            }

            if (!found)
                printf("Account Not Found or Wrong Password!\n");
        }

        else if (choice == 6) {
            printf("\nThank you for using Bank Management System!\n");
            break;
        }

        else {
            printf("Invalid Choice! Try Again.\n");
        }
    }

    return 0;
}
