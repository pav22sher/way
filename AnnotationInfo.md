###Аннотации

>Аннотации - описывают метаданные для функции/класса/пакета.

####Встроенные аннотации Java
* @Retention - в каком жизненном цикле кода аннотация будет доступна 
  (в исходнике, в class-файле или во время выполнения).
* @Target - для какого элемента ее можно использовать (поле, класс, пакет и тд).
* @Override - говорит о том, что родительский метод переопределён в наследнике.
* @Deprecated - помечаются элементы языка, которые больше не рекомендуется использовать, 
  так как они заменены другими.
* @SuppressWarnings - отключает вывод предупреждений компилятора.
* @Documented - аннотация будет помещена в сгенерированную документацию javadoc.
* @FunctionalInterface - говорит о том, что данный интерфейс функциональный 
  и должен содержать не более одного метода.
* @Inherited - помечает аннотацию, которая будет унаследована потомком класса, 
  отмеченного такой аннотацией.
  
Пример:

```java
//аннотация будет помещена в сгенерированную документацию javadoc
@Documented
//указывается над классом
@Target(ElementType.TYPE)
//может использоваться во время выполнения самой программы
@Retention(RetentionPolicy.RUNTIME)
//@interface: сообщает о том, что это аннотация
public @interface FunctionalInterface {} //аннотация маркер

//указывается над методом
@Target(ElementType.METHOD)
//аннотация используется только при написании кода и игнорируется компилятором
@Retention(RetentionPolicy.SOURCE) 
//@interface: сообщает о том, что это аннотация
public @interface Override {} //аннотация маркер

@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, MODULE, PARAMETER, TYPE})
public @interface Deprecated {
  //Возвращает версию, в которой аннотированный элемент стал устаревшим.
  String since() default "";//default значением мб только константное НЕ null-значение.
  //подлежит ли элемент удалению
  boolean forRemoval() default false;
}

//Кроме элементов со значениями по умолчанию, 
//в аннотациях можно использовать константы. 
//Они, как и в интерфейсах, неявно public, static и final.
public @interface ReadingTime {
  int MIN_POST_READING = 1;
  int MAX_POST_READING = 20;
  int avgTime() default  MIN_POST_READING;
  int readLimit() default MAX_POST_READING;
}
```

Набор типов для элементов ограничен, можно использовать только:
* примитивные типы (byte, short, int, long, float, double, boolean, char);
* String;
* Class;
* перечисление (enum);
* другую аннотацию;
* массив любого из вышеперечисленных типов.

####Аннотации библиотеки Lombok

* @AllArgsConstructor – конструктор со всеми полями класса
* @RequiredArgsConstructor – конструктор со всеми final полями класса
* @NoArgsConstructor – конструктор без параметров
* @Getter-создает геттеры для полей класса.
* @Setter-создает сетторы для полей класса.
* @ToString-создает метод ToString.
* @EqualsAndHashCode-создает методы equals и hashCode.
* @Data-эквивалентна комбинации аннотаций @Getter, @Setter, 
  @ToString, @EqualsAndHashCode, и @RequiredArgsConstructor


* @Value - реализация неизменяемого(immutable) класса
* @Builder - реализация паттерна строитель для класса
* @NonNull - проверка на null
* @Cleanup - автоматическая очистка ресурса
* @SneakyThrows - можно использовать для скрытого создания проверенных исключений 
  без фактического объявления этого в предложении вашего метода throws
* @Synchronized- более безопасный вариант synchronized модификатора метода.

>Java Architecture for XML Binding (JAXB) — это программная структура, 
>которая позволяет разработчикам отображать классы Java в представления XML. 
>JAXB позволяет делать сохранение объекта в файл и обратно в объекты.
 
Пример:
```java
@XmlRootElement(name = "employee")
@XmlAccessorType(XmlAccessType.FIELD)
public class Employee implements Serializable 
{
    private Integer id;
    private String fullName;
}
```
Java объект с помощью JAXB можно преобразовать в xml.
```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<employee>
  <id>1</id>
  <fullName>Lokesh</fullName>
</employee>
```

[Первый источник знаний](https://topjava.ru/blog/rukovodstvo-po-annotatsiyam-v-java-i-mekhanizmu-ikh-raboty)

[Второй источник знаний](https://skillbox.ru/media/base/kak-napisat-annotatsiyu-na-java-za-5-shagov/)

[Третий источник знаний](https://howtodoinjava.com/jaxb/jaxb-annotations/)

[Lombok источник знаний](https://projectlombok.org/features/all)

[JAXB источник знаний](https://javarush.ru/quests/lectures/questcollections.level03.lecture07)