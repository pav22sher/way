### Основные понятия

>Java - кроссплатформенный, объектно-ориентированный язык со строгой типизацией.

>Java Core - это фундаментальные концепции языка программирования Java
>для разработки общих приложений (Java SE(Standard Edition)).

>JVM (Java Virtual Machine) — виртуальная машина Java (интерпретирует байт-кода в
>машинный код и исполняет его).

>JRE (Java Runtime Environment) — среда выполнения Java(JVM+библиотеки).
>JRE - предназначена только для запуска программы.

>JDK (Java Development Kit) — набор инструментов разработчика,
>необходимых для написания программ на Java.
>Включает в себя компилятор, JRE, набор стандартных библиотек Java,
>документацию, различные утилиты.
>JDK - предназначена для разработки, компиляции и запуска программы.

>JRE = JVM + библиотеки для запуска приложения Java.

>JDK = JRE + инструменты для разработки приложений Java. 

>Just-In-Time компиляция - если в программе присутствуют части кода,
>которые выполняются много раз,
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

>Javadoc — это инструмент, который поставляется с JDK и используется для создания 
>документации кода Java в формате HTML из исходного кода Java.

[Первый источник знаний](https://howtodoinjava.com/java/basics/jdk-jre-jvm/)

[Второй источник знаний](http://proglang.su/java/documentation)