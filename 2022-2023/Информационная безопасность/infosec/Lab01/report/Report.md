---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №_01"
author: "Габриэль Тьерри"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: cite.bib
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

Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.


# Задание

- Лабораторная работа подразумевает установку на виртуальную машину VirtualBoх операционной системы Linux (дистрибутив Rocky или CentOS)
- Изучить идеологию и применение средств контроля версий.
- Освоить умения по работе с git.
- Научиться оформлять отчёты с помощью легковесного языка разметки Markdow


# Выполнение лабораторной работы

1. Создаем  виртуальную машину. Операционная система Rocky 9, RAM 2048 МБ, Жесткий диск 40 Гб, Тип Linux версия Red Hat.

![Краткий обзор конфигурации виртуальной машины](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture1.PNG){#fig:001 width=70%}

![Краткий обзор конфигурации виртуальной машины](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture2.PNG){#fig:002 width=70%}

![Начало установки](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture3.PNG){#fig:003 width=70%}

2. Получим следующую информацию с помощью команды "dmesg | grep -i"

![Версия ядра Linux](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture5.PNG){#fig:004 width=70%}

![Модель процессора](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture7.PNG){#fig:005 width=70%}

![Тип файловой системы корневого раздела](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture8.PNG){#fig:006 width=70%}

![Объем доступной оперативной памяти _ Частота процессора _ Тип обнаруженного гипервизора](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture9.PNG){#fig:007 width=70%}

3. Создали репозиторий курса на github

![репозиторий курса](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/github.PNG){#fig:008 width=70%}

# Выводы

Для лабораторных работ я установил операционную систему Linux Rocky с помощью VirtualBox, изучил идеологию и применение средств контроля версий, овладел навыками работы с git, научился проектировать отчеты с использованием облегченного языка разметки Markdonw

# Список литературы{.unnumbered}

:::{#refs}
:::   