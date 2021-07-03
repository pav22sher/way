###Объектно-ориентированное программирование

####Основные принципы ООП:

* Абстракция

>Абстракция - представление элементов задачи из реального мира в виде объектов в программе.
>Отделение значимой0 информации реального объекта от незначимой в контексте решаемой задачи.

Пример: 
Человека можно описать следующими параметрами:
* ФИО
* дата рождения
* рост
* вес
* адрес проживания
* номер страхового полиса
* семейное положение
* и т.д.

При решении задачи по доставке товаров на дом мы бы создали например такой класс:
```java
class Person{
    private String fullName;
    private String fullAddress;
}
```

При решении задачи по электронной очереди в больнице такой класс:
```java
class Person{
    private String fullName;
    private String poleNumber;
}
```

При решении задачи по анонимному опросу такой класс:

```java
import java.time.LocalDate;

class Person {
    private LocalDate birthDay;
    private MaritalStatus maritalStatus;
}

enum MaritalStatus{
    UNMARRIED("не замужем/не женат"),
    DIVORCED("разведена/разведен"),
    MARRIED("замужем/женат"),
    COHABITATION("гражданский брак или сожительство"),
    WIDOW("вдова/вдовец");
    
    private String ruName;
    
    MaritalStatus(String ruName) {
        this.ruName = ruName;
    }
}
```

---
* Инкапсуляция
  
>Инкапсуляция - сокрытие данных.

Пример:

Поля объекта доступны только из класса.
Для доступа к полям объекта используются публичные методы(геттеры).
Изменить имя товара после создания нельзя.
Цену товара нельзя сделать отрицательной.
```java
import java.math.BigDecimal;

class Product {
    private String name;
    private BigDecimal price;

    public Product(String name, BigDecimal price) {
        setName(name);
        setPrice(price);
    }

    public String getName() {
        return name;
    }
    
    private void setName(String name) {
        if(!name.isEmpty()){
            this.name = name;
        } else {
            throw new RuntimeException("Ошибка: Название продукта не может отсутствовать!");
        }
    }

    public BigDecimal getPrice() {
        return price;
    }

    public void setPrice(BigDecimal price) {
        if(price.compareTo(BigDecimal.valueOf(0)) >= 0){
            this.price = price;
        } else {
            throw new RuntimeException("Ошибка: Цена продукта не должна быть отрицательной!");
        }
    }
}
```

---
* Наследование

>Наследование - использование уже существующих классов для описания новых.

Пример:

У каждого уважающего себя животного должно быть имя.
```java
class Animal{
    private String name;

    public Animal(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
class Dog extends Animal{
    public Dog(String name) {
        super(name);
    }
}
```

---
* Полиморфизм

>Полиморфизм - использование объектов с одинаковым интерфейсом без информации
>о конкретном типе этого объекта.
 
Пример:

Каждый уважающий себя телефон умеет звонить, но звонки бывают разные.
В примере выбор конкретной реализации звонка производился динамически
на основании конкретного типа вызывающего его объекта
в процессе выполнения программы.
```java
public class Main {
    public static void main(String[] args) {
        Phone phone;
        phone = new Phone(111);
        phone.call(222);
        phone = new VideoPhone(111);
        phone.call(333);
    }

    static class Phone {
        private int number;

        public Phone(int number) {
            this.number = number;
        }

        public int getNumber() {
            return number;
        }

        public void setNumber(int number) {
            this.number = number;
        }

        public void call(int outputNumber) {
            System.out.println("Звоним на " + outputNumber);
        }

        public void ring(int inputNumber) {
            System.out.println("Звонят с " + inputNumber);
        }
    }

    static class VideoPhone extends Phone {
        public VideoPhone(int number) {
            super(number);
        }
        @Override
        public void call(int outputNumber) {
            System.out.println("Видео звонок на " + outputNumber );
        }
        @Override
        public void ring(int inputNumber) {
            System.out.println("Видео звонок с " + inputNumber);
        }
    }
}
```

---

[Первый источник знаний](https://javarush.ru/groups/posts/principy-oop)

[Второй источник знаний](https://topjava.ru/blog/oops-concepts-in-java)
