---
title: 'Chapter Title Here'
description: 'Chapter description goes here.'
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

## Линейная регрессия

```yaml
type: NormalExercise
key: d69d502d3d
lang: r
xp: 100
skills: 1
```



`@instructions`
- Постройте линейную регрессию x от y и z и запишите ее в переменную fit.

`@hint`


`@pre_exercise_code`
```{r}
x=rnorm(10000)
y=x+rnorm(10000,1,1.5)
z=x>2
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
z=x+rnorm(10000,0,5)>3
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
