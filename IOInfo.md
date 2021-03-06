###Потоки ввода-вывода

Основные пакеты для работы с потоками ввода/вывода:
* java.io
* java.nio

Потоки бывают 2 типов:
* потоки байтов (базовые абстрактные классы InputStream и OutputStream)
* потоки символов (базовые абстрактные классы Reader и Writer)

> Для оптимизации операций ввода/вывода используются буферизуемые потоки.
> Эти потоки добавляют к стандартным специальный буфер в памяти,
> с помощью которого повышается производительность при работе с потоками.

###InputStream

Наследники класса InputStream:
* FileInputStream - читает данные из файла
* BufferedInputStream - буферизованный поток ввода
* ByteArrayInputStream - читает данные из массива
* DataInputStream - читает данные стандартных типов (int, long, double и т.д)
* ObjectInputStream - читает данные ссылочных типов (объекты)

Методы класса InputStream:
* int read() - возвращает целочисленное представление следующего байта в потоке
* int read(byte[] buffer) - считывает байты из потока в массив buffer и возвращает число считанных байтов.
* int read(byte[] buffer, int offset, int length) - считывает некоторое количество байтов,
  равное length, из потока в массив buffer, начиная со смещения offset, то есть с элемента buffer[offset].
* void close() - закрывает поток
* int available() - возвращает количество байтов, доступных для чтения в потоке
* long skip(long number) - пропускает в потоке при чтении некоторое количество байт

###OutputStream

Наследники класса OutputStream:
* FileOutputStream - записывает данные в файл
* BufferedOutputStream - буферизованный поток вывода
* ByteArrayOutputStream - записывает данные в массив
* DataOutputStream - записывает данные стандартных типов (int, long, double и т.д)
* ObjectOutputStream - записывает данные ссылочных типов (объекты)

Методы класса OutputStream:
* void write(int b) - записывает в выходной поток один байт
* void write(byte[] buffer) - записывает в выходной поток массив байтов buffer
* void write(byte[] buffer, int offset, int length) - записывает некоторое количество байтов,
  равное length, из массива buffer в поток, начиная со смещения offset, то есть с элемента buffer[offset]
* void close() - закрывает поток
* void flush() - очищает буфер вывода, записывая все его содержимое

###Reader

Наследники класса Reader:
* FileReader - читает данные из файла
* BufferedReader - буферизованные поток ввода
* CharArrayReader - читает данные из массива

Методы класса Reader
* int read() - возвращает целочисленное представление следующего символа в потоке
* int read(char[] buffer) - считывает символы из потока в массив buffer и возвращает число считанных символов
* int read(char[] buffer, int offset, int count) - считывает некоторое количество символов, 
  равное count, из потока в массив buffer, начиная со смещения offset, то есть с элемента buffer[offset].
* void close() - закрывает поток
* long skip(long count) - пропускает количество символов, равное count и возвращает число успешно пропущенных символов


###Writer

Наследники класса Writer:
* FileWriter - записывает данные в файл
* BufferedWriter - буферизованный поток вывода
* CharArrayWriter - записывает данные в массив

Методы класса Writer
* void write(int c) - записывает в поток один символ
* void write(char[] buffer) - записывает в поток массив символов
* void write(char[] buffer, int offset, int count) - записывает некоторое количество символов, 
  равное count, из массива buffer в поток, начиная со смещения offset, то есть с элемента buffer[offset]
* void close() - закрывает поток
* void flush() - очищает буфер вывода, записывая все его содержимое

###Closeable

```java
public interface Closeable extends AutoCloseable {
    void close() throws IOException; //закрывает поток после окончания работы с ним
}
```

> При закрытии потока необходимо освободить все выделенные для него ресурсы.
> В случае, если поток окажется не закрыт, может происходить утечка памяти.

> try-с-ресурсами - автоматически вызывает метод close у ресурса.

> В качестве ресурсов в try-with-resources можно передавать только объекты классов
> унаследованных от интерфейса AutoCloseable.

```java
class Test {
  public static void main(String[] args) {
      //try-с-ресурсами с одним ресурсом
      try(FileOutputStream output = new FileOutputStream(path))
      {
        output.write(1);
      }
      //try-с-ресурсами с несколькими ресурсами
      try(FileInputStream input = new FileInputStream(src);
          FileOutputStream output = new FileOutputStream(dest))
      {
        byte[] buffer = input.readAllBytes();
        output.write(buffer);
      }
  }
}
```

###Java NIO или Java New IO или Java Non-blocking IO

###Пакеты

> java.nio.file - улучшенная поддержка работы с файлами

> java.nio.charset - кодеры и декодеры для отображения байт и символов Unicode

> java.nio.channels - каналы и селекторы

NIO:
* Буфер-ориентированный
* Неблокирующий (асинхронный) ввод/вывод
* Селекторы

###Буфер-ориентированный

> Данные считываются в буфер для последующей обработки. 
> Вы можете двигаться по буферу вперед и назад. 
> Это дает немного больше гибкости при обработке данных.
> В то же время, вам необходимо проверять содержит ли буфер 
> необходимый для корректной обработки объем данных. 
> Также необходимо следить, чтобы при чтении данных в буфер 
> вы не уничтожили ещё не обработанные данные.

Буферы:
* ByteBuffer
* IntBuffer
* CharBuffer
* LongBuffer
* DoubleBuffer
* FloatBuffer
* ShortBuffer

###Неблокирующий (асинхронный) ввод/вывод

> Неблокирующий режим позволяет запрашивать считанные данные из канала (channel) 
> и получать только то, что доступно на данный момент, или вообще ничего, 
> если доступных данных пока нет.

> Каналы - это логические порталы, через которые осуществляется ввод/вывод данных, 
> а буферы являются источниками или приёмниками этих переданных данных. 
> При выводе, данные, которые вы хотите отправить, помещаются в буфер, а он передается в канал.
> При вводе, данные из канала помещаются в предоставленный вами буфер.

> Каналы – это шлюзы, которые позволяют получить доступ к сервисам ввода/вывода ОС 
> с минимальными накладными расходами, а буферы – внутренние конечные точки этих шлюзов, 
> используемые для передачи и приема данных.

Каналы:
* FileChannel - работа с файлами
* SocketChanel - работа c TCP-соединением
* ServerSocketChannel - работа c TCP-соединением, инициированные клиентом
* DatagramChannel - работа c UDP-соединением

###Селекторы 

> Селекторы позволяют одному потоку выполнения мониторить несколько каналов ввода. 
> Вы можете зарегистрировать несколько каналов с селектором, 
> а потом использовать один поток выполнения для обслуживания каналов, 
> имеющих доступные для обработки данные, или для выбора каналов, готовых для записи.

Селекторы:
* Selector
* SelectionKey
* WindowsSelectorImpl
