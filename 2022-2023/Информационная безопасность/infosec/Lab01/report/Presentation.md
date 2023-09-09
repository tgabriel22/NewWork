---
## Front matter
lang: ru-RU
title: Информационная безопасность
subtitle: Презентация к лабораторной работе №_01
author:
  - Габриэль Тьерри
institute:
  - Российский университет дружбы народов имени Патриса Лумумбы, Москва, Россия
  - Факультет физико-математических и естественных наук, Москва, Россия
date: 09 сентября 2023

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

## Цель

- Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

## задачи

- Лабораторная работа подразумевает установку на виртуальную машину VirtualBoх операционной системы Linux (дистрибутив Rocky или CentOS)
- Изучить идеологию и применение средств контроля версий.
- Освоить умения по работе с git.
- Научиться оформлять отчёты с помощью легковесного языка разметки Markdo

# Выполнение лабораторной работы

1. Создаем  виртуальную машину. Операционная система Rocky 9, RAM 2048 МБ, Жесткий диск 40 Гб, Тип Linux версия Red Hat
![Краткий обзор конфигурации виртуальной машины](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture1.PNG){#fig:000 width=70%}

![Краткий обзор конфигурации виртуальной машины](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture2.PNG){#fig:001 width=70%}

![Начало установки](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture3.PNG){#fig:002 width=70%}

2. Получим следующую информацию с помощью команды "dmesg | grep -i"

![Версия ядра Linux](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture5.PNG){#fig:003 width=70%}

![Модель процессора](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture7.PNG){#fig:004 width=70%}

![Тип файловой системы корневого раздела](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture8.PNG){#fig:005 width=70%}

![Объем доступной оперативной памяти _ Частота процессора _ Тип обнаруженного гипервизора](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/Capture9.PNG){#fig:006 width=70%}

3. Создали репозиторий курса на github

![репозиторий курса](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab01/report/image/github.PNG){#fig:007 width=70%}

## Вывод:
- Для лабораторных работ я установил операционную систему Linux Rocky с помощью VirtualBox, изучил идеологию и применение средств контроля версий, овладел навыками работы с git, научился проектировать отчеты с использованием облегченного языка разметки Markdonw