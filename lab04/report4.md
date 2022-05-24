---
## Front matter
title: "Отчёт по лабораторной работе №4"
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

Построить фазовый портрет гармонического осциллятора и решенить уравнения
гармонического осциллятора.

# Задание

**Вариант 24**  
  Задача: ППостройте фазовый портрет гармонического осциллятора и решение уравнения
гармонического осциллятора для следующих случаев 

1. Колебания гармонического осциллятора без затуханий и без действий внешней
силы  $x'' + 9x = 0$

2. Колебания гармонического осциллятора c затуханием и без действий внешней
силы $x'' + x' + 4.9x = 0$

3. Колебания гармонического осциллятора c затуханием и под действием внешней
силы $x'' + x' + 9.9x = 0,2sin(3.5t)$

На интервале t = [0;49] (шаг 0.05) с начальными условиями $x_{0}=-0.5$, $y_{0}=-1$ 

# Выполнение лабораторной работы

**1. Теоритические сведения**

Движение грузика на пружинке, маятника, заряда в электрическом контуре, а
также эволюция во времени многих систем в физике, химии, биологии и других
науках при определенных предположениях можно описать одним и тем же
дифференциальным уравнением, которое в теории колебаний выступает в качестве
основной модели. Эта модель называется линейным гармоническим осциллятором.
Уравнение свободных колебаний гармонического осциллятора имеет
следующий вид:  
  $x'' + 2yx' + w_{0}^2x = 0$  
  где x – переменная, описывающая состояние системы (смещение грузика, заряд
конденсатора и т.д.), y – параметр, характеризующий потери энергии (трение в
механической системе, сопротивление в контуре), $w_{0}$ – собственная частота
колебаний, t – время.  
  Предыдущее уравнение - линейное однородное дифференциальное уравнение
второго порядка и оно является примером линейной динамической системы.  
  При отсутствии потерь в системе ($y = 0$ получаем уравнение консервативного осциллятора энергия колебания которого сохраняется
во времени: $x'' + w_{0}^2x = 0$. Для однозначной разрешимости уравнения второго порядка необходимо
задать два начальных условия $x(t_{0}) = x_{0}$ и $x'(t_{0}) = y_{0}$.  
  Уравнение второго порядка можно представить в виде системы двух
уравнений первого порядка: $x' = y$ и $y' = -w_{0}^2x$; и тогда начальные условия примут вид: $x(t_{0}) = x_{0}$ и $y(t_{0}) = y_{0}$.

**2. Построение графиков**

2.1. Написал программу на Scilab:
```
w = sqrt(5.9);
g = 1;
function f=f(t)
f = 9.9*sin(t); //sin 0 = 0
endfunction
function dx=y(t, x)
dx(1) = x(2);
dx(2) = -w.* w.* x(1) - g.* x(2) - f(t);
endfunction
t0 = 0;
x0 = [-0.5;1];
t = [0:0.05:49];
x = ode(x0, t0, t, y);
n = size(x, "c");
for i = 1: n
y1(i) = x(1, i);
y2(i) = x(2, i);
end
plot(y1, y2);
xgrid();

```
Получил следующие графики (см. рис. -@fig:001, -@fig:002, -@fig:003).

![Рис. 1. График для 1 случая](image/1.JPG){ #fig:001 width=70% }

![Рис. 2. График для 2 случая](image/2.JPG){ #fig:002 width=70% }

![Рис. 3. График для 3 случая](image/3.JPG){ #fig:003 width=70% }

# Выводы

Построил фазовый портрет гармонического осциллятора и решенил уравнения
гармонического осциллятора.
