# Assignment 6 - Gradebook

You task is to write a flask application in python that shows students, courses and grades.

The application uses a SQLite database do store and access data.

### Database

The file `setup_db.py` includes scripts to initialize a sqlite database, create tables, read, and write data.
* Run the script to initialize the database.
* You can also use the provided function in your flask application.
* Please add additional functions if you need them.

### Flask application

You should complete the `app.py` flask application. Generate templates that create the pages shown in the `sample` folder.
Do not store data in the application. Instead, store and retrieve data from the database using provided functionality.
You need to create the following templates/routes:

  - `/` or `index.html`
    * This file contains an overview and links to all files. Specifically, there should be two tables:
        - List of all courses, with columns "course code" and "name", sorted by course code. Add a link on the course code to the course's page.
        - List of all students, with columns "student no" and "name", sorted by student number. Add a link on the student number to the student's profile page.
        - A link to a form that allows to add new students.
        - See e.g. [index.html](sample/index.html)  
  - `/student/{student_no}`
    * This page displays for a student with a given student number:
        - The name of the student.
        - A list (table) of all courses (with course code and name) together with the grade.
        - A form with button that redirects to `/add_grade` route.
        - See e.g. [111111.html](sample/student/111111.html)
  - `/course/{course_code}`
    * This page displays for course with course_code
        - The course code.
        - A list (table) of all students that have a grade from this course, and their grades.
        - *This list should be sorted by grades, i.e. starting with all As then Bs, ...*
        - A summary of the grades, i.e. a table with the count of each grade.
        Only including grades with count 1 or higher.
        - A form with button that redirects to `/add_grade` route.
        - See e.g. [DAT100.html](sample/course/DAT100.html)
  - `/add_student`  
    * This page displays a form, that allows to add a student.
        - The form has one field for the students name.
        - When submitted, check that the name in not empty. Otherwise, display an error [student_form_error](sample/student_form_error.html).
        - Otherwise, add the student to the database with a new student_no.
          * Student numbers should be between 100000 and 999999
        - Then redirect the user to the index page.
        - See e.g. [student_form.html](sample/student_form.html).
  - `/add_grade`
    * This page allows to add a grade for a given course and student.
        - It contains a dropdown with all students.
        - It contains a dropdown with all courses.
        - It contains a dropdown with grades A to F.
        - It contains a submit button.
        - All dropdowns contain default elements, i.e. *Select*.
        - If the form is submitted and course, student or grade is missing,
        display the form again, together with an error message ([add_grade_error.html](sample/add_grade_error.html))
        - If a grade is successfully added to `grades.tsv` display a success message ([add_grade_success.html](sample/add_grade_success.html))
        - Display a link back to the main page.
        - See e.g. [add_grade.html](sample/add_grade.html).

  - `/add_grade` from course:
    * When the form is reached from a given course, then the Course-select should only contain this one course. E.g. [add_grade_DAT100.html](sample/add_grade_DAT100.html).
    * When the form is reached from a given student, then the student-select should only contain this one student. E.g. [add_grade_stud1.html](sample/add_grade_stud1.html).

All templates should inherit from one base template `base.html`, that contains header and footer of the HTML page.
The CSS file `/static/style.css` is already given (but you are free to make changes to it, if you wish). 

Under the `sample` folder, you can find an example of how the page should look.