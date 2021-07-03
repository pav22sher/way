###Дженерики (обобщения)

####Основы

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


####Wildcards


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
public class Stack {
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


[Основная информация](https://coderlessons.com/articles/java/kratkoe-rukovodstvo-po-java-generics)
[Стирание типов](https://javascopes.com/java-type-erasure-febcf174/)
[Методы мосты](http://www.linkex.ru/java/methods-bridges.php)