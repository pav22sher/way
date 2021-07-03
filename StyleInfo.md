###Порядок указания элементов файла с исходным кодом
<span style="color: red">(Все, что далее изложено носит рекомендательный характер)</span>

* Комментарий
* Название пакета
* Импорт пакетов
* Public класс или интерфейс <span style="color: red">(должен быть одним в файле)</span>.
* Импорт пакетов
* Не публичные классы и интерфейсы.
<p style="color: red">
Файлы длиной более 2000 строк являются громоздкими, и их следует избегать.
</p>

Пример кода:
```java
/*
 * Classname - Имя класса
 *
 * Version info - Информация о версии
 *
 * Copyright notice - Уведомление об авторских правах
 */
package examplePackage.examplePackage;

import importPackage.ImportClass;

public class PublicClass{}

class NotPublicClass{}
```

###Порядок указания элементов класса
* указывать static поля (поля класса) в порядке 
  * public 
  * protected
  * private
* указывать не static поля (поля экземпляра класса) в порядке
  * public
  * protected
  * private
* конструкторы (первым указать конструктор без параметров)
* методы
><div style="color: red">Методы должны быть сгруппированы по функциональности, а не по области применения или доступности.
>Например, метод частного класса может находиться
>между двумя методами открытого экземпляра. Цель состоит
>в том, чтобы облегчить чтение и понимание кода.</div>

Пример кода:
```java
/*
 * Classname - Имя класса
 *
 * Version info - Информация о версии
 *
 * Copyright notice - Уведомление об авторских правах
 */
package examplePackage.examplePackage;

import importPackage.ImportClass;

public class PublicClass{ 
    static public String exampleClassField1;
    static protected String exampleClassField2;
    static private String exampleClassField3;

    static public String exampleObjectField1;
    static protected String exampleObjectField2;
    static private String exampleObjectField3;

    PublicClass(){}
    
    public void showMsg(){
        System.out.println(getMsg());
    }
    
    private String getMsg(){
        return "Hello World!";
    } 
}

class NotPublicClass{}
```


###Избегайте строк длиной более 80 символов.
><div style="color: red">Если выражение не помещается в одну строку, разбейте его в соответствии 
>с этими общими принципами</div>
* Перевод на новую строку после запятой
* Перевод на новую строку перед оператором
Примеры:
```java
void function(int longExpression1,int longExpression2, int longExpression3,
                      int longExpression4, int longExpression5);
```
```java
int longName1 = longName2 * (longName3 + longName4 - longName5)
```
```java
+ 4 * longname6;
if ((condition1 && condition2)
        || (condition3 && condition4)){
    doSomethingAboutIt();
}
```
```java
alpha = (aLongBooleanExpression) ? beta : gamma;

alpha = (aLongBooleanExpression) ? beta
: gamma;

alpha = (aLongBooleanExpression)
? beta
: gamma;
```

###Комментарии
>Комментарии должны содержать только ту информацию, которая имеет
>отношение к чтению и пониманию программы.

>Частота комментариев иногда отражает низкое качество кода. 
>Если вы чувствуете необходимость добавить комментарий, подумайте о том,
>чтобы переписать код, чтобы сделать его более понятным.

###Общие замечания
* Фигурные скобки используются вокруг всех операторов, 
  даже одиночных, когда они являются частью структуры управления, 
  такой как оператор if-else или for
```java
if(true){}
```
```java
do(){
} while();
```
* Избегайте магических цифр в коде
```java
if(age > 18){} //плохо

final int MAX_AGE = 18;
if(MAX_AGE > 18){} //плохо
```


###Правила именования

>Camel case (camelCase) - «Верблюжий регистр» — по аналогии с горбатым красавцем
>каждое следующее слово в цепочке начинается с заглавной буквы.
>Существует lowerCamelCase(методы в java) и UpperCamelCase(классы в java).

>Snake case (snake_case) - «Змеиный регистр» — заменяет пробелы на символ подчеркивания.
>Существует lower_case_snake_case(таблицы бд) и UPPER_CASE_SNAKE_CASE(SCREAMING_SNAKE_CASE константы)

>Kebab case (kebab-case) - «Змеиный регистр» - заменяет пробелы на символ дефис.
>Используется в URL-адресах (http://localhost:8080/test-test)

Тип переменной|Правила именования|Примеры
---|---|---
классы|Имя класса - существительное. Старайтесь, чтобы имена ваших классов были простыми и описательными. Используйте целые слова(избегайте аббревиатур и сокращений)|class LivingWage{}
интерфейсы|Имя интерфейса - часто причастие(присутствует суффиксы -able)|interface Printable{}
методы|Имя метода - глагол.|runMethod(){}
поля/переменные/константы|Имена переменных должны быть короткими, но значимыми. Выбор имени переменной должен быть мнемоническим—то есть предназначенным для того, чтобы указать случайному наблюдателю на намерение его использования|String description; final int MAX_LENGTH

###Принципы хорошего кода

>DRY – Don’t repeat yourself – принцип призывает Вас не повторяться при написании кода. 
>Все что Вы пишите в проекте, должно быть определено только один раз.

>KISS – keep it short simple – делайте вещи проще. Порой наиболее правильное решение – 
>это наиболее простая реализация задачи, в которой нет ничего лишнего.

>YAGNI — You ain’t gonna need it – вам это не понадобится. Все что не предусмотрено 
>техническим заданием проекта, не должно быть в нем.

###SOLID

>Single-responsibility principle /Принцип единственной ответственности -
>программные объекты должны отвечать только за что-то одно.

>Open–closed principle / Принцип открытости-закрытости -
>программные объекты должны быть открыты для расширения, но закрыты для модификации.

>Liskov substitution principle / Принцип подстановки Лисков -
>должна быть возможность вместо базового типа подставить любой его подтип.

>Interface segregation principle / Принцип разделения интерфейсов -
>слишком «толстые» интерфейсы необходимо разделять на более маленькие.

[Первый источник знаний](https://www.oracle.com/technetwork/java/codeconventions-150003.pdf)

[Второй источник знаний](http://download.blackball.lv/data/library/Chistyj_kod_-_Sozdanie_analiz_i_refaktoring_%282013%29.pdf)

[Третий источник знаний](https://medium.com/webbdev/solid-4ffc018077da)

[Четвертый источник знаний](https://professorweb.ru/my/it/blog/net/solid.php)