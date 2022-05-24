---
## Front matter
title: "Отчёт по лабораторной работе №5"
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

Построить график для модели «хищник-жертва».

# Задание

**Вариант 24**  
  Задача: Для модели «хищник-жертва»:  
  $\frac{\partial x}{\partial t} = -0,29x(t)+0,039x(t)y(t)$  
  $\frac{\partial y}{\partial t} = 0,49y(t)-0,059x(t)y(t)$

Постройте график зависимости численности хищников от численности жертв,
а также графики изменения численности хищников и численности жертв при
следующих начальных условиях: $x_{0} = 8$, $y_{0} = 17$.
Найдите стационарное состояние системы.

# Выполнение лабораторной работы

**1. Теоритические сведения**

Простейшая модель взаимодействия двух видов типа «хищник — жертва» -
модель Лотки-Вольтерры. Данная двувидовая модель основывается на
следующих предположениях:  
  1. Численность популяции жертв x и хищников y зависят только от времени
(модель не учитывает пространственное распределение популяции на
занимаемой территории)  
  2. В отсутствии взаимодействия численность видов изменяется по модели
Мальтуса, при этом число жертв увеличивается, а число хищников падает  
  3. Естественная смертность жертвы и естественная рождаемость хищника
считаются несущественными  
  4. Эффект насыщения численности обеих популяций не учитывается  
  5. Скорость роста численности жертв уменьшается пропорционально
численности хищников:
 
  $\frac{\partial x}{\partial t} = ax(t)-bx(t)y(t)$  
  $\frac{\partial y}{\partial t} = -cy(t)+dx(t)y(t)$

В этой модели x – число жертв, y - число хищников. Коэффициент a
описывает скорость естественного прироста числа жертв в отсутствие хищников, с
- естественное вымирание хищников, лишенных пищи в виде жертв. Вероятность
взаимодействия жертвы и хищника считается пропорциональной как количеству
жертв, так и числу самих хищников (xy). Каждый акт взаимодействия уменьшает
популяцию жертв, но способствует увеличению популяции хищников (члены -bxy
и dxy в правой части уравнения).  
  Стационарное состояние системы (1) (положение равновесия, не зависящее
от времени решение) будет в точке:
 
  $x_{0} = \frac{c}{d}$  
  $y_{0} = \frac{a}{b}$ 

**2. Построение графика**

2. Написал программу на Scilab:
```
a= 0.29;
b= 0.039;
c= 0.49;
d= 0.059;
function dx=syst2(t, x)
dx(1) = -a*x(1) + c*x(1)*x(2);
dx(2) = b*x(2) - d*x(1)*x(2);
endfunction
t0 = 0;
x0=[8;17];
t = [0: 0.1: 400];
y = ode(x0, t0, t, syst2);
n = size(y, "c");
for i = 1: n
y2(i) = y(2, i);
y1(i) = y(1, i);
end
xcc=c/d;
ycc=a/b;
//plot(t,y1);
//plot(t,y2);
plot(y1,y2)

```
Получил следующиq график (см. рис. -@fig:001).

![Рис. 1. График](image/1.JPG){ #fig:001 width=70% }

**3. Стационарное состояние**

Стационарная точка будет иметь коориднаты 

![Рис. 2. коориднаты](image/2.JPG){ #fig:001 width=70% }

# Выводы

Построил график для модели «хищник-жертва».