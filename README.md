- [Javascript fundamentals](#javascript-fundamentals)
  - [Basic syntax](#basic-syntax)
    - [Literal values](#literal-values)
    - [Variable values](#variable-values)
    - [Operators](#operators)
    - [Operator precedence](#operator-precedence)
    - [Operator associativity](#operator-associativity)
    - [Operator precedence table](#operator-precedence-table)
    - [Expression](#expression)
    - [Keywords](#keywords)
    - [Comments](#comments)
    - [Identifiers](#identifiers)
  - [Hoisting](#hoisting)
  - [Event bubling](#event-bubling)
  - [Scope](#scope)
  - [Prototype](#prototype)
  - [Variables](#variables)
  - [Arrays & Object literals](#arrays--object-literals)
  - [Events](#events)
  - [Functions](#functions)
  - [Loops](#loops)
  - [Conditionals](#conditionals)
  - [Closures](#closures)
- [Modules](#modules)
  - [ES6 Modules, TypeScript (Angular)](#es6-modules-typescript-angular)
  - [Parcel, Webpack & Babel](#parcel-webpack--babel)
  - [Export & Export Default](#export--export-default)
- [Classes](#classes)
  - [Structuring a class](#structuring-a-class)
  - [Constructors](#constructors)
  - [Methods & properties](#methods--properties)
  - [Instantiation](#instantiation)
  - [Extending classes](#extending-classes)
- [Arrow functions](#arrow-functions)
  - [Looks much cleaner and less lines of code](#looks-much-cleaner-and-less-lines-of-code)
  - [The standard in writing modern Javascript](#the-standard-in-writing-modern-javascript)
  - [Scope and “lexical this”](#scope-and-lexical-this)
- [Promises / Asynchronus requests](#promises--asynchronus-requests)
  - [HTTP request](#http-request)
  - [Learn how to create and recieve promises](#learn-how-to-create-and-recieve-promises)
  - [Standard .then( ) and .catch( ) syntax](#standard-then--and-catch--syntax)
  - [Async / Await is optional but recommended](#async--await-is-optional-but-recommended)
  - [Learn the Fetch API for making HTTP requests](#learn-the-fetch-api-for-making-http-requests)
- [Destructuring](#destructuring)
- [Concept of components & state](#concept-of-components--state)
  - [Each component can have it’s own data & state of being](#each-component-can-have-its-own-data--state-of-being)
  - [We also have application level state, usually implemented using a state manager like Redux, Vuex, etc](#we-also-have-application-level-state-usually-implemented-using-a-state-manager-like-redux-vuex-etc)
  - [Nested components (Parent & children)](#nested-components-parent--children)
  - [Can be directly inserted or used in a router](#can-be-directly-inserted-or-used-in-a-router)
- [Spread operator (...)](#spread-operator)
- [High order array functions](#high-order-array-functions)
  - [forEach( ) - basic iteration / looping](#foreach----basic-iteration--looping)
  - [map( ) - manipulation the data to create a new array](#map----manipulation-the-data-to-create-a-new-array)
  - [filter( ) - used to filter out certain pieces of data; used a lot in state reducers](#filter----used-to-filter-out-certain-pieces-of-data-used-a-lot-in-state-reducers)

# Javascript fundamentals

## Basic syntax

Składnia języka JavaScript wyróżnia dwa typy wartości:

### Literal values

Stałe wartości to głównie liczby i ciągi znaków.

Liczby zapisujemy jako ułamek z kropką lub nie:

`123.456`

`123`

Ciągi znaków - **String** zapisujemy w podwójnych lub pojedynczych cudzysłowach:

`"To jest ciąg znaków"`

`'To też jest ciąg'`

### Variable values

Zmienne wartości służą do przechowywania danych. W JavaScript do deklarowania zmiennych służą słowa kluczowe:

- `var`
- `let`
- `const`

Operator `=` służy do przypisania wartości do zmiennej.

```javascript
const x;
x = 5;
```

### Operators

Javascript używa operatorów arytmetycznych do obliczania wartości:

`+ - * /`

Znak `=` jest operatorem przypisania wartości do zmiennych.

### Operator precedence
Pierwszeństwo operatorów określa zachowanie operatorów niższego i wyższego pierwszeństwa względem siebie.
```javascript
console.log(3 + 4 * 5); // evaluates to 23: 4 * 5; 20 + 3; 23
```

### Operator associativity
Asocjatywność określa sposób, w jaki operatory o tym samym pierwszeństwie są przetwarzane: z **lewej do prawej** lub z **prawej do lewej.**

`a OPERATOR b OPERATOR c`

może być roziązane w zależności od asocjatywności:

`(a OPERATOR b) OPERATOR c`

lub

`a OPERATOR (b OPERATOR c)`

### Operator precedence table
Poniższa tabela jest uporządkowana od **najwyższego (20)** do **najniższego (1)** pierwszeństwa.

| Precedence | Operator type                 | Associativity | Individual operators |
| :--------- | :---------------------------- | :------------ | :------------------- |
| 20         | Grouping                      | n/a           | `( … )`              |
| 19         | Member Access                 | left-to-right | `… . …`              |
|            | Computed Member Access        | left-to-right | `… [ … ]`            |
|            | `new` (with argument list)    | n/a           | `new … ( … )`        |
|            | Function Call                 | left-to-right | `… ( … )`            |
|            | Optional chaining             | left-to-right | `?.`                 |
| 18         | `new` (without argument list) | right-to-left | `new …`              |
| 17         | Postfix Increment             | n/a           | `… ++`               |
|            | Postfix Decrement             |               | `… --`               |
| 16         | Logical NOT                   | right-to-left | `! …`                |
|            | Bitwise NOT                   |               | `~ …`                |
|            | Unary Plus                    |               | `+ …`                |
|            | Unary Negation                |               | `- …`                |
|            | Prefix Increment              |               | `++ …`               |
|            | Prefix Decrement              |               | `-- …`               |
|            | `typeof`                      |               | `typeof …`           |
|            | `void`                        |               | `void …`             |
|            | `delete`                      |               | `delete …`           |
|            | `await`                       |               | `await …`            |
| 15         | Exponentiation                | right-to-left | `… ** …`             |
| 14         | Multiplication                | left-to-right | `… * …`              |
|            | Division                      |               | `… / …`              |
|            | Remainder                     |               | `… % …`              |
| 13         | Addition                      | left-to-right | `… + …`              |
|            | Subtraction                   |               | `… - …`              |
| 12         | Bitwise Left Shift            | left-to-right | `… << …`             |
|            | Bitwise Right Shift           |               | `… >> …`             |
|            | Bitwise Unsigned Right Shift  |               | `… >>> …`            |
| 11         | Less Than                     | left-to-right | `… < …`              |
|            | Less Than Or Equal            |               | `… <= …`             |
|            | Greater Than                  |               | `… > …`              |
|            | Greater Than Or Equal         |               | `… => …`             |
|            | `in`                          |               | `… in …`             |
|            | `instanceof`                  |               | `… instanceof …`     |
| 10         | Equality                      | left-to-right | `… == …`             |
|            | Inequality                    |               | `… != …`             |
|            | Strict Equality               |               | `… === …`            |
|            | Strict Inequality             |               | `… !== …`            |
| 9          | Bitwise AND                   | left-to-right | `… & …`              |
| 8          | Bitwise XOR                   | left-to-right | `… ^ …`              |
| 7          | Bitwise OR                    | left-to-right | `… | …`              |
| 6          | Logical AND                   | left-to-right | `… && …`             |
| 5          | Logical OR                    | left-to-right | `… || …`             |
| 4          | Conditional                   | right-to-left | `… ? … : …`          |
| 3          | Assignment                    | right-to-left | `… = …`              |
|            |                               |               | `… += …`             |
|            |                               |               | `… -= …`             |
|            |                               |               | `… **= …`            |
|            |                               |               | `… *= …`             |
|            |                               |               | `… /= …`             |
|            |                               |               | `… %= …`             |
|            |                               |               | `… <<= …`            |
|            |                               |               | `… >>= …`            |
|            |                               |               | `… >>>= …`           |
|            |                               |               | `… &= …`             |
|            |                               |               | `… ^= …`             |
|            |                               |               | `… |= …`             |
| 2          | `yield`                       | right-to-left | `yield …`            |
| 1          | Comma / Sequence              | left-to-right | `… , …`              |

### Expression

Wyrażenie jest kombinacją wartości, zmiennych i operatorów, które obliczają wartość. Te obliczenia nazywa sie **evaluation.**

```javascript
2 * 5; // evaluates to 10
```

```javascript
var secondName = 'Deep';
'Johnny' + secondName; // evaluates to "Johnny Deep"
```

### Keywords

Słowa kluczowe w JavaScript służą do identyfikowania akcji jaką język ma wykonać. W JavaScript nie można używać tych zarezerwowanych słów jako zmiennych, etykiet lub nazw funkcji:

|   []()   |    []()    |     []()     |   []()    |
| :------: | :--------: | :----------: | :-------: |
| abstract | arguments  |    await     |  boolean  |
|  break   |    byte    |     case     |   catch   |
|   char   |   class    |    const     | continue  |
| debugger |  default   |    delete    |    do     |
|  double  |    else    |     enum     |   eval    |
|  export  |  extends   |    false     |   final   |
| finally  |   float    |     for      | function  |
|   goto   |     if     |  implements  |  import   |
|    in    | instanceof |     int      | interface |
|   let    |    long    |    native    |    new    |
|   null   |  package   |   private    | protected |
|  public  |   return   |    short     |  static   |
|  super   |   switch   | synchronized |   this    |
|  throw   |   throws   |  transient   |   true    |
|   try    |   typeof   |     var      |   void    |
| volatile |   while    |     with     |   yield   |

### Comments

Nie wszystkie polecenia JavaScript są "wykonywane". Kod po podwójnym ukośniku `//` lub pomiędzy `/*` i `*/` jest traktowany jako komentarz i nie zostanie wykonany.

### Identifiers

Identyfikatory to nazwy. W JavaScript identyfikatory są używane do nazwania zmiennych, słów kluczowych, funkcji i etykiet. Zasady dotyczące dozwolonych nazw są takie same jak w większości języków programowania.

W JavaScript pierwszy znak musi być literą lub podkreśleniem `_` lub znakiem dolara `$`

Kolejne znaki mogą być literami, cyframi, podkreśleniami lub znakami dolarowymi.

Numery nie są dozwolone jako pierwszy znak. W ten sposób JavaScript może łatwo odróżnić identyfikatory od liczb.

JavaScript rozróżnia duże i małe znaki. Zmienne `lastName` i `lastname` to dwie różne zmienne.

W JavaScript przyjętą konwencją łączenia wielu członów nazwy w jeden **identifier** jest **Camel case.**

## Hoisting

## Event bubling

## Scope

## Prototype

## Variables

## Arrays & Object literals

## Events

## Functions

## Loops

## Conditionals

## Closures

# Modules

## ES6 Modules, TypeScript (Angular)

## Parcel, Webpack & Babel

## Export & Export Default

# Classes

## Structuring a class

## Constructors

## Methods & properties

## Instantiation

## Extending classes

# Arrow functions

## Looks much cleaner and less lines of code

## The standard in writing modern Javascript

## Scope and “lexical this”

# Promises / Asynchronus requests

## HTTP request

An HTTP request is use to send and recieve data between the client and server, in which you would use a HTTP method (GET, POST, PUT, DELETE, etc.). These HTTP requests can be made from the client or server, depending on your project.

## Learn how to create and recieve promises

## Standard .then( ) and .catch( ) syntax

## Async / Await is optional but recommended

## Learn the Fetch API for making HTTP requests

# Destructuring

# Concept of components & state

## Each component can have it’s own data & state of being

## We also have application level state, usually implemented using a state manager like Redux, Vuex, etc

## Nested components (Parent & children)

## Can be directly inserted or used in a router

# Spread operator (...)

# High order array functions

## forEach( ) - basic iteration / looping

## map( ) - manipulation the data to create a new array

## filter( ) - used to filter out certain pieces of data; used a lot in state reducers
