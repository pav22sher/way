###Дженерики (обобщения)

####Основы

>Дженерики (обобщения) — это особые средства языка Java для реализации 
>обобщённого программирования: особого подхода к описанию данных и алгоритмов, 
>позволяющего работать с различными типами данных без изменения их описания.

Примеры:
в классе
```java
class Cup<T>{
    private T content;
}
```
в интерфейсе
```java
public interface Comparable<T> {
    public int compareTo(T o);
}
```
в конструкторе
```java
class StringWrapper{
    private String stringValue;
    <T>StringWrapper(T value){
        this.stringValue = value.toString();
    }
}
```
в методе
```java
class Printer {
    public <T> void print(T[] items) {
        for (T item : items) {
            System.out.println(item);
        }
    }
}
```
с несколькими параметрами
```java
public class Pair<K,V> {
    private K key;
    private V value;
}
```

####Ограничения
Ограничение параметра одним классом:
```java
public class NumberContainer<T extends Number>{}
```
Ограничение параметра может быть несколькими интерфейсами, но только один классом:
```java
public class NumberContainer<T extends Number&Serializable&Cloneable>{}
```

####Wildcards
>Wildcards обозначаются знаком вопроса <?>.
```java
public class Main{
  public static void main(String[] args) {
    printList(new ArrayList<Integer>());
    printList(new ArrayList<String>());
  }
  //вывод списка любых объектов
  static void printList(List<?> list) {
    for (var val : list) { 
        System.out.println(val);
    }
  }
}
```
Ограничения Wildcards:
Upper Bounded Wildcards - <? extends T> -
может принимать на вход объекты класса T и любого другого дочернего класса.
Lower Bounded Wildcards - <? super T> - 
может принимать на вход объекты класса T и любого другого родительского класса.
```java
public class Main{
  public static void main(String[] args) {
    List<? extends Number> numList = new ArrayList<Integer>();
    List<? super Integer> numberList = new ArrayList<Number>();
  }
}
```

####Стирание типов
>Стирание типов (type erasure) - процесс удаления из байт-кода класс-файла информацию 
>о типах-дженериках.

Стирание состоит из трех действий:
* Если параметры ограничены (bounded), вместо типа-параметра в местах использования 
  подставляется верхняя граница, иначе Object;
* В местах присвоения значения типа-параметра в переменную обычного типа 
  добавляется каст к этому типу;
* Генерируются bridge-методы.

Примеры:

```java
public class Stack<E> {
    private E[] stackContent;

    public Stack(int capacity) {
        this.stackContent = (E[]) new Object[capacity];
    }

    public void push(E data) {
        // ...
    }

    public E pop() {
        // ...
    }
}
//преобразуется
public class Stack {
    private Object[] stackContent;

    public Stack(int capacity) {
        this.stackContent = (Object[]) new Object[capacity];
    }

    public void push(Object data) {
        // ...
    }

    public Object pop() {
        // ...
    }
}
```

####Мостовой метод
>Мостовые методы решают проблему переопределения методов в параметризованных классах.

Примеры:
```java
public class MyComparator implements Comparator<Integer> {
   public int compare(Integer a, Integer b) {
      //какая-то логика
   }
}
//преобразуется
public class MyComparator implements Comparator<Integer> {
    public int compare(Integer a, Integer b) {
        //какая-то логика
    }

    //это и есть мостовой метод("bridge method")
    public int compare(Object a, Object b) {
        return compare((Integer)a, (Integer)b);
    }
}
```

[Основная информация 1](http://www.quizful.net/post/java-generics-tutorial)

[Основная информация 2](https://annimon.com/article/2637)

[Основная информация 3](https://coderlessons.com/articles/java/kratkoe-rukovodstvo-po-java-generics)

[Стирание типов](https://javascopes.com/java-type-erasure-febcf174/)

[Методы мосты](http://www.linkex.ru/java/methods-bridges.php)

