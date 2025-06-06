Student Grade Management System

import json

File to store student data

data_file = "students.json"

def load_data(): try: with open(data_file, "r") as f: return json.load(f) except FileNotFoundError: return []

def save_data(data): with open(data_file, "w") as f: json.dump(data, f, indent=4)

def calculate_grade(avg): if avg >= 90: return 'A+' elif avg >= 75: return 'A' elif avg >= 60: return 'B' elif avg >= 50: return 'C' else: return 'F'

def add_student(): student = {} student['name'] = input("Enter name: ") student['roll'] = input("Enter roll number: ") marks = [] for i in range(3): mark = float(input(f"Enter marks for subject {i+1}: ")) marks.append(mark) student['marks'] = marks student['total'] = sum(marks) student['average'] = student['total'] / 3 student['grade'] = calculate_grade(student['average']) data = load_data() data.append(student) save_data(data) print("Student added successfully!\n")

def view_students(): data = load_data() if not data: print("No student records found.\n") return for student in data: print("-------------------------------") print(f"Name: {student['name']}") print(f"Roll No: {student['roll']}") print(f"Marks: {student['marks']}") print(f"Total: {student['total']}") print(f"Average: {student['average']:.2f}") print(f"Grade: {student['grade']}") print("-------------------------------\n")

def search_student(): roll = input("Enter roll number to search: ") data = load_data() for student in data: if student['roll'] == roll: print(f"Found student: {student['name']}, Grade: {student['grade']}\n") return print("Student not found.\n")

def update_student(): roll = input("Enter roll number to update: ") data = load_data() for student in data: if student['roll'] == roll: print(f"Updating student: {student['name']}") student['name'] = input("Enter new name: ") or student['name'] marks = [] for i in range(3): mark = input(f"Enter new mark for subject {i+1} (or press Enter to keep old): ") if mark: marks.append(float(mark)) else: marks.append(student['marks'][i]) student['marks'] = marks student['total'] = sum(marks) student['average'] = student['total'] / 3 student['grade'] = calculate_grade(student['average']) save_data(data) print("Student record updated.\n") return print("Student not found.\n")

def delete_student(): roll = input("Enter roll number to delete: ") data = load_data() new_data = [s for s in data if s['roll'] != roll] if len(data) == len(new_data): print("Student not found.\n") else: save_data(new_data) print("Student record deleted.\n")

def menu(): while True: print("===== Student Grade Management System =====") print("1. Add Student") print("2. View All Students") print("3. Search Student") print("4. Update Student") print("5. Delete Student") print("6. Exit") choice = input("Enter your choice (1-6): ")

if choice == '1':
        add_student()
    elif choice == '2':
        view_students()
    elif choice == '3':
        search_student()
    elif choice == '4':
        update_student()
    elif choice == '5':
        delete_student()
    elif choice == '6':
        print("Exiting... Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.\n")

if name == "main": menu()

