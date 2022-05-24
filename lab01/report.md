---
## Front matter
title: "Отчёт по лабораторной работе №1"
subtitle: "дисциплина: Математическое моделирование"
author: "Разважный Георгий Геннадиевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

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

Настроить Git и научиться им пользоваться, 
а так же изучить язык разметки Markdown

# Задание

 1.1 Подготовка
 
 1.2 Создание проекта
 
 1.3 Внесение изменений
 
 1.4 Индексация изменений
 
 1.5 Отмена локальных изменений (до индексации)
 
 1.6 Отмена проиндексированных изменений (перед коммитом)
 
 1.7 Отмена коммитов
 
 1.8 Удаление коммиттов из ветки
 
 1.9 Удаление тега oops
 
 1.10 Внесение изменений в коммиты
 
 1.11 Перемещение файлов
 
 1.12 Второй способ перемещения файлов
 
 1.13 Подробнее о структуре
 
 1.14 Git внутри: Каталог .git
 
 1.15 Работа непосредственно с объектами git
 
 1.16 Создание ветки
 
 1.17 Навигация по веткам
 
 1.18 Изменения в ветке master
 
 1.19 Сделайте коммит изменений README.md в ветку master.
 
 1.20 Слияние
 
 1.21 Создание конфликта
 
 1.22 Разрешение конфликтов
 
 1.23 Сброс ветки style
 
 1.24 Сброс ветки master
 
 1.25 Перебазирование
 
 1.26 Слияние в ветку master

 1.27 Клонирование репозиториев
 
 1.28 Просмотр клонированного репозитория
 
 1.29 Что такое origin?
 
 1.30 Удаленные ветки
 
 1.31 Изменение оригинального репозитория
 
 1.32 Слияние извлеченных изменений

1.33 Добавление ветки наблюдения

1.34 Чистые репозитории

1.35 Создайте чистый репозиторий

1.36 Добавление удаленного репозитория

1.37 Отправка изменений

1.38 Извлечение общих изменений

# Выполнение лабораторной работы

1.1 Подготовка


1.1.1 Установка имени и электронной почты
Если вы никогда ранее не использовали git, для начала вам необходимо осуще-
ствить установку. Выполните следующие команды, чтобы git узнал ваше имя и
электронную почту. Если git уже установлен, можете переходить к разделу оконча-
ния строк.

git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"

![Рис. 1. График для 1 случая](image/1.png){ #fig:001 width=70% }


1.1.2 Параметры установки окончаний строк
Настройка core.autocrlf с параметрами true и input делает все переводы
строк текстовых файлов в главном репозитории одинаковы.
core.autocrlf true - git автоматически конвертирует CRLF->LF при комми-
те и обратно LF->CRLF при выгрузке кода из репозитория на файловую систему
(используют в Windows). core.autocrlf input - конвертация CRLF в LF только
при коммитах (используют в Mac/Linux).
Если core.safecrlf установлен в true или warm, git проверяет, если пре-
образование является обратимым для текущей настройки core.autocrlf.
core.safecrlf true - отвержение необратимого преобразования lf<->crlf.
Полезно, когда специфические бинарники похожие на текстовые файлы.
core.safecrlf warn - печать только предупреждение, но принимает необрати-
мый переход.

Для пользователей Unix/Mac:

git config --global core.autocrlf input