<!-- 
Esercizio di oggi:
nome repo: db-university

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

Utilizzare https://www.drawio.com/ per la creazione dello schema.
Esportare quindi il diagramma in png, caricarlo in un file html e pushare tutto nella repo.
 -->






 ## departments
- id
- name
- students_id


 ## courses_degree
- id
- name
- students_id


 ## course_subjects
- id
- name
- courses_degree_id
- teachers_id
- students_id


 ## teachers
- id
- firstname
- lastname
- birth
- date_of_hire
- phone
- email
- course_subject_id
- contractual_regime


 ## exam_calls
- id
- students_id
- course_subject_id
- teachers_id
- date
- outcome


 ## students
 - id
 - firstname
 - lastname
 - course_subject_id
 - course_degree_id
 - departments_id
 - birth
 - email
 - phone
 - study_regime
 - votes