-- JOIN

-- Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT *
FROM students
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name LIKE '%Economia%';

-- Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT *
FROM degrees
JOIN departments ON degrees.department_id = departments.id
WHERE departments.name like '%Neurosci%'
AND degrees.level = 'magistrale'

-- Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT *
FROM courses
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON teachers.id = course_teacher.teacher_id
WHERE teachers.id = 44;

-- Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT *
FROM students as s
JOIN degrees as d ON s.degree_id = d.id
JOIN departments as dep ON d.department_id = dep.id
ORDER BY s.name ASC

-- Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
SELECT *
FROM degrees as d
JOIN courses as c ON d.id = c.degree_id
JOIN course_teacher as ct ON ct.course_id = c.id
JOIN teachers as t ON t.id = ct.teacher_id

-- Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
SELECT DISTINCT t.*
FROM teachers as t
JOIN course_teacher as ct ON t.id = ct.teacher_id
JOIN courses as c ON ct.course_id = c.id
JOIN degrees as d ON c.degree_id = d.id
JOIN departments as dep ON d.department_id = dep.id
WHERE dep.name like '%Matematica%'
ORDER BY t.name ASC

-- BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.




-- GROUP BY


-- Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(id), YEAR(enrolment_date)
FROM students
GROUP BY YEAR(enrolment_date)

-- Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(id), office_address
FROM teachers
GROUP BY office_address

-- Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(vote), exam_id
FROM exam_student
GROUP BY exam_id

-- Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(*), department_id
FROM degrees
GROUP BY department_id