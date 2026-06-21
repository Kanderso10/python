import csv
import os
from datetime import datetime

FILE_NAME = "transactions.csv"


def create_file():
    """Create the CSV file if it does not exist."""
    if not os.path.exists(FILE_NAME):
        with open(FILE_NAME, "w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(["Date", "Type", "Category", "Amount", "Description"])


def add_transaction():
    """Add a new transaction."""
    print("\nAdd New Transaction")

    transaction_type = input("Enter type (income/expense): ").strip().lower()

    while transaction_type not in ["income", "expense"]:
        print("Invalid type. Please enter income or expense.")
        transaction_type = input("Enter type (income/expense): ").strip().lower()

    category = input("Enter category: ").strip()

    while True:
        try:
            amount = float(input("Enter amount: "))
            if amount <= 0:
                print("Amount must be greater than 0.")
            else:
                break
        except ValueError:
            print("Please enter a valid number.")

    description = input("Enter description: ").strip()
    date = datetime.now().strftime("%Y-%m-%d")

    with open(FILE_NAME, "a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow([date, transaction_type, category, amount, description])

    print("Transaction added successfully.")


def view_transactions():
    """Display all transactions."""
    print("\nTransaction History")

    with open(FILE_NAME, "r") as file:
        reader = csv.reader(file)

        for row in reader:
            print(row)


def show_summary():
    """Show income, expenses, and balance."""
    income = 0
    expenses = 0

    with open(FILE_NAME, "r") as file:
        reader = csv.DictReader(file)

        for row in reader:
            amount = float(row["Amount"])

            if row["Type"].lower() == "income":
                income += amount
            elif row["Type"].lower() == "expense":
                expenses += amount

    balance = income - expenses

    print("\nFinancial Summary")
    print(f"Total Income: ${income:.2f}")
    print(f"Total Expenses: ${expenses:.2f}")
    print(f"Balance: ${balance:.2f}")


def search_by_category():
    """Search transactions by category."""
    category_search = input("\nEnter category to search: ").strip().lower()

    found = False

    with open(FILE_NAME, "r") as file:
        reader = csv.DictReader(file)

        for row in reader:
            if row["Category"].lower() == category_search:
                print(row)
                found = True

    if not found:
        print("No transactions found in that category.")


def delete_all_transactions():
    """Delete all transactions."""
    confirm = input(
        "\nAre you sure you want to delete all transactions? (yes/no): "
    ).strip().lower()

    if confirm == "yes":
        with open(FILE_NAME, "w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(
                ["Date", "Type", "Category", "Amount", "Description"]
            )

        print("All transactions deleted.")
    else:
        print("Delete canceled.")


def main():
    """Main menu."""
    create_file()

    while True:
        print("\n===== Personal Budget Tracker =====")
        print("1. Add Transaction")
        print("2. View Transactions")
        print("3. Show Summary")
        print("4. Search by Category")
        print("5. Delete All Transactions")
        print("6. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            add_transaction()
        elif choice == "2":
            view_transactions()
        elif choice == "3":
            show_summary()
        elif choice == "4":
            search_by_category()
        elif choice == "5":
            delete_all_transactions()
        elif choice == "6":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")


if __name__ == "__main__":
    main()
