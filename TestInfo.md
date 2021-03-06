###Тестирование

> JUnit — библиотека для модульного автоматизированного тестирования

JUnit 4:
* @Test – указывает на то, что метод является тестовым
* @Test(expected = Exception.class) - указывает на то, что в тестовом методе
  вы преднамеренно ожидаете Exception
* @Test(timeout = 100) - указывает на то, тестируемый метод 
  не должен занимать больше чем 100 миллисекунд
* @Before - указывает на то, что метод должен выполнятся
  перед каждым тестируемым методом @Test
* @After – указывает на то, что метод должен выполнятся
  после каждого тестируемого метода @Test
* @BeforeClass – указывает на то, что метод должен выполнятся
  один раз перед всеми тестами
* @AfterClass - указывает на то, что метод должен выполнятся
  один раз после всех тестов
* @Ignore – указывает на то, что метод должен быть 
  проигнорирован в момент проведения тестирования
  
JUnit 5:
* @DisplayName - изменение названия теста для отображения
* @Disabled - отключает тест до устранения ошибки
* @ParameterizedTest - позволяют запускать тест несколько раз с разными аргументами
* @ValueSource - источник аргументов для тестов @ParameterizedTest
* @RepeatedTest - позволяет запускать тест несколько раз
* и т.д.

> Класс Assert - содержит методы для сравнения 
> фактического результата с ожидаемы.
> Если фактический результат не соответствует ожидаемому,
> то тест считается не пройденным.

Методы класса Assert:
* fail - прерывание теста с ошибкой
* assertTrue - проверка условия condition == true
* assertFalse - проверка условия condition == false
* assertEquals - проверка условия expected == actual
* assertNotEquals - проверка условия expected != actual
* assertArrayEquals - проверка условия expecteds[] == actuals[]
* assertNull - проверка, что object == null
* assertNotNull - проверка, что object != null
* assertSame - проверка того, что expected и actual указывают на один объект
* assertNotSame - проверка того, что expected и actual указывают на разные объекты

###TDD

> TDD расшифровывается как Test Driven Development (разработка через тестирование).

> Подход TDD заключается в том, что прежде, чем написать какой-то код, вы сначала пишете тест, 
> который будет служить спецификацией, то есть определять, что должен делать этот код.

> Целью TDD является создание спецификации, т.е. требований к функционалу программы.

Этапы разработки:
* создание тестов, которые падают на данном этапе
* написание кода, который проходил бы тесты
* рефакторинг кода

###Виды тестирования

> Позитивное тестирование – проверка того, что программа работает правильно на «правильных» данных.

> Негативное тестирование - проверка того, что программа работает правильно на «неправильных» данных.

> Тестирование белого ящика — метод тестирования ПО, который предполагает полный доступ к коду проекта

> Тестирование серого ящика — метод тестирования ПО, который предполагает частичный доступ к коду проекта

> Тестирование чёрного ящика — метод тестирования ПО, который не предполагает доступ к коду проекта

> Ручное тестирование - без использования дополнительных программных средств

> Автоматизированное тестирование - c использованием дополнительных программных средств

> Модульное тестирование (Unit testing) - тестирование одного модуля в изоляции,
> тестирование методов какого-то класса программы в изоляции от остальной программы.

> Интеграционное тестирование (Integration Testing) - тестирование группы взаимодействующих модулей,
> тестирование взаимодействия нескольких классов, выполняющих вместе какую-то работу.

> Системное тестирование (System Testing) – проверка работы приложения целиком.
