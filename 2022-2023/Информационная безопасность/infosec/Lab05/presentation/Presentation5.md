---
## Front matter
lang: ru-RU
title: Информационная безопасность
subtitle: Презентация к лабораторной работе №_05
author:
  - Габриэль Тьерри
institute:
  - Российский университет дружбы народов имени Патриса Лумумбы, Москва, Россия
  - Факультет физико-математических и естественных наук, Москва, Россия
date: 07/10/2023

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Габриэль Тьерри
  * Студент НКНбд 01-20
  * Факультет физико-математических и естественных наук
  * Российский университет дружбы народов имени Патриса Лумумбы 
  * <https://github.com/tgabriel22>
  * [1032204249@pfur.ru](mailto:1032204249@pfur.ru)

:::
::: {.column width="30%"}

:::
::::::::::::::

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

5. От пользователя guest2 попробовал дозаписать в файл /tmp/file01.txt слово test2 командой echo "test2" > /tmp/file01.txt Удалось ли вам выполнить операцию? нет, не удалось.

![изображение 013](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab05/report/image/Capture13.PNG){#fig:012 width=70%}

6. Проверил содержимое файла командой cat /tmp/file01.txt

7. От пользователя guest2 попробовал записать в файл /tmp/file01.txt слово test3, стерев при этом всю имеющуюся в файле информацию командой
echo "test3" > /tmp/file01.txt Удалось ли вам выполнить операцию? да, удалось.

8. Проверил содержимое файла командой cat /tmp/file01.txt

9. От пользователя guest2 попробовал удалить файл /tmp/file01.txt командой rm /tmp/fileOl.txt
Удалось ли вам удалить файл? да, удалось.

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