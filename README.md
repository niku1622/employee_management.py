# employee_management.py
import sys

def main_menu():
    while True:
        print("\nEmployee Management System")
        print("1. Add Employee")
        print("2. View All Employees")
        print("3. Search for Employee")
        print("4. Exit")
        
        choice = input("Enter your choice (1-4): ")
        
        if choice == '1':
            add_employee()
        elif choice == '2':
            view_employees()
        elif choice == '3':
            search_employee()
        elif choice == '4':
            print("Thank you for using EMS. Exiting...")
            sys.exit()
        else:
            print("Invalid choice. Please enter a number between 1 and 4.")

employees = {
    101: {'name': 'Satya', 'age': 27, 'department': 'HR', 'salary': 50000},
    102: {'name': 'Amit', 'age': 30, 'department': 'IT', 'salary': 70000},
    103: {'name': 'Riya', 'age': 25, 'department': 'Finance', 'salary': 55000}
}

def add_employee():
    try:
        emp_id = int(input("Enter Employee ID: "))
        if emp_id in employees:
            print("Employee ID already exists. Please enter a unique ID.")
            return
        
        name = input("Enter Employee Name: ")
        age = int(input("Enter Employee Age: "))
        department = input("Enter Employee Department: ")
        salary = float(input("Enter Employee Salary: "))
        
        employees[emp_id] = {'name': name, 'age': age, 'department': department, 'salary': salary}
        print("Employee added successfully!")
    except ValueError:
        print("Invalid input. Please enter numeric values for ID, age, and salary.")

def view_employees():
    if not employees:
        print("No employees available.")
        return
    
    print("\nEmployee Details:")
    print("ID    Name      Age  Department  Salary")
    print("------------------------------------------------")
    for emp_id, details in employees.items():
        print(f"{emp_id:<5} {details['name']:<10} {details['age']:<4} {details['department']:<12} {details['salary']:<10}")

def search_employee():
    try:
        emp_id = int(input("Enter Employee ID to search: "))
        if emp_id in employees:
            details = employees[emp_id]
            print("\nEmployee Found:")
            print(f"Name: {details['name']}")
            print(f"Age: {details['age']}")
            print(f"Department: {details['department']}")
            print(f"Salary: {details['salary']}")
        else:
            print("Employee not found.")
    except ValueError:
        print("Invalid input. Please enter a numeric Employee ID.")

if __name__ == "__main__":
    main_menu()
