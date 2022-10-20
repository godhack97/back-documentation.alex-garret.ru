# Общие рекомендации
## Развертывание проекта
### Git
При развертывании проекта обязательно нужно составить .gitgnore\

Подключить гит, в гит не должны попадать авторизационные данные проекта. подключение к бд, ssh ..

Проект должен быть приватным и находится в гите компании.

---
### Файлы

1) Все файлы структуры должны быть именованы максимально информативно, Информацию может нести как путь к файлу, так и именование самого файла.

   ```php
   GetUsers.php или Users/Get.php
   ```

2) Структура проекта должна быть понятной, минимальное подключение файлов через ```include_once() ``` , для повторного использования кода используйте ```use```

3) Файлы должны быть написаны в кодировке ```UTF-8``` (в редакторах это стандарт)

------
### Строки
1) Длина строки желательно не должна превышать 80 символов.

2) Недопустимы конструкции по типу:
   ```php
   if(1>1){ true }

    Можно заменить на:

      1>1 ?: false;

    Или:

       if(1>1)
       {
           true
       }
   ```
3) Используйте пустые строки для улучшения читаемости кода
   ```php
   Правильно:

      protected $data;

      function newFunction($result)
      {
          return $result
      }

      function newFunction2($result)
      {
          return $result
      }

   Не правильно:

      protected $data;
      function newFunction($result)
      {
          return $result
      }
      function newFunction2($result)
      {
          return $result
      }
   ```
---

### Именования

1) Всем файлам, переменным, константам, функциям, классам и методам давать "говорящие" названия, чтобы они отражали свою суть, а не были набором безсмысленных символов.
2) В рамках одного проекта придерживаться одного стиля именования переменных, `camelCase` или `snake_case`
3)  Имена констант и глобальных переменных всегда должны быть в верхнем регистре в стиле `UPPER_CASE`.
4)   Функции/методы класса писать в верблюжьей нотации, где первое слово начинается с маленькой буквы, все остальные с большой в стиле `сamelCase()`.
5)   В функциях/методах класса использовать префиксы: `is (обозначение вопроса)`, `get (получить значение)`, `set (установить значение)`.
6) Имена классов в стиле StudlyCaps.
Каждое слово в имени класса с большой буквы и никаких символов, кроме букв латинского алфавита.
---
### Основы синтаксиса
1) Однострочный комментарий `//` `#` использовать можно везде.
Комментарии писать грамотно с заглавной буквы и делать отступ в один пробел слева.
   ```php
       Правильно:
       // мой комментарий
       #
       Не правильно:
       //мой комментарий
   ```
2)  В качестве отступов использовать табуляцию длиной равной 4-м и не лепить код к левому краю.
    ```php
        if()
            if()
                echo 'ok';

        die();
    ```
3) Булевы значения писать явно `true` , `false`, `null` , не заменять на `0` или `1`
4)  Нельзя писать на одной строке более одной инструкции.
    ```php
    //Неправильно
    $a = $b; $b = $c; $c = $a;

    //Правильно
    $a = $b;
    $b = $c;
    $c = $a;
    ```

5) При выводе `HTML` через `PHP` также придерживаться длины строки 80 символов используя конкатенацию, табуляцию и перенос строк.
6) В тернарном операторе заключать  в скобки только условие, при сложном условии стоит заменить его на `if/else` и не стесняться его использовать.
   ```php
    $var = (условие) ? 'если true' : 'если false';
   ```
7) Использовать сокращение тернарного оператора
   ```php
       $var = 'переменная' ?: 'другая переменная';
   ```
8) Использовать null-коалисцентный оператор только для проверки на null. Часты случаи ошибок в коде из-за неправильного использования оператора `??`.
9) Короткие строки писать выше длинных.
   ```php
   use \Bitrix\Main\Entity,
       \Bitrix\Highloadblock as HL,
       \Godra\Api\Helpers\Utility\Misc;
   ```
#### Массивы
10) При множественной инициализации переменных выравнивать значения между ними по правому краю используя доп. пространство.
    ```php
        protected static $row_data    = [];
        protected static $select_rows = [];
        protected static $api_ib_code = false;
    ```
11) Все массивы прописывать через `[]` вместо стандартного `array()`.
12) Придерживаться такому форматированию массивов
    ```php
    // Если значений больше 2х - каждый аргумент с новой строки
        protected static $select_rows = [
            [ 'name' => 'URL'],
            [ 'name' => 'NAME'],
            [ 'name' => 'CODE'],
            [ 'name' => 'IBLOCK_ID'],
            [ 'name' => 'ID', 'alias' => 'id'],
            [ 'name' => 'PICTURE', 'method' => '\\CFile::getPath'],
        ];

    // По возможности выравнивать оператор |=>| , после последнего элемента оставлять запятую.
        [
            'limit'  => 1,
            'select' => ['*'],
            'filter' => [ 'UF_URL' => $url ],
        ]
    ```

