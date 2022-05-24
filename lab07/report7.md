---
## Front matter
title: "Отчёт по лабораторной работе №7"
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

Построить график распространения рекламы.

# Задание

**Вариант 35**  
  Задача: постройте график распространения рекламы, математическая модель которой описывается
следующим уравнением:  
  1. $\frac{\partial n}{\partial t} = (0.88+0.00008*n(t))(N-n(t))$  
  2. $\frac{\partial n}{\partial t} = (0.00008+0.88*n(t))(N-n(t))$  
  3. $\frac{\partial n}{\partial t} = (0.7*t+0.6*sin(t)*n(t))(N-n(t))$  
  
  При этом объем аудитории N = 1230, в начальный момент о товаре знает 14 человек. Для
случая 2 определите в какой момент времени скорость распространения рекламы будет
иметь максимальное значение.

# Выполнение лабораторной работы

**1. Теоритические сведения**

Организуется рекламная кампания нового товара или услуги. Необходимо,
чтобы прибыль будущих продаж с избытком покрывала издержки на рекламу.
Вначале расходы могут превышать прибыль, поскольку лишь малая часть
потенциальных покупателей будет информирована о новинке. Затем, при
увеличении числа продаж, возрастает и прибыль, и, наконец, наступит момент,
когда рынок насытиться, и рекламировать товар станет бесполезным.  
  Предположим, что торговыми учреждениями реализуется некоторая
продукция, о которой в момент времени t из числа потенциальных покупателей N
знает лишь n покупателей. Для ускорения сбыта продукции запускается реклама
по радио, телевидению и других средств массовой информации. После запуска
рекламной кампании информация о продукции начнет распространяться среди
потенциальных покупателей путем общения друг с другом. Таким образом, после
запуска рекламных объявлений скорость изменения числа знающих о продукции
людей пропорциональна как числу знающих о товаре покупателей, так и числу
покупателей о нем не знающих.  
  Модель рекламной кампании описывается следующими величинами.
Считаем, что $\frac{\partial n}{\partial t}$ - скорость изменения со временем числа потребителей,
узнавших о товаре и готовых его купить, t - время, прошедшее с начала рекламной
кампании, n(t) - число уже информированных клиентов. Эта величина
пропорциональна числу покупателей, еще не знающих о нем, это описывается
следующим образом: $a_{1}(t)(N-n(t))$, где N - общее число потенциальных
платежеспособных покупателей, $a_{1}(t)>0$ - характеризует интенсивность
рекламной кампании (зависит от затрат на рекламу в данный момент времени).
Помимо этого, узнавшие о товаре потребители также распространяют полученную
информацию среди потенциальных покупателей, не знающих о нем (в этом случае
работает т.н. сарафанное радио). Этот вклад в рекламу описывается величиной
$a_{2}(t)n(t)(N-n(t))$, эта величина увеличивается с увеличением потребителей
узнавших о товаре. Математическая модель распространения рекламы описывается
уравнением: $\frac{\partial n}{\partial t} = (0.91+0.00005*n(t))(N-n(t))$ 

**2. Построение графиков**

2.1 Написал программу на Scilab:
```
t0 = 0;
x0 = 14;
N = 1230;
t = 0: 0.1: 30;
function g=k(t);
g = 0.7*t;
endfunction
function v=p(t);
v = 0.6*sin(t);
endfunction
function xd=f(t, x);
xd = ( k(t) + p(t)*x )*( N - x );
endfunction
x = ode(x0, t0, t, f);
plot(t, x);
mas = [x]
i = 2: 1: 300;
if (mas(i)- mas(i-1) > maximal) then maximal = (mas(i)- mas(i-1));
end
bg = max (maximal)
disp(maximal)
disp(bg)

```
Получил следующий график (см. рис. -@fig:001).

![Рис. 1. График для 1 случая](image/1.JPG){ #fig:001 width=70% }  

Нашел точку для кажого графика где 
эффективность рекламы имеет наибольший показатель.

![Рис. 1.](image/2.JPG){ #fig:002 width=70% }  

2.2 Написал программу на Scilab(Изменил некоторые значения):
```
t0 = 0;
x0 = 14;
N = 1230;
t = 0: 0.1: 30;
function g=k(t);
g = 0.7*t;
endfunction
function v=p(t);
v = 0.6*sin(t);
endfunction
function xd=f(t, x);
xd = ( k(t) + p(t)*x )*( N - x );
endfunction
x = ode(x0, t0, t, f);
plot(t, x);
mas = [x]
i = 2: 1: 300;
if (mas(i)- mas(i-1) > maximal) then maximal = (mas(i)- mas(i-1));
end
bg = max (maximal)
disp(maximal)
disp(bg)

```
Получил следующий график (см. рис. -@fig:003).

![Рис. 3. График для 2 случая](image/3.JPG){ #fig:003 width=70% }

2.3 Написал программу на Scilab:
```
t0 = 0;
x0 = 14;
N = 1230;
t = 0: 0.1: 30;
function g=k(t);
g = 0.7*t;
endfunction
function v=p(t);
v = 0.6*sin(t);
endfunction
function xd=f(t, x);
xd = ( k(t) + p(t)*x )*( N - x );
endfunction
x = ode(x0, t0, t, f);
plot(t, x);
mas = [x]
i = 2: 1: 300;
if (mas(i)- mas(i-1) > maximal) then maximal = (mas(i)- mas(i-1));
end
bg = max (maximal)
disp(maximal)
disp(bg)

```
Получил следующий график (см. рис. -@fig:003).

![Рис. 4. График для 3 случая](image/4.JPG){ #fig:004 width=70% }  

# Выводы

Построить график распространения рекламы.