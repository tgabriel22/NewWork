---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №_05 / Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов"
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

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.

# Выполнение лабораторной работы

##  Создание программы

- Проверил, что компилятор gcc установлен, используя команду `gcc --version`
- отключил систему запретов до очередной перезагрзка системы командой `sudo setenforce 0`, после чего команда `getenforce` вывела `Permissive`
- Проверил успешное выполнение команд `whereis gcc` и `whereis g++`

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture1.PNG){#fig:001 width=70%}

1. Вошел в систему от имени пользователя guest командой `su - guest`. Создал программу `simpleid.c` командой `touch simpleid.c` и открыл её в редакторе командой `vim /home/guest/simpleid.c`

![изображение 002](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture2.PNG){#fig:002 width=70%}

- Код программы:

![изображение 003](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture3.PNG){#fig:003 width=70%}

3. Скомпилировал программу и убедился, что файл программы был создан командой “gcc simpleid.c -o simpleid”
4. Выполнил программу simpleid командой “./simpleid” 
5. выполнил системную программу id командой “id”

![изображение 004](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture4.PNG){#fig:004 width=70%}

6. Усложнил программу, добавив вывод действительных идентификаторов
7.  Скомпилировал и запустил simpleid2.c командами `gcc simpleid2.c -o simpleid2` и `./simpleid2`

![изображение 005](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture5.PNG){#fig:005 width=70%}

![изображение 006](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture6.PNG){#fig:006 width=70%}

8. От имени суперпользователя выполнил команды `sudo chown root:guest /home/guest/simpleid2` и `sudo chmod u+s /home/guest/simpleid2`
9. повысил временно свои права с помощью su.
10. выполнил проверку правильности установки новых атрибутов и смены владельца файла simpleid2
11. Запустил программы simpleid2 и id. 
12. Проделал тоже самое относительно SetGID-бита.

![изображение 007](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture7.PNG){#fig:007 width=70%}

13. Создал программу readfile.c

![изображение 008](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture8.PNG){#fig:008 width=70%}

![изображение 009](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture9.PNG){#fig:009 width=70%}

![изображение 010](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture10.PNG){#fig:010 width=70%}

![изображение 011](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture11.PNG){#fig:011 width=70%}

![изображение 012](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture12.PNG){#fig:012 width=70%}

## Исследование Sticky-бита

1. Выяснил, установлен ли атрибут Sticky на директории /tmp, для чего выполните команду ls -l / | grep tmp

2. От имени пользователя guest создал файл file01.txt в директории /tmp со словом test: echo "test" > /tmp/file01.txt

3. Просмотрил атрибуты у только что созданного файла и разрешил чтение и запись для категории пользователей «все остальные»: ls -l /tmp/file01.txt chmod o+rw /tmp/file01.txt ls -l /tmp/file01.txt

4. . От пользователя guest2 (не являющегося владельцем) попробовал прочитать файл /tmp/file01.txt: cat /tmp/file01.txt

5. От пользователя guest2 попробовал дозаписать в файл /tmp/file01.txt слово test2 командой echo "test2" > /tmp/file01.txt Удалось ли вам выполнить операцию?

![изображение 013](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture13.PNG){#fig:012 width=70%}

6. Проверил содержимое файла командой cat /tmp/file01.txt

7. От пользователя guest2 попробовал записать в файл /tmp/file01.txt слово test3, стерев при этом всю имеющуюся в файле информацию командой
echo "test3" > /tmp/file01.txt Удалось ли вам выполнить операцию?

8. Проверил содержимое файла командой cat /tmp/file01.txt

9. От пользователя guest2 попробовал удалить файл /tmp/file01.txt командой rm /tmp/fileOl.txt
Удалось ли вам удалить файл?

10. Повысил свои права до суперпользователя следующей командой su - и выполнил после этого команду, снимающую атрибут t (Sticky-бит) с
директории /tmp: chmod -t /tmp

11. Покинул режим суперпользователя командой exit

12. От пользователя guest2 Проверил, что атрибута t у директории /tmp нет: ls -l / | grep tmp

13. Повторил предыдущие шаги. Какие наблюдаются изменения?

14. Удалось ли вам удалить файл от имени пользователя, не являющегося его владельцем? 

15. Повысил свои права до суперпользователя и верните атрибут t на директорию /tmp: su - chmod +t /tmp exit

![изображение 014](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture14.PNG){#fig:012 width=70%}

# Выводы

Изучение механизмов изменения идентификаторов, применения SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.
