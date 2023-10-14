---
## Front matter
lang: ru-RU
title: Информационная безопасность
subtitle: Презентация к лабораторной работе №_06
author:
  - Габриэль Тьерри
institute:
  - Российский университет дружбы народов имени Патриса Лумумбы, Москва, Россия
  - Факультет физико-математических и естественных наук, Москва, Россия
date: 14/10/2023

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

- Развить навыки администрирования ОС Linux. Получить первое практическое знакомство с технологией SELinux1
- Проверить работу SELinx на практике совместно с веб-сервером Apache.

# Выполнение лабораторной работы

1.Вошел в систему под своей учетной записью и убедился, что SELinux работает в режиме enforcing политики targeted с помощью команд getenforce и sestatus

![изображение 001](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture1.PNG){#fig:001 width=70%}

2. Обратился с помощью браузера к веб-серверу, запущенному на моем компьютере, и убедился, что последний работает с помощью команды service httpd status

![изображение 002](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture2.PNG){#fig:002 width=70%}


3. Определил контекст безопасности веб-сервера Apache - httpd_t  С помощью команды ps auxZ | grep httpd

![изображение 003](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture3.PNG){#fig:003 width=70%}

4. Посмотрел текущее состояние переключателей SELinux для Apache с помощью команды sestatus -bigrep httpd, многие из переключателей находятся в положении off

![изображение 004](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture4.PNG){#fig:004 width=70%}

5. Посмотрел статистику по политике с помощью команды seinfo, также определите множество пользователей, ролей, типов.
6. Посмотрел тип файлов и поддиректорий, находящихся в директории /var/www, с помощью команды ls -lZ /var/www
7. Определил тип файлов, находящихся в директории /var/www/html:
ls -lZ /var/www/html
8. Определил круг пользователей, которым разрешено создание файлов в
директории /var/www/html.

![изображение 005](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture6.PNG){#fig:005 width=70%}


9. создал от имени суперпользователя (так как в дистрибутиве после установки только ему разрешена запись в директорию) html-файл
/var/www/html/test.html следующего содержания:
<html>
<body>test</body>
</html>

![изображение 006](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture7.PNG){#fig:006 width=70%}

10. Проверил контекст созданного вами файла. 
11. Обратился к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html. убедился, что файл был успешно отображён.

![изображение 007](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture8.PNG){#fig:007 width=70%}

12. Изучил справку man httpd_selinux и выясните, какие контексты файлов определены для httpd. Сопоставил их с типом файла test.html. Проверил контекст файла можно командой ls -Z. ls -Z /var/www/html/test.html
13. Изменил контекст файла /var/www/html/test.html с httpd_sys_content_t на любой другой, к которому процесс httpd не должен иметь доступа, например, на samba_share_t:
chcon -t samba_share_t /var/www/html/test.html
ls -Z /var/www/html/test.html
После этого проверил, что контекст поменялся.

![изображение 008](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture9.PNG){#fig:008 width=70%}

14. Попробовал ещё раз получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html.и  получил сообщение об ошибке: Forbidden
You don't have permission to access /test.html on this server.

![изображение 009](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture10.PNG){#fig:009 width=70%}

15. Проанализовал ситуацию. 
Просмотрил log-файлы веб-сервера Apache. Также просмотрите системный лог-файл: tail /var/log/messages

16. Попробовал запустить веб-сервер Apache на прослушивание ТСР-порта 81 (а не 80, как рекомендует IANA и прописано в /etc/services). Для этого в файле /etc/httpd/httpd.conf найдите строчку Listen 80 и замените её на Listen 81.

![изображение 010](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture11.PNG){#fig:010 width=70%}

![изображение 011](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture12.PNG){#fig:011 width=70%}

17. Выполнил перезапуск веб-сервера Apache. Произошёл сбой? Поясните почему?
18. Проанализовал лог-файлы: tail -nl /var/log/messages
Просмотрил файлы /var/log/http/error_log, /var/log/http/access_log и /var/log/audit/audit.log и выясните, в каких файлах появились записи.

![изображение 012](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture13.PNG){#fig:012 width=70%}

19. Выполнил команду
semanage port -a -t http_port_t -р tcp 81
После этого проверьте список портов командой
semanage port -l | grep http_port_t
убедился, что порт 81 появился в списке.

![изображение 013](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture14.PNG){#fig:013 width=70%}

20. Попробовал запустить веб-сервер Apache ещё раз. Поняли ли вы, почему
он сейчас запустился, а в предыдущем случае не смог?
21. Вернул контекст httpd_sys_cоntent__t к файлу /var/www/html/ test.html:
chcon -t httpd_sys_content_t /var/www/html/test.html
После этого Попробовал получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1:81/test.html.
и увидел содержимое файла — слово «test».

![изображение 014](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture15.PNG){#fig:014 width=70%}

22. Исправил обратно конфигурационный файл apache, вернув Listen 80.

![изображение 015](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture16.PNG){#fig:015 width=70%}

23. Удалил привязку http_port_t к 81 порту:
semanage port -d -t http_port_t -p tcp 81
и проверил, что порт 81 удалён.
24. Удалил файл /var/www/html/test.html:
rm /var/www/html/test.html

![изображение 016](https://raw.githubusercontent.com/tgabriel22/Work/main/2022-2023/Информационная%20безопасность/infosec/Lab06/report/image/Capture17.PNG){#fig:016 width=70%}

# Выводы

- Развить навыки администрирования ОС Linux. Получить первое практическое знакомство с технологией SELinux1
- Проверить работу SELinx на практике совместно с веб-сервером Apache.