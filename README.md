Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi Insegnanti;
- ogni Corso prevede più appelli d'Esame;
- ogni Studente è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.


# DB University

### 1) Selezionare tutti gli studenti nati nel 1990 (160).
```sql
 SELECT *
 FROM `students`
 WHERE YEAR(`date_of_birth`) = 1990;
```


### 2) Selezionare tutti i corsi che valgono più di 10 crediti (479).
```sql
SELECT *
FROM `courses`
WHERE `cfu` > 10;
```


### 3) Selezionare tutti gli studenti che hanno più di 30 anni.
```sql
SELECT * 
FROM `students`
WHERE YEAR(CURDATE()) - YEAR(date_of_birth) = 30;
```

### 4) Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286).

```sql
SELECT * 
FROM `courses` 
WHERE `year` = 1 AND 
      `period` = 'I semestre';
```

### 5) Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21).

```sql
SELECT * 
FROM `exams` 
WHERE `date` = DATE('2020-06-20') AND 
      `hour` > '14:00:00';
```

### 6) Selezionare tutti i corsi di laurea magistrale (38).

```sql
SELECT * 
FROM `degrees` 
WHERE `name` LIKE '%corso di Laurea magistrale%';
```

### 7) Da quanti dipartimenti è composta l'università? (12).

```sql
SELECT * 
FROM `departments`
```

### 8) Quanti sono gli insegnanti che non hanno un numero di telefono? (50).

```sql
SELECT * 
FROM `teachers` 
WHERE `phone` IS NULL;
```