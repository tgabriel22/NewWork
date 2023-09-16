---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Лабораторная работа №_02"
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
Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux1

# Выполнение лабораторной работы.

1. В установленной при выполнении предыдущей лабораторной работы
операционной системе создайте учётную запись пользователя guest (использую учётную запись администратора): </br>
`useradd guest` </br>

![Рис_1](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture1.PNG){#fig:001 width=70%}

2. Задайте пароль для пользователя guest (использую учётную запись администратора):
`passwd guest` </br>

![Рис_2](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture.2PNG.PNG){#fig:002 width=70%}

3. Войдите в систему от имени пользователя guest. </br>

![Рис_3](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture3.PNG){#fig:003 width=70%}

4. Определите директорию, в которой вы находитесь, командой `pwd`. Сравните её с приглашением командной строки. Определите, является ли она вашей домашней директорией?
- Да </br>

![Рис_4](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture4.PNG){#fig:004 width=70%}

5. Уточните имя вашего пользователя командой `whoami`. </br>

![Рис_5](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture5.PNG){#fig:005 width=70%}

6. Уточните имя вашего пользователя, его группу, а также группы, куда входит пользователь, командой `id`. Выведенные значения uid, gid и др. запомните. Сравните вывод id с выводом команды `groups`.
- значения совпадают.

![Рис_6](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture6.PNG){#fig:006 width=70%}

7. Сравните полученную информацию об имени пользователя с данными,
выводимыми в приглашении командной строки.
- значения совпадают.(Рис_6) </br>

8. Просмотрите файл `/etc/passwd` командой
`cat /etc/passwd`
Найдите в нём свою учётную запись. Определите uid пользователя.
- 1001 (Рис_6)</br>

Определите gid пользователя.
- 1001 (Рис_6)</br>

Сравните найденные значения с полученными в предыдущих пунктах. - значения совпадают.  </br>
`cat /etc/passwd | grep guest` </br>

![Рис_7](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture7.PNG){#fig:007 width=70%}

![Рис_8](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture8.PNG){#fig:008 width=70%}

9. Определите существующие в системе директории командой
`ls -l /home/`
Удалось ли вам получить список поддиректорий директории /home?
- Да 
</br>

Какие права установлены на директориях? </br>
- Обе директории имеют права на чтение, запись и исполнение только для владельца директорий.  </br>

![Рис_9](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture9.PNG){#fig:009 width=70%}

10. Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой:
lsattr /home
Удалось ли вам увидеть расширенные атрибуты директории? </br>
Удалось ли вам увидеть расширенные атрибуты директорий других
пользователей? </br>
- Посмотреть расширенные атрибуты удалось только для пользователя guest. Они отсутствуют. </br>

![Рис_10](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture10.PNG){#fig:010 width=70%}

11. Создайте в домашней директории поддиректорию dir1 командой
`mkdir dir1`
Определите командами `ls -l` и `lsattr`, какие права доступа и расширенные атрибуты были выставлены на директорию dir1. </br>

![Рис_11](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture11.PNG){#fig:011 width=70%}

12. Снимите с директории dir1 все атрибуты командой
`chmod 000 dir1`
и проверьте с её помощью правильность выполнения команды
`ls -l` </br>

![Рис_12](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture12.PNG){#fig:012 width=70%}


13. Попытайтесь создать в директории dir1 файл file1 командой
`echo "test" > /home/guest/dir1/file1`
Объясните, почему вы получили отказ в выполнении операции по созданию файла? 
- нет прав
Оцените, как сообщение об ошибке отразилось на создании файла? 
- файл не создался
Проверьте командой
`ls -l /home/guest/dir1`
действительно ли файл file1 не находится внутри директории dir1. </br>

![Рис_13](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture13.PNG){#fig:013 width=70%} 


![Рис_14](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab02/report/image/Capture13.1.PNG){#fig:014 width=70%}

14. Заполните таблицу «Установленные права и разрешённые действия»
(см. табл. 2.1), выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-». </br>

| **Права директории** | **Права файла** | **Создание файла** | **Удаление файла** | **Запись в файл** | **Чтение файла** | **Смена директории** | **Просмотр файлов в директории** | **Переименование файла** | **Смена атрибутов файла** |
|----------------------|-----------------|--------------------|--------------------|-------------------|------------------|----------------------|----------------------------------|--------------------------|---------------------------|
| **[000]**            | [000]           | -                  | -                  | -                 | -                | -                    | -                                | -                        | -                         |
| **[100]**            | [100]           | -                  | -                  | -                 | -                | +                    | -                                | -                        | +                         |
| **[200]**            | [200]           | +                  | +                  | +                 | -                | -                    | -                                | +                        | -                         |
| **[300]**            | [300]           | +                  | +                  | +                 | +                | +                    | -                                | +                        | +                         |
| **[400]**            | [400]           | -                  | -                  | -                 | +                | -                    | -                                | +                        | -                         |
| **[500]**            | [500]           | -                  | -                  | -                 | +                | +                    | +                                | -                        | +                         |
| **[600]**            | [600]           | -                  | -                  | -                 | +                | -                    | +                                | +                        | -                         |
| **[700]**            | [700]           | +                  | +                  | +                 | +                | +                    | +                                | +                        | +                         |


15. На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения операций внутри директории
dir1, заполните табл. 2.2. </br>

| **Операция**               | **Мин. права на директ.** | **Мин. права на файл** |
|----------------------------|---------------------------|------------------------|
| **Создание файла**         | 200                       | 200                    |
| **Удаление файла**         | 300                       | 300                    |
| **Чтение файла**          | 200                       | 200                    |
| **Запись в файл**          | 500                       | 500                    |
| **Переименование файла**   | 100                       | 100                    |
| **Создание поддиректории** | 400                       | 400                    |
| **Удаление поддиректории** | 200                       | 200                    |


# Выводы

Получил практические навыки работы в консоли с атрибутами файлов, закрепил теоретические основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux