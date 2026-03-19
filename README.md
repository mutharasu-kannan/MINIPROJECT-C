# MINIPROJECT-C
Banking Management System in C
Overview

This C program implements a simple bank account management system with file-based storage. It allows users to create, update, delete accounts, transfer funds, and track transaction history with password protection and account security features.

The program uses binary files (credit.dat) to store account information and transaction logs (transactions.dat) to maintain a history of all transactions with timestamps.

Features

Account Management

Create a new account with first name, last name, balance, and password.

Update account balance by recording deposits or payments.

Delete existing accounts.

Password protection with account lock after 3 failed attempts.

Transaction Management

Transfer funds between accounts with a daily transfer limit of 200,000.

Log all transactions (Deposit, Payment, Transfer) with date and time.

View transaction history for any account.

Security Features

Password verification for sensitive operations.

Account lock after 3 consecutive wrong password attempts.

Minimum balance alert (alert triggered if balance < 1000).

Reporting

Generate a formatted text file (accounts.txt) of all accounts for printing or review.

Display account details before and after updates or transfers.

File Structure

credit.dat: Binary file storing account information.

transactions.dat: Binary file storing transaction history.

accounts.txt: Text file generated for human-readable account overview.

Data Structures

Client Account

struct clientData {
    unsigned int acctNum;      // Account number (1-100)
    char lastName[15];         // Last Name
    char firstName[10];        // First Name
    double balance;            // Current balance
    char password[20];         // Account password
    int failedAttempts;        // Track wrong password entries
    int locked;                // 0 = active, 1 = locked
};

Transaction Record

struct transaction {
    unsigned int acctNumFrom;  // Source account number
    unsigned int acctNumTo;    // Destination account number
    char type[10];             // Deposit, Payment, Transfer
    double amount;             // Transaction amount
    char dateTime[20];         // Timestamp: YYYY-MM-DD HH:MM
};
Installation & Compilation

Save the code to a file named, for example, banking.c.

Open a terminal or command prompt.

Compile using GCC:

gcc banking.c -o banking

Run the program:

./banking      # Linux / macOS
banking.exe    # Windows
Usage Instructions

After running the program, the menu will appear:

Enter your choice
1 - store a formatted text file of accounts called "accounts.txt" for printing
2 - update an account
3 - add a new account
4 - delete an account
5 - transfer amount between accounts
6 - view transaction history
7 - end program
1. Generate Account Report

Creates accounts.txt containing all accounts.

Opens the file automatically in Notepad (Windows) or default text editor (macOS/Linux).

2. Update Account

Enter the account number.

Verify password.

Enter deposit (+) or payment (-) amounts.

Displays updated balance.

Logs the transaction in transactions.dat.

3. Create New Account

Enter a new account number.

Enter first name, last name, initial balance, and password.

Logs initial deposit transaction.

4. Delete Account

Enter the account number to delete.

Resets account data to blank.

5. Transfer Funds

Enter FROM and TO account numbers.

Enter transfer amount (limit 200,000/day).

Verifies FROM account password.

Updates balances and logs the transaction.

Alerts if balance falls below 1000 in either account.

6. View Transaction History

Enter the account number.

Displays all deposits, payments, and transfers for the account.

Security & Validation

Accounts lock after 3 wrong password attempts.

Transfers limited to 200,000 per transaction.

Alerts for low balances (<1000).

Password-protected sensitive operations: update account, transfer funds.

Dependencies

Standard C libraries:

stdio.h – Input/output

stdlib.h – Memory allocation, exit

string.h – String operations

time.h – Date and time logging

No external dependencies.

File Management

credit.dat: Random-access binary file for accounts.

transactions.dat: Append-only binary file for transactions.

accounts.txt: Generated from credit.dat for easy reading.

Important: Ensure these files are in the same directory as the executable.

Example Flow

User creates two accounts:

Account 1: Alice Smith, balance 5000
Account 2: Bob Jones, balance 3000

User transfers 1000 from Alice to Bob.

Both accounts updated.

Transaction logged in transactions.dat.

User views transaction history of Alice:

2026-03-19 15:45: Deposit 5000.00
2026-03-19 15:50: Transfer from 1 to 2 1000.00

Low balance alert triggers if balance < 1000.

Notes

Maximum 100 accounts supported (account numbers 1–100).

Account numbers are unique; duplicate creation is prevented.

Transactions are logged with local date and time.

Program is designed for console usage.