#### Функции
1) При вызове функции пробелы между названием функции и открывающей круглой скобкой недопустимы.
2) В списке аргументов необходим один пробел после каждой запятой и недопустимы пробелы перед запятыми.

#### Управляющие конструкции
1) Стараться короткие конструкции умещать в тернарный оператор
```php
    // Не правильно
    if($x>$y)
    {
        $res = $x;
    }
    else
    {
        $res = $y
    }

    // Правильно
    $res = $x > $y ? $x : $y;
 ```

2) Использовать в конструкциях фигурные скобки `{}`
   ```php
   // Не правильно
      if(true):
          return 'ok';
      endif;

   // Правильно
      if(true)
      {
          return 'ok';
      }
   ```
3) Открывающую фигурную скобку ставить под началом выражения и на одном уровне вертикально с закрывающей
    ```php
   if(true)
   {
       return 'ok';
   }
    ```
4) Избегать лишних фигурных скобок если в условии/блоке одно выражение.
   ```php
   if(isset($name))
      return $name;
   ```
---
## Объектно-ориентированное программирование

#### Пространства имён и оператор use
1) После объявления пространства имен namespace необходима одна пустая строка.
2)  Оператор use должен быть после объявления простарнства имён namespace.

3) Использовать один `use` для всех обьевленных namespas-ов
4)  После блока операторов  use должна быть одна пустая строка.

```php
namespace Godra\Api\HighloadBlock;

use \Godra\Api\Iblock,
    \Bitrix\Iblock\SectionTable,
    \Godra\Api\Helpers\Utility\Misc;

   ```
#### Классы, свойства и методы
1)  Каждый класс должен располагаться в отдельном файле именовоном так-же как и сам класс.

#### Extends и implements
1)  Ключевые слова extends и implements располагать на одной строке с именем класса.
2)  Наследование классов не должно быть слишком запутанным, максимум 2 наследования.
3)  Все используемые пространства имён нужно прописать в `use` и использовать в коде не полный namespace, а только его последнее или 2 последних именования
```php
use \Godra\Api\Iblock,
    \Bitrix\Iblock\SectionTable,
    \Godra\Api\Helpers\Utility\Misc;

class Base
{
    function __construct()
    {
        SectionTable::getList();
        Misc::getDte();
    }
}
```
#### Свойства
1) Для всех свойств и методов класса необходимо объявлять область видимости public, static, protected, private;
2)  Разделять пустой строкой константы и группы свойств по области видимости.
3)   Недопустимо в одном объявлении указывать более одного свойства.
```php
abstract class Base
{
    public static $select_rows = [];
    protected static $row_data = [];
    private static $api_ib_code = false;
}
```
#### Методы
1)  Для всех методов класса необходимо объявлять область видимости public, static, protected, private;
2)   Недопустимо объявлять методы с пробелом между названием и круглой скобкой.

#### Аргументы методов
1)  Аргументы метода со значениями по-умолчанию располагать в конце списка аргументов.
    ```php
    public function getNameByIdOrCode($id_or_code, $type = null )
    {
        if($type)
            $filter = [$type => $id_or_code];
    }
    ```
#### abstract, final и static
1) Ключевые слова abstract и final пишутся перед модификаторам видимости.
2) Ключевое слово static пишется после модификатора видимости.
    ```php
    abstract class Base
    {
        protected satic function getName()
        {
            return;
        }
    }
    ```
---
## Документация
### Классы
1) Каждый класс должен иметь phpDoc блок с описанием входных данных `__construct` и сути класса
2) Переменные в классе также должны быть описаны
3) Каждая функция/метод класса должна иметь doc-блок.

```php
use \Bitrix\Iblock\IblockTable;

/**
 * Базовый абстрактный класс Каталога
 * @param int $id id Каталога
 */
abstract class Base
{
    /**
     * Id каталога
     * @var int
     */
    protected $id;

    function __construct($id)
    {
        $this->id = $id;
        $this->getCatalogById($this->id)
    }

    /**
     * Получение инфоблока каталога
     * @param int $id ID инфоблока
     * @return string|void
     */
    protected function getCatalogById($id)
    {
        return IblockTable::getById($id)->fetch()['NAME'];
    }
```