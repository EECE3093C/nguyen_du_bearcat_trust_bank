# UML Sequence Diagram

UML Sequence Diagram includes the following interactions:
* Creating a Savings account
* Creating a Checking account
* Depositing to a Checking account
* Withdrawing from a Savings account

```mermaid

sequenceDiagram
    participant User as User
    participant Bank as Bank
    participant SavingsAccount as SavingsAccount
    participant CheckingAccount as CheckingAccount
    participant Account as Account

    User ->> Bank: create_account("SavingsAccount", ...)
    Bank ->> SavingsAccount: __init__(account_number, account_holder_name, balance, interest_rate)
    SavingsAccount ->> Account: __init__(account_number, account_holder_name, balance)
    Bank ->> Bank: accounts.append(savings_account)

    User ->> Bank: create_account("CheckingAccount", ...)
    Bank ->> CheckingAccount: __init__(account_number, account_holder_name, balance, overdraft_limit)
    CheckingAccount ->> Account: __init__(account_number, account_holder_name, balance)
    Bank ->> Bank: accounts.append(checking_account)

    User ->> Bank: find_account(account_number)
    Bank ->> Bank: find_account(account_number)
    User ->> CheckingAccount: deposit(amount)
    CheckingAccount ->> Account: deposit(amount)

    User ->> Bank: delete_account(account_number)
    Bank ->> Bank: accounts.remove(account)
    User ->> SavingsAccount: withdraw(amount)
    SavingsAccount ->> Account: withdraw(amount)

```