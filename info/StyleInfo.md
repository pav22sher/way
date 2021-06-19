###Порядок указания элементов файла
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

Тип переменной|Правила именования|Примеры
---|---|---
классы|Имя классов должно начинаться с большой буквы и быть существительным. Если это не одно слово,то каждое следующее слово в названии класса должно начинатся с заглавной буквы. Старайтесь, чтобы имена ваших классов были простыми и описательными. Используйте целые слова(избегайте аббревиатур и сокращений)|class LivingWage{}
интерфейсы|Имена интерфейсов должны быть написаны с заглавной буквы, как и имена классов. Часто в конце присутсвуют суффиксы -able(причастие)|interface Printable{}
методы|Методы должны быть написаны с маленькой буквы и быть глаголам.Если это не одно слово,то каждое следующее слово в названии метода должно начинаться с заглавной буквы.|doSomthing(){}
поля/переменные|Имена переменных должны быть короткими, но значимыми. Выбор имени переменной должен быть мнемоническим—то есть предназначенным для того, чтобы указать случайному наблюдателю на намерение его использования|String description
константы|Имена переменных, объявленных константами должны быть прописными в верхнем регистре, если константа состоит из нескольких слов, то разделить их знаком нижнего подчеркивания|final int MAX_LENGTH

###Общий пример для стиля
```java
/*
 * %W% %E% Firstname Lastname
 *
 * Copyright (c) 1993-1996 Sun Microsystems, Inc. All Rights Reserved.
 *
 * This software is the confidential and proprietary information of Sun
 * Microsystems, Inc. ("Confidential Information"). You shall not
 * disclose such Confidential Information and shall use it only in
 * accordance with the terms of the license agreement you entered into
 * with Sun.
 *
 * SUN MAKES NO REPRESENTATIONS OR WARRANTIES ABOUT THE SUITABILITY OF
 * THE SOFTWARE, EITHER EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED
 * TO THE IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A
 * PARTICULAR PURPOSE, OR NON-INFRINGEMENT. SUN SHALL NOT BE LIABLE FOR
 * ANY DAMAGES SUFFERED BY LICENSEE AS A RESULT OF USING, MODIFYING OR
 * DISTRIBUTING THIS SOFTWARE OR ITS DERIVATIVES.
 */
package java.blah;
import java.blah.blahdy.BlahBlah;
/**
 * Class description goes here.
 *
 * @version 1.10 04 Oct 1996
 * @author Firstname Lastname
 */
public class Blah extends SomeClass {
 /* A class implementation comment can go here. */
 /** classVar1 documentation comment */
 public static int classVar1;
 /*** classVar2 documentation comment that happens to be
 * more than one line long
 */
 private static Object classVar2;
 /** instanceVar1 documentation comment */
 public Object instanceVar1;
 /** instanceVar2 documentation comment */
 protected int instanceVar2;
 /** instanceVar3 documentation comment */
 private Object[] instanceVar3;
 /**
 * ...method Blah documentation comment...
 */
 public Blah() {
 // ...implementation goes here...
 }
 /**
 * ...method doSomething documentation comment...
 */
 public void doSomething() {
 // ...implementation goes here...
 }
 /**
 * ...method doSomethingElse documentation comment...
 * @param someParam description
 */
 public void doSomethingElse(Object someParam) {
 // ...implementation goes here...
 }
}
```