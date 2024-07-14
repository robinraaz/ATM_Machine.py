# ATM_Machine.py
class BankAccount:
    def __init__(self, initial_balance=0):
        self.balance = initial_balance
    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            return True
        return False
    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            return True
        return False
    def check_balance(self):
        return self.balance
class ATM:
    def __init__(self, account):
        self.account = account
    def display_menu(self):
        print("\n--- ATM Menu ---")
        print("1. Check Balance")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Exit")
    def check_balance(self):
        print(f"Your current balance is: {self.account.check_balance()}")
    def deposit(self):
        amount = float(input("Enter amount to deposit: "))
        if self.account.deposit(amount):
            print(f"Successfully deposited {amount}.")
        else:
            print("Deposit amount must be greater than zero.")
    def withdraw(self):
        amount = float(input("Enter amount to withdraw: "))
        if self.account.withdraw(amount):
            print(f"Successfully withdrew {amount}.")
        else:
            print("Insufficient balance or invalid amount.")
    def run(self):
        while True:
            self.display_menu()
            choice = input("Select an option: ")
            if choice == '1':
                self.check_balance()
            elif choice == '2':
                self.deposit()
            elif choice == '3':
                self.withdraw()
            elif choice == '4':
                print("Thank you for using the ATM. Goodbye!")
                break
            else:
                print("Invalid selection. Please try again.")
if __name__ == "__main__":
    initial_balance = float(input("Welcome to ATM Machine \nEnter initial balance for the account: "))
    account = BankAccount(initial_balance)
    atm = ATM(account)
    atm.run()
