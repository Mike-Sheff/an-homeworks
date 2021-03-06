## Задача 2

Эта задача про телефонный справочник с поддержкой групп контактов. Один контакт может входить в несколько групп, например, если вы работаете со своим другом, то он будет в группах Друзья и Работа. У пользователя должна быть возможность создания групп и контактов, добавления контакта в несколько групп. Ну и конечно же наш список контактов отсортирован в алфавитном порядке.

1. Вам нужно создать класс `Contact`:
    * Имя
    * Номер телефона

2. Переопределить методы `hashCode` и `equals` для  корректной работы HashSet. Также для вывода контакта на экран переопределить метод `toString`.

3. По аналогии с первой задачей создать методы для ввода `Contact` с клавиатуры. 

4. Для того чтобы наш список контактов был отсортирован по имени, необходимо чтобы класс `Contact` реализовывал интерфейс `Comparable`. C похожей задачей мы уже сталкивались на лекции по одномерным массивам.

5. Создадим `List<Contact>`, который будем всегда поддерживать отсортированным по имени. Он нам пригодиться если пользователь захочет просмотреть все контакты в алфавитном порядке. Для этого перед добавлением очередного элемента в список, будем находить для него правильную позицию, при которой имя предыдущего будет меньше, а имя следующего больше. 
Так как список у нас все время будет отсортированный, то эффективнее всего искать позицию для элемента с помощью [бинарного поиска](https://wikipedia.org/wiki/Двоичный_поиск). 
В  Java этот алгоритм уже реализован в `Collections.binarySearch(list, key)`: 
* если элемент содержится в списке, то метод вернет его позицию, 
* если элемента в коллекции нет, то метод вернет место, куда он должен быть вставлен. 
Можно воспользоваться им или написать свою реализацию.

> На следующих лекциях мы будем рассматривать структуры данных которые "из коробки" позволяют хранить данные отсортированными. Например класс TreeSet.

6. Далее создадим HashMap, где ключом будет имя группы, а значением множество HashSet контактов в этой группе (в группе может быть несколько контактов, но каждый контакт может встречаться в этой группе только один раз).

7. Логика работы приложения. На выбор пользователю выводится несколько действий:
    1. Просмотреть все контакты в алфавитном порядке.
    2. Просмотреть все группы с содержащимися контактами (см. пример).
    3. Добавить новый контакт.
    4. При создании нового контакта приложение предлагает добавить его в группы. Если введенной группы ещё не существует – она создается автоматически.

Пример отображения списка групп:
```
Семья:
  Мама +70000000000
  Папа +70000000001
  Я +70000000002

Работа:
  Саня +70000000003

Друзья:
  Саня +70000000003
```

8. Для демонстрации работы программы в коде создайте несколько контактов и добавьте в несколько групп.

> Так как со временем наши задачи становятся всё объёмнее, пора бы задуматься об архитектуре нашего приложения:
> Как можно больше логики выносите из функции main в небольшие, узкоспециализированные функции! Так будет намного легче писать/читать/поддерживать код.

## Задача 2`*`

В дополнение к возможным действиям задачи № 2 добавьте возможности:
* редактирования контакта (как его полей, так и групп в которые он входит);
* редактирование групп добавление, удаление, изменение имени.
