# UML Class Diagram

Relationship between `Bank`, `Account`, `SavingsAccount`, `CheckingAccount`

classDiagram

    Account <|-- SavingsAccount
    Account <|-- CheckingAccount
    Bank *-- Account

    class Bank 
        Bank : +create_account(account_type, account_number, account_holder_name, balance, interest_rate, overdraft_limit) void
        Bank : +delete_account(account_number) void
        Bank : +find_account(account_number) account
        Bank : +list_accounts() void 
        
    
    class Account {
        +String account_number
        +String account_holder_name
        +Float balance
        +deposit(amount) float
        +withdraw(amount) float
        +get_balance() float
        +display() void
    }
    class SavingsAccount  {
        +Float interest_rate
        +calculate_interest() float
        +display() void
    }
    class CheckingAccount {
        +Float overdraft_limit
        +withdraw(amount) float
        +display() void
    }
    