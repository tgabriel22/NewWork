---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №_03 / Дискреционное разграничение прав в Linux. Два пользователя"
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

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.


# Выполнение лабораторной работы

1. В установленной операционной системе создал учётную запись пользователя guest (использую учётную запись администратора):
`useradd guest` (изображение 01)
2. Задал пароль для пользователя guest (использую учётную запись администратора):
`passwd guest` (изображение 01)
3. Аналогично создал  второго пользователя guest2. (изображение 01)
4. Добавил пользователя guest2 в группу guest: 
`gpasswd -a guest2 guest` (изображение 001)

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab03/report/image/Capture1-1.PNG){#fig:001 width=70%}

5. Осуществил вход в систему от двух пользователей на двух разных консолях: guest на первой консоли и guest2 на второй консоли. (изображение 002 - 003)
6. Для обоих пользователей командой pwd определил директорию, в которой вы находитесь. Сравните её с приглашениями командной строки. (изображение 002 - 003)
7. Уточнил имя вашего пользователя, его группу, кто входит в неё
и к каким группам принадлежит он сам. Определил командами
groups guest и groups guest2, в какие группы входят пользователи guest и guest2. Сравнил вывод команды groups с выводом команд
id -Gn и id -G. (изображение 002 - 003)

![изображение 002](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab03/report/image/Capture1-2.PNG){#fig:002 width=70%}

![изображение 003](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab03/report/image/Capture3.PNG){#fig:003 width=70%}


8. Сравните полученную информацию с содержимым файла /etc/group.
Просмотрите файл командой
`cat /etc/group`

![изображение 004](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab03/report/image/Capture5.PNG){#fig:004 width=70%}

9. От имени пользователя guest2 выполните регистрацию пользователя
guest2 в группе guest командой
`newgrp guest` 

![изображение 005](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab03/report/image/Capture4.PNG){#fig:005 width=70%}

10. От имени пользователя guest измените права директории /home/guest,
разрешив все действия для пользователей группы:
`chmod g+rwx /home/guest` (изображение 006)
11. От имени пользователя guest снимите с директории /home/guest/dir1
все атрибуты командой
`chmod 000 dirl` (изображение 006)

![изображение 006](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab03/report/image/Capture2.PNG){#fig:006 width=70%}


12. Заполнили таблицу возможных действий с различными атрибутами директории 

| **Права директории**             | [000] | [010] | [020] | [030] | [040] | [050] | [060] | [070] |
|----------------------------------|-------|-------|-------|-------|-------|-------|-------|-------|
| **Права файла**                  | **[000]** | **[010]** | **[020]** | **[030]** | **[040]** | **[050]** | **[060]** | **[070]** |
| **Создание файла**               | -     | -     | -     | +     | -     | -     | -     | +     |
| **Удаление файла**               | -     | -     | -     | +     | -     | -     | -     | +     |
| **Запись в файл**                | -     | +     | -     | -     | -     | +     | -     | +     |
| **Чтение файла**                 | -     | +     | -     | +     | -     | +     | -     | +     |
| **Смена директории**             | -     | -     | -     | +     | -     | -     | -     | +     |
| **Просмотр файлов в директории** | -     | -     | -     | -     | -     | +     | +     | +     |
| **Переименование**               | -     | -     | -     | +     | -     | -     | -     | +     |
| **Смена атрибутов файла**        | -     | -     | -     | -     | -     | -     | -     | -     |


13. Заполнили таблицу минимально неободимых атрибутов для определенных действий 

| **Операция**               | **Мин. права на директ.** | **Мин. права на файл** |
|----------------------------|---------------------------|------------------------|
| **Создание файла**         | 030                       | 020                    |
| **Удаление файла**         | 030                       | 030                    |
| **Чтение файла**           | 010                       | 020                    |
| **Запись в файл**          | 010                       | 050                    |
| **Переименование файла**   | 030                       | 010                    |
| **Создание поддиректории** | 030                       | 040                    |
| **Удаление поддиректории** | 030                       | 020                    |



# Выводы

Получили практических навыков работы в консоли с атрибутами файлов для групп пользователей.

# Список литературы{.unnumbered}

::: {#refs}
:::