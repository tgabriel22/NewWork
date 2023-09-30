---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №_04 / Дискреционное разграничение прав в Linux. Расширенные атрибуты"
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
Получение практических навыков работы в консоли с расширенными атрибутами файлов.

# Выполнение лабораторной работы

1. От имени пользователя guest определите расширенные атрибуты файла `/home/guest/dir1/file1` командой `lsattr /home/guest/dir1/file1`. (изображение 001)
 
2. Установите командой `chmod 600 file1` на файл file1 права, разрешающие чтение и запись для владельца файла. (изображение 001)

3. Попробуйте установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
`chattr +a /home/guest/dir1/file1`. (изображение 001)

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab04/report/image/Capture1.PNG){#fig:001 width=70%}

4. Зайдите на третью консоль с правами администратора либо повысьте свои права с помощью команды su. Попробуйте установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя:
`chattr +a /home/guest/dir1/file1`. (изображение 002)

5. От пользователя guest проверьте правильность установления атрибута: `lsattr /home/guest/dir1/file1`. (изображение 002)

6. Выполните дозапись в файл file1 слова «test» командой 
`echo "test" /home/guest/dir1/file1`. (изображение 002)
После этого выполните чтение файла file1 командой
`cat /home/guest/dir1/file1`
Убедитесь, что слово test было успешно записано в file1. (изображение 002)

![изображение 002](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab04/report/image/Capture2.PNG){#fig:002 width=70%}

7. Попробуйте удалить файл file1 либо стереть имеющуюся в нём информацию командой
`echo "abcd" > /home/guest/dirl/file1`
Попробуйте переименовать файл. (изображение 003)

8.  Попробуйте с помощью команды
`chmod 000 file1`
установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. Удалось ли вам успешно выполнить указанные команды? (изображение 003)

![изображение 003](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab04/report/image/Capture3.PNG){#fig:003 width=70%}

9. Снимите расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя командой
`chattr -a /home/guest/dir1/file1`
Повторите операции, которые вам ранее не удавалось выполнить. Ваши наблюдения занесите в отчёт. (изображение 004)


10. . Повторите ваши действия по шагам, заменив атрибут «a» атрибутом «i». Удалось ли вам дозаписать информацию в файл? 
- Нет, не удалось

В результате выполнения работы вы повысили свои навыки использования интерфейса командой строки (CLI), познакомились на примерах с тем,
как используются основные и расширенные атрибуты при разграничении доступа. Имели возможность связать теорию дискреционного разделения доступа (дискреционная политика безопасности) с её реализацией на практике в ОС Linux. Составили наглядные таблицы, поясняющие какие операции возможны при тех или иных установленных правах. Опробовали действие на практике расширенных атрибутов «а» и «i». (изображение 004)

![изображение 004](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab04/report/image/Capture4.PNG){#fig:004 width=70%}

# Выводы

Получение практических навыков работы в консоли с расширенными атрибутами файлов.