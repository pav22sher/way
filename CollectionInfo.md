##Коллекции

> Коллекции - контейнеры с определенной структурой
> для хранения набора объектов.

###Класс Collections

> Collections - состоит из статических методов, которые реализуют различные алгоритмы
> для работы с коллекциями.

Методы класса Collections:
* Collections.sort - сортировка
* Collections.binarySearch - бинарный поиск
* Collections.reverse - изменяет порядок элементов в указанном списке
* Collections.shuffle - перемешать в случайном порядке
* Collections.swap - поменять местами два элемента
* Collections.fill - заполнить всю коллекцию одним элементом
* Collections.copy - скопировать содержимое из одной коллекции в другую
* Collections.addAll - добавить элементы
* Collections.replaceAll - заменить один элемент другим
* Collections.max - максимальный элемент
* Collections.min - минимальный элемент
* Collections.disjoint - проверка на общие элементы в двух коллекциях
* Collections.frequency - поиск кол-ва определенных объектов

Пример:
```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>(List.of(3,2,1)); //создаем список
        Collections.sort(list); //сортируем список
        list.forEach(System.out::println); //вывод списка в консоль
        System.out.println(Collections.min(list));//поиск минимума
        System.out.println(Collections.max(list));//поиск максимума
        System.out.println(Collections.frequency(list,1));//кол-во элемента 1 в списке
    }
}
```

###Comparator

>Класс Comparator - предоставляет метод compare() для сравнения объектов и
>дает возможность сравнения по нескольким признакам.

Пример:
```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Message> messages = new ArrayList<>(List.of(
                new Message(1, "Pavel","Hello"), 
                new Message(2, "Vlad","World"))
        );
        Comparator<Message> comparator1 = (o1, o2) -> o1.getId().compareTo(o2.getId());
        messages.sort(comparator1);
        messages.forEach(System.out::println);
        Comparator<Message> comparator2 = (o1, o2) -> o1.getFrom().compareTo(o2.getFrom());
        messages.sort(comparator2);
        messages.forEach(System.out::println);
        Comparator<Message> comparator3 = Comparator.comparing(Message::getMessage);
        messages.sort(comparator3);
        messages.forEach(System.out::println);
    }

    @Data
    @AllArgsConstructor
    public static class Message {
        private Integer id;
        private String from;
        private String message;
    }
}
```

###Comparable
> Интерфейс Comparable - предоставляет метод compareTo() для сравнения объектов и
> возможность сравнения по одному признаку.

```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Message> messages = new ArrayList<>(List.of(
                new Message(1, "Pavel","Hello"),
                new Message(2, "Vlad","World"))
        );
        Collections.sort(messages);
        messages.forEach(System.out::println);
    }

    @Data
    @AllArgsConstructor
    public static class Message implements Comparable<Message>{
        private Integer id;
        private String from;
        private String message;

        @Override
        public int compareTo(Message o) {
            return this.getId().compareTo(o.getId());
        }
    }
}
```

###Iterator

Интерфейс Iterator - методы для перемещения по списку элементов.

Методы Iterator:
* hasNext - проверяет есть ли следующий элемент
* next - получить следующий элемент
* remove - удаляет текущий элемент

Методы ListIterator:
* hasPrevious - проверяет предыдущий элемент
* previous - получить предыдущий элемент
* previousIndex - возвращает индекс предыдущего элемента
* nextIndex - возвращает индекс следующего элемента
* set - заменяет текущий элемент
* add - вставляет элемент после текущего

###Collection

> Интерфейс Collection - содержит базовые методы, которыми обладает каждая коллекция

