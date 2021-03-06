# 1.Введение

XML обладает следующими особенностями :

- Переносимость
- Средство взаимодействия приложений
- Расширяемость

## Низкоуровневые API 

Они позволяют взаимодействовать с “сырым” XML кодом. 

**JAXP** (Java  API for XML processing) является тонким уровнем абстракции для первых двух API из этого списка.

1. SAX (Simple API for XML)
2. DOM (Document Object Model)
3. Stax (Streaming API for XML)
4. XSLT(Extrnsible Stylesheet Language Transformations)
5. XPATH

## Высокоуровневые API

Они представляют сущности XML в виде классов. **JAXB** является примером такого API и одновременно реализации от [java.sun.com]()  

## Анализаторы

Реализуют низкоуровневые API(не все) и проверяют на валидность.

- Apache Xerces
- Oracle XML Parser

# 2. Основы

В ходе исследования языка XML и его спецификаций были сделаны следующие выводы:

### Анализаторы

- DOM анализатор использует дерево для прохождения по xml
- SAX использует события и у него нет возможности редактировать файлы
- StaX использует потоки. 

### Namespaces

Используются как UID для некоторой схемы. Для значения пространства имен используют URI, но это не значит, что за ним кроется некий ресурс. Он нужен всего лишь для уникальности имени. Для использования элементов из схемы **ОБЯЗАТЕЛЬНО** указывается. `schemaLocation` не обязателен для некоторых пространств, так как для некоторых пространств(к примеру стандартных) анализатор сам отыщет схему, либо она ему вообще не нужна. Все зависит от анализатора.

### Schema 

Используется для валидации XML файлов. `targetNamespace` указывается в схеме. В xml воспользуется им и включит таргет в пространство имен и добавит `schemaLocation` для определения схемы, что не обязательно. Чтобы элементы в схеме привязывались к  `targetNamespase ` желательно указывать 

``` 
elementFormDefault="qualified"
```

## JAXB

**JAXB** – (Java API for XML Binding) – интерфейс для представления XML в виде java классов. Преобразование работает как и в одну как и в другую сторону. 
