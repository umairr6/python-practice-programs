students = {}

def calculate_result(marks):
    total = sum(marks.values())
    percentage = total /len(marks)

    if percentage >=90:
        grade ="A+"
    elif percentage >=80:
        grade ="A"
    elif percentage >=70:
        grade ="B"
    elif percentage >=60:
        grade ="C"
    elif percentage >=50:
        grade ="D"
    else:
        grade ="F"

    return total, percentage, grade

def add_student():
    name =input("Enter Student Name: ")

    marks = {}
    subjects =["Python","Math","Data Science"]

    for subject in subjects:
        marks[subject] = float(input(f"Enter marks for {subject}: "))
        students[name] = marks
        print("Student Added Successfully")

def display_students():
    if not students:
            print("No Student Record Found")
            return
        
    for name, marks in students.items():
            total,percentage,grade = calculate_result(marks)
        
            print("\n"+"=" * 80)
            print(f"Name      : {name}")
            print(f"Marks     : {marks}")
            print(f"Total     : {total}")
            print(f"Percentage: {percentage}")
            print(f"Grade     : {grade}")
            print("\n"+"=" * 80)

while True:
            print("Student Management System")
            print("1. Add Student")
            print("2. Display Student")
            print("3. Exit")

            choice = input("Enter choice; ")
            if choice == "1":
                add_student()
            elif choice == "2":
                display_students()
            elif choice =="3":
                print("Program Terminated")
                break
            else:
                print("invalid choice")