Методы Collection:
* size - возвращает кол-во элементов
* isEmpty - проверка на пустоту коллекции
* contains - проверка на то, что элемент есть в коллекции
* containsAll - проверка на то, что элементы есть в коллекции
* add - добавление элемента в коллекцию
* addAll - добавить элементы в коллекцию
* remove - удаление элемента из коллекции
* removeAll - удалить элементы из коллекции
* removeIf - удалить элементы, которые удовлетворяют условию
* retainAll - удалить все элементы, которых нет в другой коллекции
* clear - удалить все элементы из коллекции
* toArray - преобразует коллекцию в массив
* stream - создать поток данных из коллекции
* parallelStream - создать параллельный поток данных из коллекции

###Списки

> Интерфейс List - упорядоченный список объектов, объекты хранятся в порядке их добавления в список, 
> объекты проиндексированы и работа с элементами может вестись через его индекс, можно хранить null. 

Реализации интерфейса List:

> Класс Vector - синхронизованный динамический массив.

> Класс ArrayList - динамический массив.

> Класс LinkedList - двусвязный список (хранит ссылку на первый и последний элементы).

###Множества

> Интерфейс Set - множество неповторяющихся объектов, можно хранить только один null объект,
> внутри используется объект Map: в качестве ключа используется добавляемый элемент,
> а в качестве значения — объект-пустышка (new Object()).

Реализации Set:

> HashSet - внутри для хранения данных используется объект HashMap,
> элементы хранятся не упорядочено.

> LinkedHashSet - внутри для хранения данных используется объект LinkedHashMap,
> элементы хранятся в порядке добавления.

> TreeSet - внутри для хранения данных используется объект TreeMap,
> упорядоченное с использованием натурального порядка ("natural ordering")
> или с использованием Comparator.

###Очереди

> Интерфейс Queue - обычная очередь (FIFO — First In First Out — если первым пришел, то первым и уйдешь).

> Интерфейс Deque - двунаправленная очередь.

###Карты

> Название Map появилось как сокращение слова mapping,
> что значит отображение, соответствие.

> Интерфейс Map - карты/словари, хранение данных в виде пары ключ-значение,
> ключи и значения являются объектами, ключи должны быть уникальными,
> а значения могут быть дублированными.

Реализации Map:

> Hashtable - синхронизованная хэш-таблица, почти все методы помечены как synchronized,
> коллекция не является упорядоченной, ключ и значение НЕ мб null.

> HashMap - не синхронизованная хэш-таблица, коллекция не является упорядоченной,
> ключ и значение мб null.

> LinkedHashMap - упорядоченная по добавлению хэш-таблица.

> TreeMap - хранение в виде красно-чёрного дерева,
> упорядочен с использованием натурального порядка ("natural ordering")
> или с использованием Comparator.

> WeakHashMap - хэш-таблица, которая организована с использованием слабых ссылок (weak references),
> Garbage Collector автоматически удалит элемент из коллекции при следующей сборке мусора, 
> если на ключ этого элемента нет жёстких ссылок.

###Дополнительная информация

> Вложенный класс - это не статический класс, который объявлен внутри объявления другого класса.

Типы внутренних классов:
* локальные классы (local classes) - класс определен и виден в блоке кода, например, в методе
* анонимные классы (anonymous classes) - локальный класс без имени
* внутренние классы-члены (member inner classes) - класс ассоциируется не с внешним классом, 
  а с его экземпляром

> Map.Entry<K, V> - вложенный статический класс. В Map метод entrySet() возвращает Set всей карты 
> в виде Map.Entry<K, V>(пара ключ-значение(K-V)).

> Immutable(неизменяемый) класс — это класс, который после инициализации не может изменить свое состояние.
> То есть если в коде есть ссылка на экземпляр иммутабельного класса,
> то любые изменения в нем приводят к созданию нового экземпляра (Пример: класс String).

> Если в классе ключа переопределены методы equals и hashCode
> и они зависят от состояния объекта(полей объекта),
> то при изменении состояния объекта можно потерять значение лежащее в Map.
> Лучшим кандидатом для ключа мб класс String, который кэширует хэш-код.

Сторонние библиотеки для работы с коллекциями:
* Apache Common Collections
* Google Guava
