# Personal Budget Tracker

#### Video Demo: 

#### Description:

The Personal Budget Tracker is a Python application created to help users record, organize, and review their personal financial transactions. The program allows a user to add income and expense records, view all saved transactions, search transactions by category, display a financial summary, and delete saved transactions when needed. The main purpose of this project is to create a useful budgeting tool while demonstrating important Python programming skills learned throughout the course.

This project runs in the terminal and uses a menu-driven interface. When the program starts, the user is shown a list of numbered options. The user can choose to add a transaction, view transactions, show a summary, search by category, delete all transactions, or exit the program. This makes the program simple to use because the user does not need to memorize commands. Each option is clearly displayed on the screen.

The main file in this project is `TermProject.py`. This file contains the complete Python program. It includes the required `main()` function and several additional functions that are all defined at the same indentation level. The `create_file()` function checks whether the transaction storage file already exists. If it does not exist, the function creates a new CSV file and adds column headers. The `add_transaction()` function allows the user to enter a transaction type, category, amount, and description. It also records the current date automatically. The `view_transactions()` function displays the saved transaction history. The `show_summary()` function calculates total income, total expenses, and the remaining balance. The `search_by_category()` function allows the user to find transactions that match a specific category. The `delete_all_transactions()` function clears the saved transactions after the user confirms the action.

The project also includes a `requirements.txt` file. This file is required by the assignment instructions. Since the program only uses built-in Python libraries, there are no outside libraries that need to be installed. The program uses the built-in `csv`, `os`, and `datetime` modules. Because of this, the `requirements.txt` file is intentionally left blank.

Another important file is `transactions.csv`. This file is created automatically when the program runs for the first time. It stores the user's transaction records. The CSV file includes columns for date, transaction type, category, amount, and description. I chose to use a CSV file because it provides simple persistent storage. This means the user’s information is saved even after the program closes. CSV files are also easy to read, easy to edit, and do not require advanced database setup.

One important design decision was separating the program into multiple functions. This makes the code easier to read, test, and maintain. Instead of placing all code inside the main function, each feature has its own function. This makes the program more organized and makes it easier to add new features later. For example, future versions could include editing transactions, creating monthly reports, or generating graphs.

Another design decision was adding input validation. The program checks that the transaction type is either income or expense. It also checks that the amount entered is a valid number greater than zero. This helps prevent errors and keeps the stored data more accurate. Input validation is important because users may accidentally type incorrect information.

This project demonstrates several Python concepts, including functions, loops, conditionals, file handling, user input, lists, CSV processing, and basic data calculations. The while loop keeps the program running until the user chooses to exit. Conditional statements decide which function should run based on the user’s menu choice. File handling is used to create, write, read, and reset the CSV file. Data processing is used to calculate the financial summary.

Overall, the Personal Budget Tracker meets the final project requirements because it is implemented in Python, includes a main function, includes more than three additional functions, uses a file named `TermProject.py`, includes a `requirements.txt` file, and is more complex than a basic lab assignment. The program combines multiple skills into one complete application that has a practical real-world purpose.
