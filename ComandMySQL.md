-- Selezionare tutti gli studenti nati nel 1990 (160)
SELECT *
FROM `students`
WHERE year(date_of_birth) = 1990;

-- Selezionare tutti i corsi che valgono più di 10 crediti (479)
SELECT *
FROM `courses`
WHERE `cfu` > 10;

-- Selezionare tutti gli studenti che hanno più di 30 anni ?? non ce scritto quanti devono essere
SELECT *
FROM `students`
WHERE YEAR(date_of_birth) <= 1996
AND MONTH(date_of_birth) <= 4
AND DAY(date_of_birth) <= 15;

-- Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
SELECT *
FROM `courses`
WHERE period like 'I semestre'
AND year = 1;

-- Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del  20/06/2020 (21)
SELECT *
FROM `exams`
WHERE HOUR(hour) >= 14
AND YEAR(date) = 2020
AND MONTH(date) = 06
AND DAY(date) = 20;

-- Selezionare tutti i corsi di laurea magistrale (38)
SELECT *
FROM `degrees`
WHERE level like 'magistrale';

-- Da quanti dipartimenti è composta l'università? (12)
SELECT *
FROM `departments`
WHERE id is NOT NULL;

-- Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
SELECT *
FROM `teachers`
WHERE phone is NULL;