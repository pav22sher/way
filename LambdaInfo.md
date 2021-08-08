###Функциональные интерфейсы

> Функциональный интерфейс (functional interface) –
> это интерфейс у которого только один абстрактный метод.
> Статические методы и методы по умолчанию при этом не в счёт,
> их в функциональном интерфейсе может быть сколько угодно.

> Аннотация @FunctionalInterface - не обязательная аннотация,
> которая сообщает компилятору, что данный интерфейс функциональный
> и должен содержать не более одного метода.
> Если в интерфейсе с данной аннотацией более одного абстрактного метода,
> компилятор не пропустит данный интерфейс, так как будет воспринимать его как ошибочный код.

> Встроенные функциональные интерфейсы находятся в пакете java.util.function.

###Предикаты

> Predicate<T> - Функциональный интерфейс Predicate<T> {boolean test(T t);)}

> BiPredicate<T, U> - Функциональный интерфейс BiPredicate<T, U> {boolean test(T t, U u);)}

> Предикаты для примитивных типов данных: IntPredicate, LongPredicate, DoublePredicate

###Поставщики

> Supplier<T> - Функциональный интерфейс Supplier<T> {T get();}

> Поставщики для примитивных типов данных: BooleanSupplier, IntSupplier, LongSupplier, DoubleSupplier

###Потребители

> Consumer<T> - Функциональный интерфейс Consumer<T> {void accept(T t);}

> Потребители для примитивных типов данных: IntConsumer, LongConsumer, DoubleConsumer

> BiConsumer<T, U> - Функциональный интерфейс BiConsumer<T, U> {void accept(T t, U u);}

> Потребители с параметрами в виде объекта и примитивного типа данных: 
> ObjIntConsumer<T>,ObjLongConsumer<T>,ObjDoubleConsumer<T>.

###Функции

> Function<T,R> - Функциональный интерфейс Function<T, R> {R apply(T t);}

> Функции для примитивных типов данных: IntFunction<R>, LongFunction<R>, DoubleFunction<R>

> BiFunction<T, U, R> - Функциональный интерфейс BiFunction<T, U, R> {R apply(T t, U u);}

> IntToDoubleFunction,IntToLongFunction,
> LongToDoubleFunction,LongToIntFunction,
> DoubleToLongFunction,DoubleToIntFunction - 
> с аргументом функции примитивного типа
> и возвращаемым значением примитивного типа!

> ToIntFunction<T>,ToIntBiFunction<T, U>,
> ToLongFunction<T>,ToLongBiFunction<T, U>,
> ToDoubleFunction<T>,ToDoubleBiFunction<T, U> - 
> с аргументом функции в виде объекта
> и возвращаемым значением в виде примитивного типа!

###Унарные

> UnaryOperator - (UnaryOperator<T> extends Function<T, T>)
> единственный абстрактный метод T apply(T t).

> Унарные для примитивных типов: IntUnaryOperator, LongUnaryOperator, DoubleUnaryOperator

###Бинарные

> BinaryOperator (BinaryOperator<T> extends BiFunction<T,T,T>) -
> единственный абстрактный метод T apply(T t, T u);

> Бинарные для примитивных типов: IntBinaryOperator, LongBinaryOperator, DoubleBinaryOperator

###Примеры функциональных интерфейсов

Встроенные функциональные интерфейсы:
```java
@FunctionalInterface 
public interface Comparator<T> {
    int compare(T o1, T o2);
}
@FunctionalInterface public interface Runnable {
    void run();
}
```
Создание собственного функционального интерфейса:
```java
@FunctionalInterface public interface Converter<T, N> {
    N convert(T t);
}
```

###Лямбда-выражения

> Лямбда-выражение - это объект с одним методом, 
> который можно передавать в другие методы в качестве аргумента
> вместо функционального интерфейса.

> Лямбда-оператор - стрелка ->.

> Никогда не указывается тип результата лямбда-выражения, т.к. он выясняется из контекста. 

Пример:
```java
public class Main {
    public static void main(String[] args) {
        //Без лямбда-выражения и с анонимным классом
        Arrays.sort(new String[]{"Hello", "World", "Bay"}, new Comparator<>() {
            @Override
            public int compare(String o1, String o2) {
                return o1.length() - o2.length();
            }
        });
        //С лямбда-выражением
        Arrays.sort(new String[]{"Hello", "World", "Bay"}, (o1, o2) -> o1.length() - o2.length());
    }
}
```

###Типы лямбда-выражений

> Однострочные - НЕ должны иметь оператор return, если возвращают значение.

> Блочные (многострочные) - должны иметь оператор return, если возвращают значение.

Пример:
```java
public class Main {
    public static void main(String[] args) {
        Runnable helloWorld1 = () -> System.out.println("Hello world");
        Runnable helloWorld2 = () -> {
            String msg = "Hello world";
            System.out.println(msg);
        };
    }
}
```

###Параметры лямбда-выражений

> Можно указывать тип параметра для повышения читабельности кода,
> а можно не указывать, т.к. тип параметра метода можно выяснить из контекста.
 
> Круглые скобки можно убрать, если это один параметр без типа.

Пример:
```java
public class Main {
    public static void main(String[] args) {
        Consumer<String> printMsg0 = msg -> System.out.println(msg);
        Consumer<String> printMsg1 = (msg) -> System.out.println(msg);
        Consumer<String> printMsg2 = (String msg) -> System.out.println(msg);
    }
}
```

###Ссылка на метод

> Вместо функциональных интерфейсов можно использовать ссылки на метод, а не лямбда-выражения.

Пример:
```java
public class Main {
    public static void main(String[] args) {
        //x -> System.out.println(x)
        Consumer<String> consumer = System.out::println;
        //(x, y) -> Math.pow(x, y)
        BiFunction<Double, Double, Double> biFunction = Math::pow;
        //(x, y) -> x.compareToIgnoreCase(y)
        Comparator<String> comparator = String::compareToIgnoreCase;
    }
}
```
