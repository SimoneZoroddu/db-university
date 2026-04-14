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
- id                                        TINYINT(-/+127)             PRIMARY_KEY, AUTO_INCREMENT
- name                                      VARCHAR(50)                 NOTNULL
- students_id                               VARCHAR(100)                NULL


 ## courses_degree
- id                                        TINYINT(-/+127)             PRIMARY_KEY, AUTO_INCREMENT
- name                                      VARCHAR(50)                 NOTNULL
- students_id                               SMALLINT(-/+32.767)         NULL


 ## course_subjects
- id                                        TINYINT(-/+127)             PRIMARY_KEY, AUTO_INCREMENT
- name                                      VARCHAR(50)                 NOTNULL
- courses_degree_id                         TINYINT(-/+127)             NOTNULL
- teachers_id                               TINYINT(-/+127)             NOTNULL
- students_id                               SMALLINT(-/+32.767)         NOTNULL


 ## teachers
- id                                        TINYINT(-/+127)             PRIMARY_KEY, AUTO_INCREMENT
- firstname                                 VARCHAR(50)                 NOTNULL
- lastname                                  VARCHAR(50)                 NOTNULL
- birth                                     DATE                        NULL
- date_of_hire                              DATE                        NOTNULL
- phone                                     TINYINT(-/+127)             NULL
- email                                     VARCHAR(50)                 NULL
- course_subject_id                         TINYINT(-/+127)             NULL
- contractual_regime                        VARCHAR(10)                 NULL


 ## exam_calls
- id                                        INT(-/+2.147.483.647)       PRIMARY_KEY, AUTO_INCREMENT
- students_id                               MEDIUMYINT(-/+8.388.607)    NOTNULL
- course_subject_id                         TINYINT(-/+127)             NOTNULL
- teachers_id                               TINYINT(-/+127)             NULL
- date                                      DATE                        NULL
- outcome                                   FLOAT(2,1)                  NOTNULL


 ## students
 - id                                       MEDIUMYINT(-/+8.388.607)    PRIMARY_KEY, AUTO_INCREMENT
 - firstname                                VARCHAR(50)                 NOTNULL
 - lastname                                 VARCHAR(50)                 NOTNULL
 - course_subject_id                        TINYINT(-/+127)             NULL
 - course_degree_id                         TINYINT(-/+127)             NULL
 - departments_id                           TINYINT(-/+127)             NULL
 - birth                                    DATE                        NULL
 - email                                    VARCHAR(50)                 NOTNULL
 - phone                                    TINYINT(-/+127)             NULL
 - study_regime                             VARCHAR(10)                 NULL
 - votes                                    FLOAT(3,1)                  NULL