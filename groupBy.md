# QUERY CON GROUP BY

### 1) Contare quanti iscritti ci sono stati ogni anno.
```sql
SELECT YEAR(`enrolment_date`) AS `year`,
COUNT(*) AS `subscribers`
FROM `students`
GROUP BY YEAR(`enrolment_date`);
```

### 2)c Contare gli insegnanti che hanno l'ufficio nello stesso edificio.
```sql
SELECT `office_address`, 
COUNT(*) AS `same_office_address`
FROM `teachers` 
GROUP BY `office_address`;
```

### 3) Calcolare la media dei voti di ogni appello d'esame.
```sql
SELECT `exam_id`, 
AVG(`vote`) AS `average_vote`
FROM `exam_student`
GROUP BY `exam_id`;
```


### 4) Contare quanti corsi di laurea ci sono per ogni dipartimento.
```sql
SELECT `department_id`, 
COUNT(`name`) AS `degree_courses`
FROM `degrees`
GROUP BY `department_id`;
```