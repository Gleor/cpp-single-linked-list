# **Single linked list**

## **Описание**

Упрощённый аналог [односвязного списка](https://ru.cppreference.com/w/cpp/container/forward_list) из стандартной библиотеки. Реализованы базовые методы контейнера, а также написан вспомогательный класс итератора типа forward_iterator

## **Функционал**

### **Создание экземпляра класса**

**Конструктор по-умолчанию - создаёт пустой список**

```
SingleLinkedList<int> list;
```

**Конструктор из набора элементов**

```
SingleLinkedList<int> list{1, 2, 3, 4, 5};
```

**Копирующий конструктор**

```
SingleLinkedList<int> list_source{1, 2, 3, 4};
auto list_copy(list_source);
```

**Оператор копирующего присваивания**

```
const SingleLinkedList<int> first_list{1, 2, 3, 4};
SingleLinkedList<int> second_list = first_list;
```

### **Методы**

**Получение константных/неконстантных итераторов на начало и конец списка: begin(), end()**

```
SingleLinkedList<int> list{1};
auto iter = list.begin();
assert(*iter == 1);
++iter;
assert(iter == list.end());
```

**Получение информации о ёмкости списка : проверка на отсутствие элементов и текущий размер**

```
SingleLinkedList<int> list{1, 2, 3};
assert(list.GetSize() == 3);
assert(list.IsEmpty() == false);
```

**Добавление и удаление элемента в начале списка**

```
SingleLinkedList<int> list;
list.PushFront(2);
list.PushFront(1);
assert(*list.begin() == 1);
list.PopFront();
assert(*list.begin() == 2);
```

**Вставка и удаление элемента в произвольной позиции**

```
SingleLinkedList<int> list;
auto iter = list.begin();
iter = numbers.InsertAfter(iter, 1);
iter = numbers.InsertAfter(iter, 2);
iter = numbers.InsertAfter(iter, 3);
assert(*iter == 3);
list.EraseAfter(list.begin());
for (auto elem : list) {
    std::cout << elem << " ";
}
```
**Обмен содержимого списков**

```
SingleLinkedList<int> first_list{1, 2, 3, 4, 5};
SingleLinkedList<int> second_list{6, 7, 8, 9, 10};
first_list.swap(second_list);
assert(*first_list.begin() == 6);
assert(*second_list.begin() == 1);
```

**Операторы сравнения двух списков (лексикографически, поэлементно)**

```
SingleLinkedList<int> first_list = {1, 2, 3, 4, 5};
SingleLinkedList<int> second_list = {1, 2, 5, 6, 7};
assert((first_list > second_list) == false);
```

## **Системные требования**

Компилятор С++ с поддержкой стандарта C++17 или новее

## **Использование**

Для испольования данного класса нужно скопировать файл single-linked-list.h в папку с проектом и подключить через директиву #include<single-linked-list.h>
