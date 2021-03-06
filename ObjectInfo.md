###Методы класса Object

###Небольшое отступление

>Все классы являются потомками класса Object!

>Ключевое слово native в методах применяется, чтобы указать, 
>что метод реализован не в файле Java, 
>а на другом языке программирования.

>Для метода final означает, что он не может быть переопределен в подклассах. 
>Это полезно, когда мы хотим, чтобы исходную реализацию нельзя было переопределить.

####Методы на каждый день

* public String toString()

>Этот метод позволяет получить текстовое описание любого объекта.
>Этот метод возвращает строковое представление объекта.

>Для чего? -Выводить информацию в консоль! 

* protected native Object clone()

>Метод позволяет клонировать объект: создает дубликат объекта.

>Для чего? -Чтобы создать копию объекта, а не копию ссылки на объект.

* protected void finalize()

>Этот метод вызывается Java-машиной у объекта перед тем, 
>как объект будет уничтожен. Фактически этот метод – 
>противоположность конструктору. 

>Для чего? -В нем можно освобождать ресурсы, используемые объектом.

####Сравнение объектов

* public boolean equals(Object obj)

>Метод для сравнения объектов.

>Для чего? Потому что “==” сравнивает ссылки, а не объекты! 

* public native int hashCode()

>Метод возвращает числовое значение(хэш-код), которое будет соответствовать данному объекту.

>Методом hashCode()(Хэш-функция), возвращает числовое значение фиксированной длины для любого объекта.
>В случае с Java метод hashCode() возвращает для любого объекта 32-битное число типа int.

>Для чего? Для более быстрого сравнения объектов, чем методом equals().

>Если в программе будет нужно сравнивать объекты, гораздо проще сделать это по хэш-коду, 
>и только если они равны по hashCode() — переходить к сравнению по equals().

####Рефлексия

* public final native Class getClass()

>Возвращает специальный объект, который описывает текущий класс.

>Для чего? -Рефлексия в Java — это специальное API из стандартной 
>библиотеки, которая позволяет получить доступ к информации 
>о программе во время выполнения.
>С помощью этой информации можно изменить 
>поведение программы динамически во время выполнения!

####Методы для многопоточных приложений

>Иногда при взаимодействии потоков встает вопрос о извещении одних потоков 
>о действиях других. Например, действия одного потока зависят от результата 
>действий другого потока, и надо как-то известить один поток, 
>что второй поток произвел некую работу.

>Все эти методы вызываются только из синхронизированного контекста - 
>синхронизированного блока или метода. 


* public final void wait()

>wait - методы для приостановки потока.

* public final native void wait(long timeout)

>wait - методы для приостановки потока на время timeout.

* public final void wait(long timeout, int nanos)

>wait - методы для приостановки потока на время timeout и nanos.
  
* public final native void notify()

>notify - методы для возобновления одного потока.

* public final native void notifyAll()

>notifyAll - методы для возобновления всех потоков.



