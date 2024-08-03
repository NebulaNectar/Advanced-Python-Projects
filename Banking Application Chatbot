class User:
    def __init__(self, username, password):
        self.username = username
        self.password = password
        self.balance = 10000.0 

class BankingApp:
    def __init__(self):
        self.users = {}

    def register_user(self, username, password):
        if username in self.users:
            return False  
        self.users[username] = User(username, password)
        return True

    def authenticate_user(self, username, password):
        if username in self.users and self.users[username].password == password:
            return True
        return False

    def check_balance(self, username):
        if username in self.users:
            return self.users[username].balance  
        return None

    def transfer_funds(self, from_user, to_user, amount):
        if from_user in self.users and to_user in self.users:
            if self.users[from_user].balance >= amount:
                self.users[from_user].balance -= amount
                self.users[to_user].balance += amount
                return True
        return False

    def detailed_transfer_steps(self):
        return """
        To transfer funds to another bank account:
        1. Log in to your online banking account.
        2. Navigate to the 'Transfer' or 'Payments' section.
        3. Add the recipient's bank account details like account number, IFSC code, etc.
        4. Enter the amount you wish to transfer.
        5. Review the details and confirm the transaction.
        6. Verify the transaction status and keep a record of the transaction ID.
        """

def main():
    bank = BankingApp()

    while True:
        print("\nWelcome to the Banking App")
        print("1. Register")
        print("2. Login")
        print("3. Exit")

        choice = input("Enter your choice (1/2/3): ")

        if choice == '1':
            username = input("Enter username: ")
            password = input("Enter password: ")
            success = bank.register_user(username, password)
            if success:
                print(f"User '{username}' registered successfully with an initial balance of Rs. 10,000!")
            else:
                print(f"Username '{username}' already exists. Please choose a different username.")

        elif choice == '2':
            username = input("Enter username: ")
            password = input("Enter password: ")
            authenticated = bank.authenticate_user(username, password)
            if authenticated:
                print("Login successful.")
                while True:
                    print("\n1. Check Balance")
                    print("2. Transfer Funds")
                    print("3. Detailed Steps for Transfer")
                    print("4. Logout")

                    option = input("Enter your option (1/2/3/4): ")

                    if option == '1':
                        balance = bank.check_balance(username)
                        if balance is not None:
                            print(f"Bank Balance in the account is Rs. {balance:.2f}")
                        else:
                            print("Error: User not found.")
                    
                    elif option == '2':
                        to_user = input("Enter recipient's username: ")
                        amount = float(input("Enter amount to transfer: "))
                        success = bank.transfer_funds(username, to_user, amount)
                        if success:
                            print(f"Transfer of Rs. {amount:.2f} to '{to_user}' successful.")
                        else:
                            print("Transfer failed: Insufficient balance or user not found.")
                    
                    elif option == '3':
                        detailed_steps = bank.detailed_transfer_steps()
                        print("Detailed steps for transferring funds:")
                        print(detailed_steps)
                    
                    elif option == '4':
                        print("Logged out.")
                        break
                    
                    else:
                        print("Invalid option. Please enter 1, 2, 3, or 4.")

            else:
                print("Login failed: Invalid username or password.")

        elif choice == '3':
            print("Exiting Banking App. Goodbye!")
            break

        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()
