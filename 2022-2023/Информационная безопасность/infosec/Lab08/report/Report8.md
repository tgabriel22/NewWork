---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №_08 / Элементы
криптографии. Шифрование (кодирование)
различных исходных текстов одним ключом
"
author: "Габриэль Тьерри"

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

Освоить на практике применение режима однократного гаммирования на примере кодирования различных исходных текстов одним ключом.

# Задание
Два текста кодируются одним ключом (однократное гаммирование).
Требуется не зная ключа и не стремясь его определить, прочитать оба текста. Необходимо разработать приложение, позволяющее шифровать и дешифровать тексты $P_1$ и $P_2$ в режиме однократного гаммирования. Приложение должно определить вид шифротекстов $C_1$ и $C_2$ обоих текстов $P_1$ и $P_2$ при известном ключе ; Необходимо определить и выразить аналитически способ, при котором злоумышленник может прочитать оба текста, не зная ключа и не стремясь его определить.

# Выполнение лабораторной работы

Определил функцию шифрования и дешифрования

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab08/report/image/Capture1.PNG){#fig:001 width=70%}

генерируем ключ

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab08/report/image/Capture2.PNG){#fig:001 width=70%}

Вызов зашифрованные сообщения

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab08/report/image/Capture3.PNG){#fig:001 width=70%}

Пример обратного шифрования

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab08/report/image/Capture4.PNG){#fig:001 width=70%}

# Выводы

Освоил на практике применение режима однократного гаммирования на примере кодирования различных исходных текстов одним ключом.