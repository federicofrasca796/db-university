# MySQL Queries

## Query con Group by

1. Contare quanti iscritti ci sono stati ogni anno
    - **SELECT COUNT(id) AS num_of_students, YEAR enrolment_date) FROM students GROUP BY YEAR enrolment_date)**

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    - **SELECT COUNT(id) AS teachers_num, office_address FROM teachers GROUP BY office_address**

3. Calcolare la media dei voti di ogni appello d'esame
    - **SELECT exam_id, AVG(vote) FROM exam_student GROUP BY exam_id**

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
    - **SELECT COUNT(id) AS degree_id, department_id FROM degrees GROUP BY department_id**

## Query con Join

5. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    - **SELECT `students`.name, `students`.surname, `students`.email, `students`.registration_number, `degrees`.name, `degrees`.level FROM `degrees` JOIN `students` ON students.degree_id = degrees.id WHERE degrees.name = 'Corso di Laurea in Economia';**

6. Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
    - **SELECT * FROM `departments` JOIN `degrees` ON `degrees`.department_id = `departments`.id WHERE `departments`.name = "Dipartimento di Neuroscienze"**

7. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    - **SELECT * FROM `teachers` JOIN `course_teacher` ON course_teacher.teacher_id = teachers.id WHERE teachers.id = 44**

8. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    - **SELECT `students`.surname, `students`.name, `degrees`.*, `departments`.* FROM `students` JOIN `degrees` ON degrees.id = students.degree_id JOIN `departments` ON departments.id = degrees.department_id ORDER BY `students`.surname**

9. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    - **SELECT `degrees`.name, `courses`.name, `courses`.name, `courses`.period, `teachers`.name, `teachers`.surname FROM `degrees` JOIN `courses` ON courses.degree_id = degrees.id JOIN `course_teacher` ON courses.id = course_teacher.course_id OIN `teachers` ON teachers.id = course_teacher.teacher_id**

10. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    - **SELECT DISTINCT teachers.*, departments.* FROM departments JOIN degrees ON degrees.department_id = departments.id JOIN courses ON courses.degree_id = degrees.id JOIN course_teacher ON course_teacher.course_id = courses.id JOIN teachers ON course_teacher.teacher_id = teachers.id WHERE departments.name = "Dipartimento di Matematica"**

11. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
    - **SELECT COUNT(exams.id) AS n_tries, students.name, students.surname, courses.name AS 'course_name' FROM exam_student JOIN students ON students.id = exam_student.student_id JOIN exams ON exams.id = exam_student.exam_id JOIN courses ON courses.id = exams.course_id GROUP BY  students.id, courses.id**
