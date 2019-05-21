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
