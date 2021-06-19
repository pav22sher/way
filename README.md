## Тяжелый путь программиста!
![start](https://www.sb.by/upload/iblock/0e3/0e3befde3b6b9a77004fb61175a120a4.jpg)

## План
![coding](https://ug.ru/wp-content/uploads/2020/05/programmirovanie.jpg)

---
[Аперитив](#aperitif)
* [Стиль кода](StyleInfo.md)
* [Методы класса Object](ObjectInfo.md)
* [ООП](OOPInfo.md)
---
[Завтрак](#breakfast)
* Библиотеки
* Generics
* Java Collections Framework
* Lambda
* Stream API
* Multithreading
* Input/Output
---
[Обед](#dinner)
* паттерны проектирования
* spring
* hibernate
* sql
---
[Ужин](#supper)
* html
* css
* js
---
[Перекус](#snack)
* intellij idea
* maven
* git
* Chrome DevTools
* linux


---
<p id="aperitif">Аперитив:<p/>
<b>Java</b> — 
<abbr title="на ней можно разрабатывать десктопные приложения, приложения под Android, заниматься веб-разработкой…">мультифункциональный</abbr>,
<abbr title="программа может работать на любой платформе">кроссплатформенный</abbr>,
<abbr title="в нем существуют классы и объекты. Классы — это типы данных, а объекты — представители классов.">объектно-ориентированный язык</abbr>,
<abbr title="не допускается смешивание в выражениях разных типов и автоматическое выполнение неявных преобразований.">со строгой типизацией</abbr>.

>Core Java - это категория Java, которая охватывает фундаментальные концепции 
>языка программирования Java для разработки общих приложений (Java SE(Standard Edition)).

>JVM (Java Virtual Machine) — виртуальная машина Java. Это программный модуль, 
>зависящий от платформы, который служит для интерпретации исходного байт-кода в 
>машинный код и его исполнения.

>JRE (Java Runtime Environment) — среда выполнения Java. 
>Включает в себя реализацию JVM для конкретной платформы 
>и набор библиотек, необходимых для выполнения программ на Java.
>JRE - предназначена только для запуска программы(обычный пользователь).

>JDK (Java Development Kit) — набор инструментов разработчика,
>необходимых для написания программ на Java.
>Включает в себя компилятор, JRE, набор стандартных библиотек Java,
>документацию, различные утилиты.
>JDK - предназначена для разработки, компиляции и запуска программы(программист).

>Простыми словами, механизм Just-In-Time компиляции заключается в следующем:
>если в программе присутствуют части кода, которые выполняются много раз,
>то их можно скомпилировать один раз в машинный код,
>чтобы в будущем ускорить их выполнение. После компиляции такой части программы
>в машинный код, при каждом следующем вызове этой части программы
>виртуальная машина будет сразу выполнять скомпилированный машинный код,
>а не интерпретировать его, что естественно ускорит выполнение программы.

>Garbage Collector (Сборщик мусора) — во время работы программы
>периодически в фоновом режиме очищает память от ненужных объектов,
>которые прекратили свою работу. То есть JVM проверяет, существует ли
>ссылка на тот или иной объект. Если ДА, то объект считается работающим. 
>Если НЕТ, то Сборщик мусора помечает объект на удаление.
>Периодичность запуска Сборщик мусора неизвестна, 
>т.к.JVM сама знает, когда включить его в работу!

>Исходный код — текстовый файл на языке Java, имеющий расширение .java

>Байт-код — машинно-независимый низкоуровневый код, 
>представляющий собой набор инструкций для JVM.
>Хранится в файле с расширением .class.

>Машинный код — набор машинных инструкций в двоичном формате,
>которые непосредственно выполняются процессором.

>Компиляция — преобразование исходного кода в байт-код.

>Интерпретация — преобразование байт-кода в машинный код.

>Платформа — программно-аппаратная среда, 
>в которой происходит выполнение программ и приложений. 
>Наиболее популярными платформами являются Microsoft Windows, Linux и Mac OS.

---
<p id="breakfast">Завтрак:<p/>

>Обобщения(Generic) - это параметризованные типы. С их помощью можно объявлять классы, 
>интерфейсы и методы, где тип данных указан в виде параметра.

>Обобщённое программирование — это такой подход к описанию данных и алгоритмов,
>который позволяет их использовать с различными типами данных без изменения их описания.

>Для хранения наборов данных в Java предназначены массивы. Однако их не всегда удобно 
>использовать, прежде всего потому, что они имеют фиксированную длину. 
>Эту проблему в Java решают коллекции. Однако суть не только в гибких по размеру 
>наборах объектов, но в и том, что классы коллекций реализуют различные структуры данных,
>(стек, очередь, дерево и т.д.).

>Stream API - упрощает работу с наборами данных, в частности, 
>упростить операции фильтрации, сортировки и другие манипуляции с данными.

>Многопоточные приложения — это приложения, где параллельно выполняются 
>два или более потоков. 

>Поток — определенный способ выполнения процесса. Когда один поток изменяет 
>ресурс процесса, это изменение сразу же становится видно другим потокам этого процесса.

>Процесс — экземпляр программы во время выполнения, независимый объект, 
>которому выделены системные ресурсы (например, процессорное время и память). 
>Каждый процесс выполняется в отдельном адресном пространстве: 
>один процесс не может получить доступ к переменным и структурам данных другого.
 
>Что бы программы ни делали, рано или поздно у большинства из них возникает задача 
>сохранить результаты своей деятельности в какое-то хранилище. 
>Часта в роли такого хранилища выступает файловая система.

---
<p id="dinner">Обед:<p/>

>Паттерн(шаблоны) проектирования — это руководства по решению повторяющихся проблем. 
>Это не классы, пакеты или библиотеки, которые можно было бы подключить 
>к вашему приложению и сидеть в ожидании чуда. Они скорее являются методиками,
>как решать определенные проблемы в определенных ситуациях.

>Spring Framework, или просто Spring — комплексный фреймворк
>для создания веб-приложений на Java.

>Spring — это не один какой-то конкретный фреймворк.
>Это скорее общее названия для целого ряда 
>небольших фреймворков, каждый из которых выполняет какую-то свою работу
>(Spring MVC, Spring Data и т.д.).

>Spring Boot — комплексный фреймворк для создания и запуска приложений 
>с минимальными усилиями и настройками.

>ORM(Object-relational mapping) — это отображение объектов какого-либо 
>объектно-ориентированного языка в структуры реляционных баз данных.

>JPA(Java Persistence API) это спецификация Java EE и Java SE, 
>описывающая систему управления сохранением java объектов 
>в таблицы реляционных баз данных.

>Hibernate - реализация спецификации JPA, ORM-решение для языка Java. 

>Реляционная база данных(РБД) — это совокупность связанных между собой 
>двумерных таблиц, в которых хранится информация об объектах. 
>Запись (строка) включает в себя данные об одном объекте, 
>а в полях (столбцах) содержатся различные его характеристики.

>SQL(structured query language — «язык структурированных запросов») — 
>декларативный язык программирования, применяемый для создания, 
>модификации и управления данными в реляционной базе данных.

---
<p id="supper">Ужин:<p/>

>HTML(HyperText Markup Language-язык гипертекстовой разметки)-это язык разметки
>документов во Всемирной паутине (World Wide Web, WWW), позволяющий составлять
>форматированный текст. Браузер интерпретирует его и отображает на экране 
>элементы веб-страниц.
 
>HTML — это контент и теги. Теги позволяют задать способ отображения контента 
>на веб-страницах.
 
>CSS (Cascading Style Sheets-каскадные таблицы стилей) — это язык описания 
>внешнего вида документа (веб-страницы), написанного с использованием языка 
>разметки(HTML).

>JavaScript — мультипарадигменный язык программирования. 
>Поддерживает объектно-ориентированный, императивный и функциональный стили.
>В основном клиентская часть любых веб-приложений(функционал веб-страницы)
>-это JavaScript.

---
<p id="snack">Перекус:<p/>

>Intellij Idea-инструмент для разработки и не только.

>Maven — инструмент для автоматизации сборки проектов и не только.

>Git - это система контроля версий.

>GitHub — крупнейший веб-сервис для хостинга IT-проектов и их совместной разработки.

>Chrome DevTools — набор инструментов для веб-разработчика, 
>встроенный в браузер Google Chrome.

>Linux — это операционная система. Как windows, только более защищенная. 
>В windows легко подхватить вирус, в линуксе это практически невозможно. 
>А еще линукс бесплатный, и ты сам себе хозяин: 
>никаких тебе неотключаемых автообновлений системы!
>Правда, разобраться в нем немного посложнее… 
>Потому что большинство операций выполняется в командной строке.

---
[Цитата про программирование (если станет скучно)](StyleInfo.md)