# python-practice-

Let's understand your Student Management System in Python step by step. 😊

Your program allows you to:

1. Add a student's name and marks.
2. Calculate their total marks, percentage, and grade.
3. Display all students' results.
4. Exit the program.

I'll explain what every part does, why it is used, and how the program works when you run it.

# 1. Understanding the complete program flow

Start the program

Display the menu

1\. Add Student · 2. Display Students · 3. Exit

Option 1

Enter name and marks

Option 2

Calculate and display results

Option 3

Stop the program

After adding or displaying records, the menu appears again until you exit.

# 2. Storing student records

Your first line is:

```
students = {}
```

This creates an empty dictionary.

A dictionary stores information as key-value pairs.

For example, after adding a student, it might look like this:

```
students = {    "Umair": {
        "Python": 95,
        "Mathematics": 85,
        "Data Science": 90    }}
```

Here:

- `"Umair"` is the key representing the student's name.
- The inner dictionary contains the student's subjects and marks.
- `{}` means an empty dictionary.

Think of `students` as a register containing every student's record.

# 3. Calculating the result

Your function is:

```
def calculate_result(marks):
    total = sum(marks.values())
    percentage = total / len(marks)
    if percentage >= 90:
        grade = "A+"
    elif percentage >= 80:
        grade = "A"
    elif percentage >= 70:
        grade = "B"
    elif percentage >= 60:
        grade = "C"
    elif percentage >= 50:
        grade = "D"
    else:
        grade = "F"
    return total, percentage, grade
```

Let's break it down.

### A. Define the function

```
def calculate_result(marks):
```

- `def` is used to define a function.
- `calculate_result` is the function's name.
- `marks` is a parameter that receives a student's marks.

A function is a reusable block of code. You write it once and call it whenever needed.

### B. Calculate total marks

```
total = sum(marks.values())
```

Suppose `marks` contains:

```
marks = {
    "Python": 95,
    "Mathematics": 85,
    "Data Science": 90}
```

`marks.values()` returns the marks:

```
95, 85, 90
```

`sum()` adds them:

\\[ 95 + 85 + 90 = 270 \\]

Therefore:

```
total = 270
```

### C. Calculate percentage

```
percentage = total / len(marks)
```

- `total` is 270.
- `len(marks)` counts the number of subjects, which is 3.

So:

\\[ \text{Percentage}=\frac{270}{3}=90\\% \\]

Important: Your code assumes every subject is marked out of 100. Because you have three subjects, the maximum total is 300, so dividing by three gives the percentage.

### D. Assign a grade

```
if percentage >= 90:
    grade = "A+"
elif percentage >= 80:
    grade = "A"
```

Python checks the conditions from top to bottom.

For example, if the percentage is 85:

- Is it at least 90? No.
- Is it at least 80? Yes.
- The grade becomes `"A"`.
- Python skips the remaining branches.

Here is your complete grading system:

| Percentage | Grade |
| ---------- | ----- |
| 90–100%    | A+    |
| 80–89.99%  | A     |
| 70–79.99%  | B     |
| 60–69.99%  | C     |
| 50–59.99%  | D     |
| Below 50%  | F     |

### E. Return the results

```
return total, percentage, grade
```

`return` sends the calculated values back to the part of the program that called the function.

For our example, it returns:

```
(270, 90.0, "A+")
```

Notice the difference: `print()` displays something on the screen, while `return` gives a value back to the caller.

# 4. Adding a student

Your function:

```
def add_student():
    name = input("Enter student name: ")
    marks = {}
    subjects = ["Python", "Mathematics", "Data Science"]
    for subject in subjects:
        marks[subject] = float(input(f"Enter marks for {subject}: "))
    students[name] = marks
       print("Student added successfully!")
```

### A. Get the student's name

```
name = input("Enter student name: ")
```

`input()` asks the user to enter information.

If you type `Umair`, the variable `name` stores `"Umair"`.

