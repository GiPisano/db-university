
# QUERY CON JOIN

### 1) Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia.
```sql
SELECT `students`.* 
FROM `students`

INNER JOIN `degrees`
ON `degrees`.`department_id` = `students`.`degree_id`

WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
```

### 2) Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze.
```sql
SELECT `courses`.* 
FROM `courses`

INNER JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'Magistrale';
```

### 3) Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44).
```sql
SELECT `courses`.* 
FROM `courses`

INNER JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

WHERE `teachers`.`id` = 44;
```

### 4) Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome.
```sql
SELECT `students`.`surname`, `students`.`name`,
`degrees`.*,
`departments`.`name`
FROM `students`

INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

ORDER BY `students`.`surname`, `students`.`name` ASC;
```


### 5) Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti.
```sql
SELECT `degrees`.*,
`teachers`.`name` AS `teacher_name`,
`teachers`.`surname` AS `teacher_surname`
FROM `degrees`

INNER JOIN `courses`
on `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

### 6) Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54).
```sql
SELECT DISTINCT
`teachers`.* 
FROM `teachers`

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

WHERE `departments`.`name` = 'Dipartimento di Matematica';
```

### 7) BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

