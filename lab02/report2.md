---
## Front matter
title: "Отчёт по лабораторной работе №2"
subtitle: "дисциплина: Математическое моделирование"
author: "Разважный Георгий Геннадиевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: cite.bib
csl: gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---


# Цель работы

Построить графики задачи о погоне.

# Задание

**Вариант 24**  
  Задача: На море в тумане катер береговой охраны преследует лодку браконьеров.
Через определенный промежуток времени туман рассеивается, и лодка
обнаруживается на расстоянии 11,4 км от катера. Затем лодка снова скрывается в
тумане и уходит прямолинейно в неизвестном направлении. Известно, что скорость
катера в 4,1 раза больше скорости браконьерской лодки.
1. Запишите уравнение, описывающее движение катера, с начальными
условиями для двух случаев (в зависимости от расположения катера
относительно лодки в начальный момент времени).
2. Постройте траекторию движения катера и лодки для двух случаев.
3. Найдите точку пересечения траектории катера и лодки 

# Выполнение лабораторной работы

**Провести аналогичные рассуждения и вывод дифференциальных уравнений,
если скорость катера больше скорости лодки в n раз**
  
На море в тумане катер береговой охраны преследует лодку браконьеров.
Через определенный промежуток времени туман рассеивается, и лодка
обнаруживается на расстоянии 11,4 км от катера. Затем лодка снова скрывается в
тумане и уходит прямолинейно в неизвестном направлении. Известно, что скорость
катера в 4,1 раза больше скорости браконьерской лодки.

**Построить траекторию движения катера и лодки для двух случаев.**

2.1. Написал программу на SciLab для перого случая:
```
s1=114/51;
s2=114/31;
fi=3*%pi/4;
function dr=f(tetha, r)
dr=r/sqrt(15.83);
endfunction;
r1=s1;
r2=s2;
tetha01=0;
tetha02=-%pi;
tetha=0:0.01:2*%pi;
r1=ode(r1,tetha01,tetha,f);
r2=ode(r2,tetha02,tetha,f);
function xt=f2(t)
 xt=tan(fi)*t;
endfunction
t=0:1:50;
polarplot(tetha,r1,style = color('green')); 
polarplot(tetha,r2,style = color('blue')); 
plot2d(t,f2(t),style = color('red'));


```
Получил следующий график (см. рис. -@fig:001).

![Рис. 1. График для 1 случая](image/1.JPG){ #fig:001 width=70% }

2.2. Написал программу на SciLab для 2 случая:
```
s1=114/51;
s2=114/31;
fi=3*%pi/4;
function dr=f(tetha, r)
dr=r/sqrt(15.83);
endfunction;
r1=s1;
r2=s2;
tetha01=0;
tetha02=-%pi;
tetha=0:0.01:2*%pi;
r1=ode(r1,tetha01,tetha,f);
r2=ode(r2,tetha02,tetha,f);
function xt=f2(t)
 xt=tan(fi)*t;
endfunction
t=0:1:50;
polarplot(tetha,r1,style = color('green')); 
polarplot(tetha,r2,style = color('blue')); 
plot2d(t,f2(t),style = color('red'));

```
Получил следующий график (см. рис. -@fig:002).

![Рис. 2. График для 2 случая](image/1.JPG){ #fig:002 width=70% }

![Рис. 3](image/3.JPG){ #fig:002 width=70% }

# Выводы

Построил графики движения катера и лодки.
