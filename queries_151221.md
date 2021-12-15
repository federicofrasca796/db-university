# MySQL Queries

## Query con Group by

1. Contare quanti iscritti ci sono stati ogni anno
    - **here**

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    - **here**

3. Calcolare la media dei voti di ogni appello d'esame
    - **here**

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
    - **here**

## Query con Join

5. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    - **SELECT `students`.name, `students`.surname, `students`.email, `students`.registration_number, `degrees`.name, `degrees`.level FROM `degrees` JOIN `students` ON students.degree_id = degrees.id WHERE degrees.name = 'Corso di Laurea in Economia';**

6. Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze
    - **SELECT * FROM `departments` JOIN `degrees` ON `degrees`.department_id = `departments`.id WHERE `departments`.name = "Dipartimento di Neuroscienze"**

7. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    - **here**

8. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    - **here**

9. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
    - **here**

10. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    - **here**

11. BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
    - **here**
