# Примеры кода на MiniC

Большой справочник примеров по всем возможностям языка. Каждый пример — рабочая программа.
Открытый исходный код.

## Содержание

- [Основы](#основы)
- [Условия](#условия)
- [Циклы](#циклы)
- [Функции](#функции)
- [Массивы](#массивы)
- [Struct](#struct)
- [Enum, Union, Const](#enum-union-const)
- [ООП: extends, override, super](#ооп-extends-override-super)
- [Обработка ошибок](#обработка-ошибок)
- [Строки](#строки)
- [Math](#math)
- [Функциональный стиль](#функциональный-стиль)
- [Модули](#модули)
- [Макросы](#макросы)
- [Время и дата](#время-и-дата)
- [Генераторы](#генераторы)
- [Комплексные примеры](#комплексные-примеры)

---

## Основы

### Hello, World

```c
println("Hello, World!");
```

### Переменные всех типов

```c
int a = 42;
String s = "текст";
bool b = true;
long big = 9007199254;
unsigned int u = 100;
auto x = 3.14;

println("int:      " + a);
println("String:   " + s);
println("bool:     " + b);
println("long:     " + big);
println("unsigned: " + u);
println("auto:     " + x);
```

### Арифметика

```c
int x = 17;
int y = 5;

println(x + " + " + y + " = " + (x + y));
println(x + " - " + y + " = " + (x - y));
println(x + " * " + y + " = " + (x * y));
println(x + " / " + y + " = " + (x / y));
println(x + " % " + y + " = " + (x % y));
```

### Операторы сравнения и логики

```c
int a = 5;
int b = 8;
bool x = true;
bool y = false;

println("a < b?  " + (a < b));
println("a >= b? " + (a >= b));
println("a == b? " + (a == b));
println("x && y = " + (x && y));
println("x || y = " + (x || y));
println("!x     = " + (!x));
```

### Инкремент и декремент

```c
let i = 5;

println("i   = " + i);      // 5
println("i++ = " + i++);    // 5, потом i = 6
println("i   = " + i);      // 6
println("++i = " + ++i);    // 7 (сразу)
println("i-- = " + i--);    // 7, потом i = 6
println("i   = " + i);      // 6
```

### Составное присваивание

```c
let x = 10;

x += 5;  println("x += 5 → " + x);  // 15
x -= 3;  println("x -= 3 → " + x);  // 12
x *= 2;  println("x *= 2 → " + x);  // 24
x /= 4;  println("x /= 4 → " + x);  // 6
```

### typeof

```c
println(typeof 42);         // int
println(typeof "привет");   // String
println(typeof true);       // bool
println(typeof nil);        // null
println(typeof [1, 2, 3]);  // array
```

### null и проверки

```c
let x = null;
let y = 5;

if (x == null) {
    println("x — null");
}

if (y != null) {
    println("y — не null, y = " + y);
}
```

---

## Условия

### Чётное / нечётное

```c
int n = 7;

if (n % 2 == 0) {
    println(n + " — чётное");
} else {
    println(n + " — нечётное");
}
```

### else if цепочка

```c
function classify(int x) {
    if (x > 100) {
        println(x + " — огромное");
    } else if (x > 10) {
        println(x + " — большое");
    } else if (x > 0) {
        println(x + " — маленькое");
    } else if (x == 0) {
        println(x + " — ноль");
    } else {
        println(x + " — отрицательное");
    }
}

classify(200);
classify(50);
classify(5);
classify(0);
classify(-10);
```

### switch/case

```c
function dayType(int day) {
    switch (day) {
        case 1: return "понедельник";
        case 2: return "вторник";
        case 3: return "среда";
        case 6: return "суббота";
        case 7: return "воскресенье";
        default: return "неизвестный день";
    }
}

for (let i = 1; i <= 8; i++) {
    println(i + " → " + dayType(i));
}
```

### Високосный год

```c
function isLeap(int year) {
    if (year % 400 == 0) { return true; }
    if (year % 100 == 0) { return false; }
    if (year % 4 == 0) { return true; }
    return false;
}

println("2024: " + isLeap(2024));  // true
println("2023: " + isLeap(2023));  // false
println("2000: " + isLeap(2000));  // true
println("1900: " + isLeap(1900));  // false
```

---

## Циклы

### for

```c
for (let i = 1; i <= 10; i++) {
    println(i);
}
```

### while

```c
let i = 1;

while (i <= 5) {
    println("i = " + i);
    i++;
}
```

### do-while

```c
let i = 0;

do {
    println("i = " + i);
    i++;
} while (i < 5);
```

### foreach

```c
let arr = [10, 20, 30, 40, 50];

for (x in arr) {
    println("Элемент: " + x);
}
```

### break и continue

```c
println("Чётные до 10 без 6:");

for (let i = 0; i <= 10; i++) {
    if (i == 6) { continue; }
    if (i > 8) { break; }
    if (i % 2 == 0) { println(i); }
}
```

### Вложенные циклы — таблица умножения

```c
for (let i = 1; i <= 9; i++) {
    for (let j = 1; j <= 9; j++) {
        print(i * j);
        if (i * j < 10) {
            print("  ");
        } else {
            print(" ");
        }
    }
    println();
}
```

### Ромб из звёздочек

```c
int n = 5;

for (let i = 1; i <= n; i++) {
    for (let j = 0; j < n - i; j++) { print(" "); }
    for (let j = 0; j < 2 * i - 1; j++) { print("*"); }
    println();
}
for (let i = n - 1; i >= 1; i--) {
    for (let j = 0; j < n - i; j++) { print(" "); }
    for (let j = 0; j < 2 * i - 1; j++) { print("*"); }
    println();
}
```

---

## Функции

### Без параметров

```c
function hello() {
    println("Привет!");
}

hello();
hello();
```

### С параметрами и возвратом

```c
function add(int a, int b) {
    return a + b;
}

println(add(3, 4));      // 7
println(add(10, 20));    // 30
```

### C-стиль и JS-стиль

```c
int cAdd(int a, int b) {
    return a + b;
}

function jsAdd(a, b) {
    return a + b;
}

println("cAdd(2, 3)  = " + cAdd(2, 3));
println("jsAdd(2, 3) = " + jsAdd(2, 3));
```

### Рекурсия — факториал

```c
function fact(int n) {
    if (n <= 1) { return 1; }
    return n * fact(n - 1);
}

for (let i = 1; i <= 10; i++) {
    println(i + "! = " + fact(i));
}
```

### Рекурсия — Фибоначчи

```c
function fib(int n) {
    if (n < 2) { return n; }
    return fib(n - 1) + fib(n - 2);
}

for (let i = 0; i <= 15; i++) {
    print(fib(i) + " ");
}
println();
```

### Композиция функций

```c
function inc(int x) { return x + 1; }
function sq(int x) { return x * x; }

function pipeline(int x) {
    x = inc(x);
    x = sq(x);
    x = inc(x);
    return x;
}

println("pipeline(3) = " + pipeline(3));
```

### inline — модификатор

```c
inline int square(int x) {
    return x * x;
}

println("square(7) = " + square(7));
```

### Функция без return

```c
function log(String msg) {
    println("[LOG] " + msg);
}

log("Первое сообщение");
log("Второе сообщение");
```

---

## Массивы

### Заполнение и вывод

```c
int arr[5];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
arr[3] = 40;
arr[4] = 50;

for (let i = 0; i < 5; i++) {
    println("arr[" + i + "] = " + arr[i]);
}
```

### Литерал массива

```c
let arr = [10, 20, 30, 40, 50];

for (let i = 0; i < 5; i++) {
    print(arr[i] + " ");
}
println();
```

### Синтаксис array { }

```c
let arr = array { 1, 2, 3, 4, 5 };

println("Массив: " + arr);

for (x in arr) {
    println("Элемент: " + x);
}
```

### Сумма, максимум, минимум

```c
let a = [5, 3, 8, 1, 9, 2];

int sum = 0;
int maxVal = a[0];
int minVal = a[0];

for (let i = 0; i < 6; i++) {
    sum += a[i];
    if (a[i] > maxVal) { maxVal = a[i]; }
    if (a[i] < minVal) { minVal = a[i]; }
}

println("Сумма:    " + sum);
println("Максимум: " + maxVal);
println("Минимум:  " + minVal);
println("Среднее:  " + (sum / 6));
```

### Сортировка пузырьком

```c
let a = [5, 2, 8, 1, 9, 3, 7, 4];

for (let i = 0; i < 8; i++) {
    for (let j = 0; j < 7 - i; j++) {
        if (a[j] > a[j + 1]) {
            int t = a[j];
            a[j] = a[j + 1];
            a[j + 1] = t;
        }
    }
}

for (let i = 0; i < 8; i++) {
    print(a[i] + " ");
}
println();
```

### Поиск элемента

```c
let a = [10, 20, 30, 40, 50, 60];
int target = 40;
int idx = -1;

for (let i = 0; i < 6; i++) {
    if (a[i] == target) {
        idx = i;
        break;
    }
}

if (idx != -1) {
    println("Нашли " + target + " на позиции " + idx);
}
```

### Бинарный поиск

```c
let a = [1, 3, 5, 7, 9, 11, 13, 15];
int target = 7;
int lo = 0, hi = 7, result = -1;

while (lo <= hi) {
    int mid = (lo + hi) / 2;
    if (a[mid] == target) {
        result = mid;
        break;
    }
    if (a[mid] < target) { lo = mid + 1; }
    else { hi = mid - 1; }
}

println("Позиция: " + result);
```

### Матрица 3×3

```c
let m = [0, 0, 0, 0, 0, 0, 0, 0, 0];

for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
        m[i * 3 + j] = i * 3 + j + 1;
    }
}

for (let i = 0; i < 3; i++) {
    for (let j = 0; j < 3; j++) {
        print(m[i * 3 + j] + " ");
    }
    println();
}
```

### Массив в функцию

```c
function sum(int arr[], int n) {
    int s = 0;
    for (let i = 0; i < n; i++) {
        s += arr[i];
    }
    return s;
}

let data = [1, 2, 3, 4, 5];
println(sum(data, 5));  // 15
```

---

## Struct

### Простая структура

```c
struct Point {
    int x;
    int y;

    int sum() {
        return this.x + this.y;
    }
}

Point p = Point(3, 4);
println("Сумма: " + p.sum());
```

### С конструктором new

```c
struct Point {
    int x;
    int y;
}

Point p1 = Point(3, 4);
Point p2 = new Point(10, 20);

println("p1: (" + p1.x + ", " + p1.y + ")");
println("p2: (" + p2.x + ", " + p2.y + ")");
```

### Массив struct

```c
struct Point {
    int x;
    int y;
}

Point points[3];
points[0] = Point(1, 2);
points[1] = Point(3, 4);
points[2] = Point(5, 6);

for (let i = 0; i < 3; i++) {
    println("(" + points[i].x + ", " + points[i].y + ")");
}
```

### Методы и this

```c
struct Counter {
    int value;

    int inc() {
        this.value++;
        return this.value;
    }

    int dec() {
        this.value--;
        return this.value;
    }

    int reset() {
        this.value = 0;
        return 0;
    }
}

Counter c = Counter(0);
c.inc();
c.inc();
c.inc();
println("После 3 inc: " + c.value);

c.dec();
println("После dec:   " + c.value);

c.reset();
println("После reset: " + c.value);
```

### Приватные поля

```c
struct Account {
    private int balance;
    public String owner;

    public int deposit(int amt) {
        this.balance += amt;
        return this.balance;
    }

    public int getBalance() {
        return this.balance;
    }
}

Account a = Account(1000, "Иван");
a.deposit(500);
println("Баланс: " + a.getBalance());
```

### Статические поля

```c
struct Counter {
    static int count = 0;

    static int inc() {
        Counter.count++;
        return Counter.count;
    }
}

Counter.inc();
Counter.inc();
Counter.inc();
println("Count: " + Counter.count);  // 3
```

### Композиция структур

```c
struct Engine {
    int power;
    String type;
}

struct Car {
    String brand;
    Engine engine;

    String info() {
        return this.brand + " с " + this.engine.type + " " +
               this.engine.power + " л.с.";
    }
}

Engine e = Engine(150, "бензин");
Car c = Car("Toyota", e);
println(c.info());
```

---

## Enum, Union, Const

### Простой enum

```c
enum Day { MON, TUE, WED, THU, FRI, SAT, SUN }

println("Пн = " + Day.MON);  // 0
println("Ср = " + Day.WED);  // 2
println("Вс = " + Day.SUN);  // 6
```

### Enum с явными значениями

```c
enum Status {
    OK = 200,
    NOT_FOUND = 404,
    ERROR = 500
}

println("OK        = " + Status.OK);
println("NOT_FOUND = " + Status.NOT_FOUND);
println("ERROR     = " + Status.ERROR);
```

### Enum в switch

```c
enum Color { RED, GREEN, BLUE }

function name(int c) {
    switch (c) {
        case Color.RED: return "красный";
        case Color.GREEN: return "зелёный";
        case Color.BLUE: return "синий";
        default: return "?";
    }
}

println(name(Color.RED));
println(name(Color.GREEN));
println(name(Color.BLUE));
```

### Union

```c
union Value {
    int i;
    String s;
}

Value v;
v.i = 42;
println("int: " + v.i);

v.s = "строка";
println("String: " + v.s);
```

### Const

```c
const int MAX = 100;
const String APP = "MiniC";
const bool DEBUG = true;

println(APP + " max=" + MAX + " debug=" + DEBUG);
```

### Const — ошибка при изменении

```c
const int N = 10;

try {
    N = 20;
} catch (e) {
    println("Ошибка: " + e);
}
```

---

## ООП: extends, override, super

### Наследование

```c
struct Animal {
    String name;

    virtual String speak() {
        return "...";
    }

    String info() {
        return this.name + " говорит: " + this.speak();
    }
}

struct Dog extends Animal {
    override String speak() {
        return "Гав!";
    }
}

struct Cat extends Animal {
    override String speak() {
        return "Мяу!";
    }
}

Animal a = Animal("Зверь");
Dog d = Dog("Рекс");
Cat c = Cat("Барсик");

println(a.info());  // Зверь говорит: ...
println(d.info());  // Рекс говорит: Гав!
println(c.info());  // Барсик говорит: Мяу!
```

### super — вызов родителя

```c
struct Shape {
    String name;

    virtual int area() {
        return 0;
    }

    String describe() {
        return this.name + " площадью " + this.area();
    }
}

struct Square extends Shape {
    int side;

    override int area() {
        return this.side * this.side;
    }

    override String describe() {
        return "Квадрат — " + super.describe();
    }
}

Square s = Square("kv", 5);
println(s.describe());
```

### Abstract

```c
abstract struct Shape {
    String name;
    abstract int area();
}

struct Rect extends Shape {
    int w;
    int h;

    override int area() {
        return this.w * this.h;
    }
}

Rect r = Rect("rect", 5, 3);
println("Площадь: " + r.area());

// Shape s = Shape("x");  // ← ошибка: abstract
```

---

## Обработка ошибок

### Базовый try/catch

```c
try {
    throw "тестовая ошибка";
} catch (e) {
    println("Поймали: " + e);
}
```

### try/catch/finally

```c
try {
    println("try");
    throw "ошибка";
} catch (e) {
    println("catch: " + e);
} finally {
    println("finally всегда выполняется");
}
```

### Функция с throw

```c
function divide(int a, int b) {
    if (b == 0) {
        throw "Деление на ноль";
    }
    return a / b;
}

try {
    println(divide(10, 2));   // 5
    println(divide(10, 0));   // ошибка
} catch (e) {
    println("Ошибка: " + e);
}
```

### Вложенные try

```c
try {
    println("внешний");
    try {
        println("  внутренний");
        throw "ошибка";
    } catch (e) {
        println("  поймали: " + e);
        throw "проброшено";
    }
} catch (e) {
    println("снаружи: " + e);
}
```

### assert

```c
function check(int x) {
    assert(x > 0, "x должен быть положительным");
    return x;
}

println(check(5));

try {
    check(-1);
} catch (e) {
    println("Ошибка: " + e);
}
```

---

## Строки

### Базовые методы

```c
String s = "Привет, мир!";

println("Длина:       " + s.length());
println("Верхний:     " + s.toUpper());
println("Нижний:      " + s.toLower());
println("Первый:      " + s.charAt(0));
println("Срез 0..6:   " + s.substring(0, 6));
println("Содержит 'мир'? " + s.contains("мир"));
println("Индекс 'мир': " + s.indexOf("мир"));
```

### Замена и обрезка

```c
String s = "  Hello World  ";

println("Trim:        '" + s.trim() + "'");
println("Replace:     '" + s.replace("World", "MiniC") + "'");
```

### Конкатенация

```c
String first = "Иван";
String last = "Петров";
String full = first + " " + last;

println("Полное имя: " + full);
```

### Перебор символов

```c
String s = "Hello";

for (let i = 0; i < s.length(); i++) {
    println("Символ " + i + ": " + s.charAt(i));
}
```

---

## Math

### Базовые операции

```c
println("sqrt(16)   = " + Math.sqrt(16));
println("pow(2, 10) = " + Math.pow(2, 10));
println("abs(-42)   = " + Math.abs(-42));
println("max(3, 7)  = " + Math.max(3, 7));
println("min(3, 7)  = " + Math.min(3, 7));
println("floor(3.7) = " + Math.floor(3.7));
println("ceil(3.2)  = " + Math.ceil(3.2));
println("round(3.5) = " + Math.round(3.5));
```

### Random

```c
for (let i = 0; i < 5; i++) {
    println("Случайное: " + Math.random());
}
```

---

## Функциональный стиль

### Стрелочные функции

```c
let double = (x) => x * 2;
let add = (a, b) => a + b;

println(double(5));       // 10
println(add(3, 4));       // 7
```

### Анонимные функции

```c
let square = function(x) {
    return x * x;
};

println(square(5));  // 25
```

### map

```c
let arr = [1, 2, 3, 4, 5];
let doubled = arr.map((x) => x * 2);

println("Удвоенные: " + doubled);
```

### filter

```c
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let evens = arr.filter((x) => x % 2 == 0);

println("Чётные: " + evens);
```

### reduce

```c
let arr = [1, 2, 3, 4, 5];
let sum = arr.reduce((acc, x) => acc + x, 0);

println("Сумма: " + sum);  // 15
```

### Цепочка map → filter → reduce

```c
let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let result = arr
    .filter((x) => x % 2 == 0)
    .map((x) => x * x)
    .reduce((acc, x) => acc + x, 0);

println("Сумма квадратов чётных: " + result);
```

---

## Модули

### Подключение

```c
#include <math.mc>

println("fact(5) = " + fact(5));
println("gcd(48, 18) = " + gcd(48, 18));
```

### Несколько модулей

```c
#include <math.mc>
#include <string.mc>
#include <array.mc>

let data = [42, 17, 93, 8];

println("Сумма:    " + sum(data, 4));
println("Максимум: " + maxOf(data, 4));
println(repeat("*", 30));
```

### Свой модуль

Создай файл `myutils.mc`:

```c
#pragma once

function double(int x) {
    return x * 2;
}

function triple(int x) {
    return x * 3;
}
```

Использование:

```c
#include "myutils.mc"

println(double(5));   // 10
println(triple(5));   // 15
```

---

## Макросы

### Простой #define

```c
#define PI 3
#define MAX 100
#define GREETING "Привет"

println(GREETING);
println("PI = " + PI);
println("MAX = " + MAX);
```

### Макрос с параметрами

```c
#define SQUARE(x) ((x) * (x))
#define CUBE(x) ((x) * (x) * (x))
#define DOUBLE(x) ((x) + (x))

println("SQUARE(5) = " + SQUARE(5));
println("CUBE(3) = " + CUBE(3));
println("DOUBLE(10) = " + DOUBLE(10));
```

### Комбинация define + include

```c
#include <math.mc>

#define LIMIT 20

print("Простые до " + LIMIT + ": ");
for (let i = 2; i <= LIMIT; i++) {
    if (isPrime(i)) {
        print(i + " ");
    }
}
println();
```

---

## Время и дата

### Вывод

```c
println("Сейчас времени: " + time);
println("Сегодня:        " + date);
println("Полный момент:  " + datetime);
```

### Логирование с временем

```c
function log(String msg) {
    println("[" + time + "] " + msg);
}

log("Запуск приложения");
log("Подключение к базе");
log("Обработка запроса");
log("Завершение");
```

### Отчёт с датой

```c
println("════════════════════════════════");
println("  ОТЧЁТ");
println("  Создан: " + datetime);
println("════════════════════════════════");
println();
println("Содержимое...");
println();
println("Подпись: " + date);
```

---

## Генераторы

### Простой генератор

```c
function* counter(int n) {
    for (let i = 0; i < n; i++) {
        yield i;
    }
}

for (x in counter(5)) {
    println(x);
}
```

### Бесконечный генератор

```c
function* fibonacci() {
    let a = 0;
    let b = 1;

    while (true) {
        yield a;
        int t = a + b;
        a = b;
        b = t;
    }
}

let count = 0;

for (x in fibonacci()) {
    if (count >= 10) { break; }
    print(x + " ");
    count++;
}
println();
```

### Генератор с диапазоном

```c
function* range(int start, int end) {
    let i = start;
    while (i < end) {
        yield i;
        i++;
    }
}

for (x in range(5, 10)) {
    println(x);  // 5, 6, 7, 8, 9
}
```

---

## Комплексные примеры

### Банкомат

```c
struct Account {
    String owner;
    int balance;
    int dailyLimit;
    int withdrawnToday;

    int withdraw(int amount) {
        if (amount <= 0) {
            throw "Сумма должна быть положительной";
        }
        if (amount > this.balance) {
            throw "Недостаточно средств";
        }
        if (this.withdrawnToday + amount > this.dailyLimit) {
            throw "Превышен дневной лимит";
        }
        this.balance -= amount;
        this.withdrawnToday += amount;
        return this.balance;
    }

    int deposit(int amount) {
        if (amount <= 0) {
            throw "Сумма должна быть положительной";
        }
        this.balance += amount;
        return this.balance;
    }

    String info() {
        return this.owner + ": " + this.balance + "₽";
    }
}

Account acc = Account("Иван", 10000, 5000, 0);
println(acc.info());

try {
    acc.withdraw(2000);
    println("После снятия: " + acc.info());

    acc.deposit(500);
    println("После депозита: " + acc.info());

    acc.withdraw(4000);
} catch (e) {
    println("Ошибка: " + e);
}
```

### Todo-лист

```c
struct Task {
    int id;
    String title;
    bool done;

    String show() {
        if (this.done) {
            return "✓ [" + this.id + "] " + this.title;
        }
        return "○ [" + this.id + "] " + this.title;
    }
}

Task tasks[10];
int count = 0;

function add(String title) {
    tasks[count] = Task(count + 1, title, false);
    count++;
}

function complete(int id) {
    for (let i = 0; i < count; i++) {
        if (tasks[i].id == id) {
            tasks[i].done = true;
            return;
        }
    }
}

add("Купить хлеб");
add("Позвонить маме");
add("Написать код");
add("Погулять");

complete(1);
complete(3);

println("Список задач:");
for (let i = 0; i < count; i++) {
    println("  " + tasks[i].show());
}
```

### Игра «Угадай число»

```c
const int SECRET = 73;
const int MAX_TRIES = 10;

function hint(int guess) {
    if (guess == SECRET) { return "🎉 ПОБЕДА!"; }
    if (guess < SECRET) { return "загаданное БОЛЬШЕ"; }
    return "загаданное МЕНЬШЕ";
}

let guesses[10] = [50, 75, 60, 80, 70, 73, 0, 0, 0, 0];

println("Угадай число от 1 до 100");
println();

try {
    for (let i = 0; i < 10; i++) {
        println("Попытка " + (i + 1) + ": " + guesses[i]);
        String h = hint(guesses[i]);
        println("  → " + h);

        if (guesses[i] == SECRET) {
            throw "Угадал с " + (i + 1) + " попытки!";
        }
    }
} catch (e) {
    println();
    println(e);
}
```

### Стек

```c
struct Stack {
    int data[10];
    int top;

    void push(int v) {
        if (this.top >= 10) {
            throw "Стек полон";
        }
        this.data[this.top] = v;
        this.top++;
    }

    int pop() {
        if (this.top == 0) {
            throw "Стек пуст";
        }
        this.top--;
        return this.data[this.top];
    }

    int size() { return this.top; }
}

Stack s = Stack([0,0,0,0,0,0,0,0,0,0], 0);
s.push(10);
s.push(20);
s.push(30);
s.push(40);

println("Размер: " + s.size());
println("pop: " + s.pop());
println("pop: " + s.pop());
println("Размер: " + s.size());
```

### Игра «Жизнь»

```c
const int N = 8;
let grid[64];
let next[64];

function init() {
    for (let i = 0; i < 64; i++) {
        grid[i] = 0;
        next[i] = 0;
    }
}

function setCell(int r, int c, int v) {
    if (r < 0 || r >= N || c < 0 || c >= N) { return; }
    grid[r * N + c] = v;
}

function getCell(int r, int c) {
    if (r < 0 || r >= N || c < 0 || c >= N) { return 0; }
    return grid[r * N + c];
}

function show() {
    for (let i = 0; i < N; i++) {
        for (let j = 0; j < N; j++) {
            if (getCell(i, j) == 1) { print("█"); }
            else { print("·"); }
        }
        println();
    }
}

function neighbors(int r, int c) {
    int count = 0;
    for (let dr = -1; dr <= 1; dr++) {
        for (let dc = -1; dc <= 1; dc++) {
            if (dr == 0 && dc == 0) { continue; }
            count += getCell(r + dr, c + dc);
        }
    }
    return count;
}

function step() {
    for (let i = 0; i < N; i++) {
        for (let j = 0; j < N; j++) {
            int n = neighbors(i, j);
            int cur = getCell(i, j);
            if (cur == 1) {
                if (n == 2 || n == 3) { next[i * N + j] = 1; }
                else { next[i * N + j] = 0; }
            } else {
                if (n == 3) { next[i * N + j] = 1; }
                else { next[i * N + j] = 0; }
            }
        }
    }
    for (let i = 0; i < 64; i++) { grid[i] = next[i]; }
}

function countAlive() {
    int c = 0;
    for (let i = 0; i < 64; i++) {
        if (grid[i] == 1) { c++; }
    }
    return c;
}

init();

setCell(1, 2, 1);
setCell(2, 3, 1);
setCell(3, 1, 1);
setCell(3, 2, 1);
setCell(3, 3, 1);

println("Поколение 0 (живых: " + countAlive() + "):");
show();

for (let gen = 1; gen <= 3; gen++) {
    step();
    println();
    println("Поколение " + gen + " (живых: " + countAlive() + "):");
    show();
}
```

**Нашли ошибку или хотите добавить пример?** — [откройте Issue](../../issues/new) или присылайте pull request.
