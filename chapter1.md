---
title: 'Chapter Title Here'
description: 'Chapter description goes here.'
free_preview: true
---

## Отрисовка графиков 2

```yaml
type: NormalExercise
key: 4b9400d745
xp: 100
```



`@instructions`
- У вас есть случайная величина x.
- Постройте её линеный график

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(100,0,5)+1:100
y=rnorm(100,0,5)+1:100
```

`@sample_code`
```{r}
x
```

`@solution`
```{r}
plot(x,type='l')
```

`@sct`
```{r}
ex() %>% check_function("plot") %>% check_result() %>% check_equal()

success_msg("Отлично!")
```

---

## Отрисовка линий

```yaml
type: NormalExercise
key: 201ee5e603
xp: 100
```



`@instructions`
- У вас есть случайная величина x.
- Постройте её линеный график 
- Добавьте на график линию y зеленого цвета

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(100,0,5)+1:100
y=rnorm(100,0,5)+1:100
```

`@sample_code`
```{r}
x
y
```

`@solution`
```{r}
plot(x,type='l')
lines(y,col='green')
```

`@sct`
```{r}
ex() %>% check_function("lines") %>% check_result() %>% check_equal()

success_msg("Отлично!")
```

---

## Отрисовка гистограмм

```yaml
type: NormalExercise
key: 2bafef99a3
lang: r
xp: 100
skills: 1
```



`@instructions`
- У вас есть случайная величина x.
- Постройте её гистограмму с разбиением на 100 столбцов.

`@hint`


`@pre_exercise_code`
```{r}
x=rchisq(10000, 40)
```

`@sample_code`
```{r}
x
```

`@solution`
```{r}
hist(x,breaks = 100)
```

`@sct`
```{r}
ex() %>% check_function("hist") %>% {
  check_arg(., "x") %>% check_equal()
  check_arg(., "breaks") %>% check_equal()
}
success_msg("Отлично!")
```

---

## Таблица сопряженности

```yaml
type: NormalExercise
key: a8da81733e
lang: r
xp: 100
skills: 1
```



`@instructions`
- У вас есть две фиктивные переменные x и y.
- Постройте таблицу z сопряженности этих переменных.

`@hint`
Используйте функцию table.

`@pre_exercise_code`
```{r}
x=round(round(runif(10000)))
y=round(round(runif(10000)))
```

`@sample_code`
```{r}
z=
```

`@solution`
```{r}
z=table(x,y)
```

`@sct`
```{r}
ex() %>% check_object("z") %>% check_equal()
success_msg("Отлично!")
```

---

## Таблица сопряженности2

```yaml
type: NormalExercise
key: 48c8962e67
lang: r
xp: 100
skills: 1
```



`@instructions`
- У вас есть таблица сопряженности z
- Проверьте с помощью теста Хи-квадрат наличие зависимость между переменными в случае если вы выбрали 5% квантиль.

`@hint`
Используйте функцию table.

`@pre_exercise_code`
```{r}
x=round(round(runif(10000)))
y=round(round(runif(10000)))
z=table(x,y)
z[1,1]=z[1,1]+200
```

`@sample_code`
```{r}
(z)
```

`@solution`
```{r}
chisq.test(z)
```

`@sct`
```{r}
ex() %>% check_function("chisq.test") %>% check_result() %>% check_equal()

success_msg("Отлично!")
```

---

## Линейная регрессия

```yaml
type: NormalExercise
key: d69d502d3d
lang: r
xp: 100
skills: 1
```



`@instructions`
- Постройте линейную регрессию x от y и z (фиктивная переменная) и запишите ее в переменную fit.

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,1.5)
z=factor(x>2)
```

`@sample_code`
```{r}
fit=

```

`@solution`
```{r}
fit=lm(x~y+z)
```

`@sct`
```{r}
ex() %>% check_object("fit") %>% check_equal()
success_msg("Отлично!")
```

---

## Линейная регрессия 2

```yaml
type: NormalExercise
key: 61661ae339
lang: r
xp: 100
skills: 1
```



`@instructions`
- Постройте линейную регрессию x от y и z (фиктивная переменная) и запишите ее в переменную fit.
- Выведите расширенную версию таблицы отчета

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,1.5)
z=factor(x>2)
```

`@sample_code`
```{r}
fit=
...(fit)
```

`@solution`
```{r}
fit=lm(x~y+z)
summary(fit)
```

`@sct`
```{r}
ex() %>% check_function("summary") %>% check_result() %>% check_equal()
success_msg("Отлично!")
```

---

## Результаты регрессии1

```yaml
type: MultipleChoiceExercise
key: ee0f0d7e10
xp: 50
```

У вас есть результаты линейной регрессии fit. Является ли регрессия значимой?

`@possible_answers`
- Да
- Нет

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=factor(x+rnorm(10000,0,5)>3)
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=summary(fit)
if(a$fstatistic[1]>qf(0.95,a$fstatistic[2],a$fstatistic[3])){
  r=1
}else{r=2}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Результаты регрессии2

```yaml
type: MultipleChoiceExercise
key: 4405348538
xp: 50
```

У вас есть результаты линейной регрессии fit. Является ли переменная y значимой?

`@possible_answers`
- Да
- Нет

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=factor(x+rnorm(10000,0,5)>3)
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=summary(fit)
if(a$coefficients[2,4]>0.05){
  r=2
}else{r=1}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Результаты регрессии3

```yaml
type: MultipleChoiceExercise
key: fb0e070ada
xp: 50
```

У вас есть результаты линейной регрессии fit. Является ли переменная zTRUE значимой?

`@possible_answers`
- Да
- Нет

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=factor(x+rnorm(10000,0,5)>3)
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
a=summary(fit)
if(a$coefficients[3,4]>0.05){
  r=2
}else{r=1}
ex() %>% check_mc(r, feedback_msgs = c(msg2, msg3))
```

---

## Результаты регрессии4

```yaml
type: MultipleChoiceExercise
key: 771f360e71
xp: 50
```

У вас есть результаты линейной регрессии fit. Что обозначает переменная zTRUE?

`@possible_answers`
- На сколько в среднем x в случае z TRUE больше, чем x в случае z FALSE
- В среднем x больше у на величину коэффициента zTRUE
- x является положительной величиной, потому что zTRUE>0

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,100)
z=factor(x+rnorm(10000,0,5)>3)
fit=lm(x~y+z)
```

`@sct`
```{r}
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
ex() %>% check_mc(1, feedback_msgs = c(msg2, msg3))
```
