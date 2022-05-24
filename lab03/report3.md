---
## Front matter
title: "Отчёт по лабораторной работе №3"
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

Построить графики модели боевых действий.

# Задание

**Вариант 24**  
  Между страной Х и страной У идет война. Численность состава войск
исчисляется от начала войны, и являются временными функциями
xt( )
и
yt( ). В
начальный момент времени страна Х имеет армию численностью 400 000 человек,
а в распоряжении страны У армия численностью в 100 000 человек. Для упрощения
модели считаем, что коэффициенты a b c h , , , постоянны. Также считаем Pt( ) и Q t( )непрерывные функции.
Постройте графики изменения численности войск армии Х и армии У для
следующих случаев:

1. Модель боевых действий между регулярными войсками  
  $\frac{\partial x}{\partial t} = -0,31x(t)-0,76y(t)+sin(3t)$  
  $\frac{\partial y}{\partial t} = -0,8x(t)-0,21y(t)+cos(4t)$

2. Модель ведение боевых действий с участием регулярных войск и
партизанских отрядов  
  $\frac{\partial x}{\partial t} = -0,21x(t)-0,7y(t)+sin(10t)$  
  $\frac{\partial y}{\partial t} = -0,56x(t)y(t)-0,15y(t)+cos(10t)$

# Выполнение лабораторной работы

**1. Рассмотрим подробнее уравнения**

1.1. В первом случае потери, не связанные с боевыми действиями, описывают члены -c(t) и -by(t), а
-ay(t) и -dx(t) отражают потери на поле боя. Также sin(t3) и cos(4t) учитывают 
возможность подхода подкрепления к войскам Х и У в течение одного дня.

1.2. Во втором случае в борьбу добавляются партизанские отряды и потери, не связанные с боевыми действиями, описывают члены -0,32x(t) и -0,43y(t), а
-0,21y(t) и -0,7x(t)y(t) отражают потери на поле боя. Также sin(105) и cos(106) учитывают 
возможность подхода подкрепления к войскам Х и У в течение одного дня.  
  

**2. Построение графиков численности войск**

2.1. Написал программу на Scilab для 1 случая:
```
x0 = 400000;
y0 = 100000;
t0 = 0;
a = 0.31;
b = 0.76;
c = 0.8;
h = 0.21;
tmax = 1;
dt = 0.05;
t = [t0:dt:tmax];
function p = P(t)
p = sin(3*t);
endfunction
function q = Q(t)
q = cos(4*t)+2;
endfunction
function dy = syst(t, y)
dy(1) = - a*y(1) - b*y(2) + P(t);
dy(2) = - c*y(1) - h*y(2) + Q(t);
endfunction
v0 = [x0;y0];
y = ode(v0,t0,t,syst);
scf(0);
plot2d(t,y(1,:),style=2);
xtitle('Модель боевых действий № 1','Шаг','Численность армии');
plot2d(t,y(2,:), style = 5);
xgrid();


```
Получил следующий график (см. рис. -@fig:001).

![Рис. 1. График для 1 случая](image/1.JPG){ #fig:001 width=70% }

2.2. Написал программу на Scilab для 2 случая:
```
x0 = 400000;
y0 = 100000;
t0 = 0;
a = 0.31;
b = 0.76;
c = 0.8;
h = 0.21;
tmax = 1;
dt = 0.05;
t = [t0:dt:tmax];
function p = P(t)
p = sin(3*t);
endfunction
function q = Q(t)
q = cos(4*t)+2;
endfunction
function dy = syst(t, y)
dy(1) = - a*y(1) - b*y(2) + P(t);
dy(2) = - c*y(1) - h*y(2) + Q(t);
endfunction
v0 = [x0;y0];
y = ode(v0,t0,t,syst);
scf(0);
plot2d(t,y(1,:),style=2);
xtitle('Модель боевых действий № 1','Шаг','Численность армии');
plot2d(t,y(2,:), style = 5);
xgrid();

```
Получил следующий график (см. рис. -@fig:002).

![Рис. 2. График для 2 случая](image/2.JPG){ #fig:002 width=70% }

# Выводы

Построил графики модели боевых действий.
