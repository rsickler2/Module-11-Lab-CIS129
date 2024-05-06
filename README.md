# Module-11-Lab-CIS129
# Robert Sickler 5/4/24

9.1)

    # Open the file in write mode to clear previous content
    with open("grades.txt", "w") as file:
    pass

    # Prompt the user to enter grades
    print("Enter grades (enter 'q' to quit):")

    # Open the file in append mode to add grades
    with open("grades.txt", "a") as file:
    while True:
        grade_input = input("Enter a grade: ")
        if grade_input.lower() == 'q':
            break
        file.write(grade_input + "\n")

    print("Grades have been stored in grades.txt.")

9.2)

    # Open the file in read mode
    with open("grades.txt", "r") as file:
    grades = file.readlines()

    # Strip newline characters and convert grades to integers
    grades = [int(grade.strip()) for grade in grades]

    # Calculate total, count, and average
    total = sum(grades)
    count = len(grades)
    average = total / count if count > 0 else 0

    # Display individual grades
    print("Individual Grades:")
    for grade in grades:
    print(grade)

    # Display total, count, and average
    print("\nTotal:", total)
    print("Count:", count)
    print("Average:", average)

9.3)

    import csv

    print("Welcome to the Student Grade Recorder")

    with open("grades.csv", "w", newline='') as csvfile:
    csv_writer = csv.writer(csvfile)
    csv_writer.writerow(["First Name", "Last Name", "Exam 1 Grade", "Exam 2 Grade", "Exam 3 Grade"])
    
    while True:
        first_name = input("Enter First Name (or 'q' to quit): ")
        if first_name.lower() == 'q':
            break
        last_name = input("Enter Last Name: ")
        exam1_grade, exam2_grade, exam3_grade = map(int, input("Enter Exam Grades (space-separated): ").split())
        
        csv_writer.writerow([first_name, last_name, exam1_grade, exam2_grade, exam3_grade])

    print("\nStudent records have been saved to grades.csv.")
