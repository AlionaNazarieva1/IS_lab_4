---
# Front matter
lang: ru-RU
title: "Oтчёт по лабораторной работе"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
author: "Назарьева Алена Игоревна НФИбд-03-18"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с расширенными атрибутами файлов

# Выполнение лабораторной работы

1. От имени пользователя guest определила расширенные атрибуты файла
/home/guest/dir1/file1 командой
lsattr /home/guest/dir1/file1
2. Установила командой chmod 600 file1 на файл file1 права,
разрешающие чтение и запись для владельца файла.
3. Попробовала установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
chattr +a /home/guest/dir1/file1
В ответ получила отказ от выполнения операции. (рис. -@fig:001)

![пункты 1-3](1.jpg){ #fig:001 width=70% }

4. Повысила свои права с помощью команды su. Попробовала установить расширенный атрибут a на файл
/home/guest/dir1/file1 от имени суперпользователя:
chattr +a /home/guest/dir1/file1 (рис. -@fig:002)

![пункты 4](2.jpg){ #fig:002 width=70% }

5. От пользователя guest проверила правильность установления атрибута:
lsattr /home/guest/dir1/file1 (рис. -@fig:008)

![пункты 5](8.jpg){ #fig:008 width=70% }

6. Выполнила дозапись в файл file1 слова «test» командой
echo "test" /home/guest/dir1/file1
После этого выполнила чтение файла file1 командой
cat /home/guest/dir1/file1
Убедилась, что слово test было успешно записано в file1.
7. Попробовала удалить файл file1 и стереть имеющуюся в нём информацию командой
echo "abcd" > /home/guest/dirl/file1
Попробовала переименовать файл. (рис. -@fig:004)

![пункты 6-7](4.jpg){ #fig:004 width=70% }

8. Попробовала с помощью команды
chmod 000 file1
установить на файл file1 права, запрещающие чтение и запись для владельца файла. (рис. -@fig:009)

![пункты 8](9.jpg){ #fig:009 width=70% }

9. Сняла расширенный атрибут a с файла /home/guest/dirl/file1 от
имени суперпользователя командой
chattr -a /home/guest/dir1/file1
Повторила операции, которые ранее не удавалось выполнить.
для chmod 600: (рис. -@fig:010)

![пункт 9-600](10.jpg){ #fig:010 width=70% }

(рис. -@fig:011)

![пункт 9-000](11.jpg){ #fig:011 width=70% }

10. Повторила ваши действия по шагам, заменив атрибут «a» атрибутом «i».(рис. -@fig:005)

![пункт 10](5.jpg){ #fig:005 width=70% }

(рис. -@fig:006)

![пункт 10-000](6.jpg){ #fig:006 width=70% }

(рис. -@fig:007)

![пункт 10-600](7.jpg){ #fig:007 width=70% }


Мои наблюдения:
Если установлен атрибут "a", файл может быть открыт для записи только в режиме добавления текста.
Если установлен атрибут "i", файл нельзя модифицировать. Это значит нельзя переименовывать, создавать символьные ссылки, исполнять и записывать, снять этот втрибут может только суперпользователь.

# Выводы

В результате выполнения работы я повысила свои навыки использования интерфейса командой строки (CLI), познакомилась на примерах с тем, как используются основные и расширенные атрибуты при разграничении
доступа. Имела возможность связать теорию дискреционного разделения доступа (дискреционная политика безопасности)
с её реализацией на практике в ОС Linux. Составила наглядные таблицы, поясняющие какие операции
возможны при тех или иных установленных правах. Опробовала действие на практике раёсширенных атрибутов «а» и «i».