### B. Create a marks dictionary

```
marks = {}
```

This creates an empty dictionary to store the marks for the current student.

### C. Define the subjects

```
subjects = ["Python", "Mathematics", "Data Science"]
```

This is a list containing three subject names.

A list stores multiple items in order.

### D. Use a loop

```
for subject in subjects:
```

This loop runs once for each subject.

First iteration

`subject = "Python"`

Ask for Python marks.

Second iteration

`subject = "Mathematics"`

Ask for Mathematics marks.

Third iteration

`subject = "Data Science"`

Ask for Data Science marks.

### E. Convert the input into a number

```
marks[subject] = float(    input(f"Enter marks for {subject}: "))
```

This line combines three important concepts:

- `input()` receives what the user types.
- `float()` converts that input into a number, such as `95.5`.
- `marks[subject] =` saves that number under the subject's name.

For example, if you enter `95`, the dictionary stores:

```
{"Python": 95.0}
```

Why use `float()`? Because input is initially text, and you need numeric values to perform calculations.

### F. Save the complete student record

```
students[name] = marks
```

This adds the marks dictionary to the main `students` dictionary using the student's name as the key.

Then:

```
print("Student added successfully!")
```

displays a confirmation message.

One thing to remember: If you add another student using exactly the same name, the existing record will be overwritten. Your current program also keeps records only in memory, so they disappear when the program ends.

# 5. Displaying student results

Your function begins with:

```
def display_students():
    if not students:
        print("No student records found.")
        return
```

`if not students` checks whether the dictionary is empty.

- If it is empty, the program prints a message.
- `return` exits the function immediately.
- If students exist, the program continues.

Next:

```
for name, marks in students.items():
```

`.items()` lets you loop through each student's name and their marks together.

For example:

```
name = "Umair"marks = {
    "Python": 95.0,
    "Mathematics": 85.0,
    "Data Science": 90.0}
```

Then this line calls your calculation function:

```
total, percentage, grade = calculate_result(marks)
```

Python receives the three returned values and assigns them to three variables.

Finally, the program prints the result:

```
print("\n" + "=" * 40)
print(f"Name       : {name}")
print(f"Marks      : {marks}")
print(f"Total      : {total}")
print(f"Percentage : {percentage:.2f}%")
print(f"Grade      : {grade}")
```

Some syntax worth understanding:

- `"\n"` creates a new line.
- `"=" * 40` prints 40 equal signs.
- `f"..."` is an f-string, which inserts variable values into text.
- `{percentage:.2f}` formats the percentage to two decimal places.

For example, `83.33333` becomes `83.33`.

Here is what the output might look like:

SAMPLE TERMINAL OUTPUT

\======================================== 
Name       : Umair 
Marks      : {'Python': 95.0, 'Mathematics': 85.0, 'Data Science': 90.0}
Total      : 270.0 Percentage : 90.00% 
Grade      : A+

# 6. The main menu and infinite loop

This is the part that keeps the program running:

```
while True:
print("\n===== STUDENT MANAGEMENT SYSTEM =====")
print("1. Add Student")
print("2. Display Students")
print("3. Exit")
choice = input("Enter choice: ")
```

`while True` creates a loop that repeats indefinitely unless something stops it.

Every time the loop runs, it shows the menu and asks the user to choose an option.

Your conditions are:

```
if choice == "1":
add_student()
elif choice == "2":
display_students()
elif choice == "3":
print("Program terminated.")
breakelse:
print("Invalid choice.")
```

| Code    | Meaning                                                 |
| ------- | ------------------------------------------------------- |
| `if`    | Checks the first condition.                             |
| `elif`  | Checks another condition if the previous one was false. |
| `else`  | Runs when none of the conditions match.                 |
| `break` | Exits the loop immediately.                             |

Why compare with `"1"` instead of `1`? Because `input()` returns text. So when you type `1`, Python receives the string `"1"`.
