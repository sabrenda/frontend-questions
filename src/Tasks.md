<div align="center"><h1>📋 Задачи по JavaScript</h1></div>

[⚙️ Back to menu](../README.md)


 <div id="menutasks"></div>

| No.|             Вопрос                   |
|:---|:-------------------------------------|
|1| [Палиндром](#js1)|
|2| [FizzBuzz](#js2)|
|3| [Анаграмма](#js3)|
|4| [Поиск гласных](#js4)|
|5| [Факториал](#js5)|
|6| [Фибоначчи](#js6)|
|7| [Как убрать дубли из массива (массив с примитивами)](#js7)|
|8| [Что вернет функция (hoisting)](#js8)|
|9| [Что выведет console.log (hoisting)](#js9)|
|10| [задачка на Замыкание](#js10)|
|11| [задачка на Контекст](#js11)|
|12| [задачка на "Привязка контекста"](#js12)|
|13| [реализовать функцию 'Rest params'](#js13)|
|14| [реализовать функцию 'Каррирование'](#js14)|
|15| [реализовать  `EventEmitter`](#js15)|
|16| [Асинхронность](#js16)|
|17| [реализовать Promise.all()](#js17)|
|18| [реализовать Promise.race()](#js18)|
|19| [реализовать Promise.allSettled()](#js19)|
|20| [реализовать Promise.any()](#js20)|


---

<div id="js1"></div>

## 1. Палиндром

Палиндром — слово, предложение или последовательность символов, которая абсолютно одинаково читается как в привычном направлении, так и в обратном. К примеру, “Anna” — это палиндром, а “table” и “John” — нет.

Постановка Дана строка; нужно написать функцию, которая позволяет вернуть значение true, если строка является палиндромом, и false — если нет. При этом нужно учитывать пробелы и знаки препинания.

решение:

```js
let  isPalindrome = function(str) {
  str = str.toLowerCase();

  return  str === str.split('').reverse().join('')
};
```

[Оглавление - Задачи 🔼](#menutasks)

<div id="js2"></div>

## 2. FizzBuzz

Требуется написать функцию, выводящую в консоль числа от 1 до n, где n — это
целое число, которая функция принимает в качестве параметра, с такими
условиями:

- вывод fizz вместо чисел, кратных 3;
- вывод buzz вместо чисел, кратных 5;
- вывод fizzbuzz вместо чисел, кратных как 3, так и 5.
```javascript
var fizzBuzz = function(n) {
    const arr = [];

    for(let count = 1; count <= n+1; count++)
    {
        if (count % 3 === 0 && count % 5 === 0)
          arr.push("FizzBuzz");
        else if (count % 3 === 0)
          arr.push("Fizz");
        else if (count % 5 === 0)
          arr.push("Buzz");
        else
          arr.push(count+"");
    }
    return arr;
};
```

[Оглавление - Задачи 🔼](#menutasks)

<div id="js3"></div>

## 3. Анаграмма

Постановка Нужно написать функцию, которая проверяет, являются ли две строки анаграммами, причем регистр букв не имеет значения. Учитываются лишь символы; пробелы или знаки препинания в расчет не берутся.

```js
var isAnagram = function(str1, str2) {
  return str1.toLowerCase().split('').sort().join('')
	  === str2.toLowerCase().split('').sort().join('')
};
```

[Оглавление - Задачи 🔼](#menutasks)



<div id="js4"></div>

## 4. Поиск гласных


Нужно написать функцию, принимающую строку в качестве аргумента и
возвращающую количество гласных, которые содержатся в строке.
Гласными являются «a», «e», «i», «o», «u».

решение:
```js
function getCount(str) {
  const arr = ['a', "e", "i", "o", "u"]
  let count = 0;
  str.split('').forEach(el => {
    if (arr.includes(el))
      count++;
  })
  return count;
}
```
---

либо регулярным выражением:
```js
function getCount(str) {
  return (str.match(/[aeiou]/g) || []).length
}
```
1.  `str.match(/[aeiou]/g)`: `match` — это метод JavaScript для строк, который ищет соответствия между строкой и регулярным выражением. В данном случае регулярное выражение — это `[aeiou]`, которое соответствует любой гласной букве (a, e, i, o, u). Флаг `g` означает, что поиск будет продолжаться после первого найденного совпадения, поэтому этот метод вернет массив всех гласных букв в строке `str`.
2.  `|| []`: оператор `||` в JavaScript возвращает первое "истинное" значение. Если в строке `str` нет гласных букв, то `str.match(/[aeiou]/g)` вернет `null`. В этом случае оператор `||` вернет пустой массив `[]`, чтобы избежать ошибки при попытке получить длину `null`.
3.  `.length`: это свойство JavaScript для массивов, которое возвращает количество элементов в массиве. В этом контексте оно возвращает количество гласных букв в строке `str`.

Таким образом, эта функция возвращает количество гласных букв в строке `str`. Если в строке нет гласных, функция вернет 0.

---
либо такое решение:
```js
const getCount = str => str.replace(/[^aeiou]/g, '').length;
```

1.  `str.replace(/[^aeiou]/g, '')`: `replace` — это метод JavaScript для строк, который заменяет части строки, соответствующие заданному шаблону, на новую подстроку. В данном случае шаблон — это регулярное выражение `/[^aeiou]/g`, которое соответствует любому символу, который не является гласной буквой (a, e, i, o, u). Флаг `g` означает, что замена будет применена ко всем символам в строке, а не только к первому совпадению. Второй аргумент для `replace` — это строка, на которую заменяются найденные совпадения — в данном случае, это пустая строка `''`. Это означает, что все не-гласные буквы будут удалены из строки.

2.  `.length`: как и в предыдущем примере, это свойство JavaScript для строк, которое возвращает длину строки. После замены все символы, которые не являются гласными буквами, удаляются, поэтому длина результирующей строки равна количеству гласных букв в исходной строке.


Таким образом, эта функция также возвращает количество гласных букв в строке `str`. Если в строке нет гласных, функция вернет 0.

[Оглавление - Задачи 🔼](#menutasks)

<div id="js5"></div>

## 5. Факториал

итеративное решение:
```js
function factorial(n){
  if (n === 1 || n === 0)
    return 1;
  let count = 1;

  while(n)
    count *= n--

  return count;
}
```
рекурсвивное решение:
```js
const factorial = n => {
  if (n === 1 || n === 0)
    return 1;
  return n * (factorial(n - 1));
};
```
[Оглавление - Задачи 🔼](#menutasks)

<div id="js6"></div>

## 6. Фибоначчи

Классическая задача, которую можно встретить на собеседованиях самого разного уровня. Стоит напомнить, что последовательность Фибоначчи — это ряд чисел, где каждое последующее является суммой двух предыдущих. Так, первые десять чисел выглядят следующим образом: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34.

рекурсивное
```js
const fibonacci = n => {
  if (n <= 2)
    return 1;
  return fibonacci(n - 1) + fibonacci(n - 2)
};
```

[Оглавление - Задачи 🔼](#menutasks)

<div id="js7"></div>

## 7. Как убрать дубли из массива (массив с примитивами)

Один из самых простых способов удаления дубликатов из массива в JavaScript - использовать структуру данных `Set`. `Set` - это встроенный объект в JavaScript, который хранит только уникальные значения.

Вот как вы можете это сделать:

```javascript
let array = [1, 2, 2, 3, 4, 4, 5, 5]; // Ваш исходный массив
let uniqueArray = [...new Set(array)]; // Удаление дубликатов
console.log(uniqueArray); // [1, 2, 3, 4, 5]
```

В этом примере вы создаете новый `Set` из исходного массива, который автоматически удалит все дубликаты, так как `Set` может содержать только уникальные значения. Затем вы используете оператор распространения `...` для преобразования `Set` обратно в массив.

Этот подход будет работать для массивов примитивных типов данных, таких как числа и строки. Однако, если в вашем массиве есть объекты, `Set` будет считать разные объекты уникальными, даже если они содержат одинаковые данные, так как они - это разные объекты в памяти.

---
либо использовать `filter`

```js
let array = [1, 2, 2, 3, 4, 4, 5, 5]; // Ваш исходный массив

let uniqueArray = array.filter((value, index, self) => {
    return self.indexOf(value) === index;
});

console.log(uniqueArray); // [1, 2, 3, 4, 5]
```

[Оглавление - Задачи 🔼](#menutasks)

<div id="js8"></div>

## 8. Что вернет функция (hoisting)
Что вернет функция ниже:
```js
var a = 5

function f() {
    if (a) {
        console.log(a)
        var a = 10
    }
}
f()
```

Код выведет `undefined`.

Причина этого в том, что JavaScript использует механизм поднятия переменных, известный как "hoisting". Это означает, что объявление переменной `var a` в функции `f()` поднимается наверх этой функции. В результате, внутри функции `f()`, `a` сначала объявляется (но еще не определено значение), и только после этого происходит проверка `if (a)` и `console.log(a)`.

Ваш код после hoisting выглядит примерно так:

```javascript
var a = 5;

function f() {
    var a;  // a = undefined здесь
    if (a) {
        console.log(a);
        a = 10;
    }
}

f();
```

Таким образом, когда `console.log(a)` выполняется внутри функции `f()`, `a` уже было объявлено в этой функции, но еще не было присвоено значение, поэтому оно `undefined`.

Обратите внимание, что поведение с `let` и `const` будет отличаться, так как они имеют блочную область видимости и не подвержены hoisting в том же смысле, что и `var`.

[Оглавление - Задачи 🔼](#menutasks)

<div id="js9"></div>

## 9. Что выведет console.log (hoisting)
Что вернет функция ниже:
```js
console.log(a)
var a = 5;

console.log(b)
let b = 2;
```
В JavaScript существуют два ключевых понятия, которые объясняют разницу в поведении этих двух блоков кода: поднятие (hoisting) и блочная область видимости.

1. `var`:

```javascript
console.log(a) // Выведет: undefined
var a = 5;
```

В этом случае `a` объявляется с помощью `var`. В JavaScript переменные, объявленные с помощью `var`, поднимаются в начало их области видимости. Это означает, что объявление переменной `var a` перемещается в начало области видимости (в этом случае — в начало глобальной области видимости). Но присвоение значения `5` остается на том же месте, поэтому когда мы вызываем `console.log(a)`, переменная `a` уже объявлена, но еще не инициализирована, поэтому вывод будет `undefined`.

2. `let`:

```javascript
console.log(b) // Ошибка: b is not defined
let b = 2;
```

Здесь `b` объявляется с помощью `let`. В JavaScript `let` и `const` имеют блочную область видимости и не поднимаются. Это означает, что переменная `b` не существует до того момента, когда доходит до строки `let b = 2`. Поэтому при попытке использовать `b` до его объявления вы получите ошибку: `ReferenceError: b is not defined`.

[Оглавление - Задачи 🔼](#menutasks)

<div id="js10"></div>

## 10. задачка на Замыкание

исправьте код ниже, чтобы замыкание работало:
```js
function makeCounter() {
  let count = 0;

  return function() {
    return count++;
  };
}

inc(); // 1
inc(); // 2
```
ответ:
```js
function makeCounter() {
  let count = 0;

  return function() {
    return ++count;
  };
}

let inc = makeCounter();

console.log(inc()); // 1
console.log(inc()); // 2
```

[Оглавление - Задачи 🔼](#menutasks)

<div id="js11"></div>

## 11. задачка на Контекст

исправьте код
```js
const obj = {
    a: 42,
    say: function () {
        setTimeout(function () {
            console.log(this.a)
        }, 1000)
    }
}

obj.say()
```
ответ:

В данном коде есть проблема, связанная с контекстом `this` в JavaScript. Когда вы вызываете `obj.say()`, `this` внутри метода `say` действительно ссылается на объект `obj`. Но когда вы входите в функцию `setTimeout`, контекст `this` меняется.

Внутри функции `setTimeout` (и любой другой функции, которая не является стрелочной), `this` обычно ссылается на глобальный объект (в браузерах это `window`). Поскольку в глобальном объекте нет свойства `a`, выражение `this.a` вернет `undefined`.

Чтобы исправить эту проблему, вы можете использовать стрелочную функцию, которая не имеет собственного `this` и берет его из окружающего лексического контекста:
```js
const obj = {
    a: 42,
    say: function () {
        setTimeout(() => {
            console.log(this.a);
        }, 1000);
    }
};

obj.say(); // Выведет: 42

```

[Оглавление - Задачи 🔼](#menutasks)

<div id="js12"></div>

## 12. задачка "Привязка контекста"

```js
const ex = (value, sum) => console.log(sum + value)
const fx = ex.bind(null, 10);

ex(12, 7) // 19
fx(7, 12) // 17 (т.к привязали 10 к value)
```

---

исправленный вариант:

Для исправления данного кода и использования функции `fx` так, чтобы она корректно принимала и использовала входные аргументы, вы можете привязать только контекст к функции `ex`, а не контекст и аргументы. Давайте обновим код таким образом:

```javascript
const ex = (value, sum) => console.log(sum + value);
const fx = ex.bind(null);

ex(12, 7); // Выведет: 19, так как 12 + 7 = 19
fx(10, 7); // Выведет: 17, так как 10 + 7 = 17
```

Теперь вызов `fx(10, 7)` приведет к выводу `17`, что является ожидаемым поведением.

Тем не менее, если вам нужно привязать значение `10` к `value` и затем передать дополнительные аргументы в `fx`, вы можете использовать частичное применение функции, используя `bind` вместе с `null` в качестве контекста:

```javascript
const ex = (value, ...args) => console.log(args.reduce((a, b) => a + b, 0) + value);
const fx = ex.bind(null, 10);

ex(12, 7); // Выведет: 19, так как 12 + 7 = 19
fx(7, 12); // Выведет: 29, так как 10 (первый аргумент, привязанный через bind) + 7 + 12 = 29
```

В этом случае, функция `ex` теперь принимает неограниченное количество аргументов и складывает их все вместе с `value`. Функция `fx` затем привязывает `10` к `value` и принимает любое количество дополнительных аргументов.


[Оглавление - Задачи 🔼](#menutasks)

<div id="js13"></div>

## 13. реализовать функцию 'Rest params'
задача:

```js
multyplyTwo(1,2,3,4,5,6)  // [2,4,6,8,10,12]
```

ответ:
```js
function multyplyTwo(...args){
	return args.map(el => el * 2)
}

console.log(multiplyTwo(1,2,3,4,5,6)); // [2, 4, 6, 8, 10, 12]
```

В этом коде `...args` позволяет функции `multiplyTwo` принимать произвольное количество аргументов и собирать их в массив `args`. Затем `args.map(arg => arg * 2)` проходит по каждому элементу массива `args`, умножает его на два и возвращает новый массив с результатами.

[Оглавление - Задачи 🔼](#menutasks)

<div id="js14"></div>

## 14. реализовать функцию 'Каррирование'

задача:
```js
function sum() {

}

sum(3)(4)

// карирование
```

---

Каррирование — это процесс преобразования функции с несколькими аргументами в функцию, которая принимает один аргумент и возвращает функцию, которая принимает остальные аргументы.

решение:
```javascript
function sum(a) {
  return function(b) {
    return a + b;
  };
}

console.log(sum(3)(4)); // 7
```

Здесь функция `sum` принимает первый аргумент `a` и возвращает новую функцию, которая принимает второй аргумент `b`. Эта внутренняя функция затем возвращает сумму `a` и `b`. Когда вы вызываете `sum(3)(4)`, вы фактически вызываете внутреннюю функцию с `b` равным `4`, и `a` уже привязано к `3`, так что результатом будет `7`.

[Оглавление - Задачи 🔼](#menutasks)

<div id="js15"></div>

## 15. реализовать `EventEmitter`

```js
class EventEmitter {
  constructor() {
    this.events = {}; 
  }

  // Метод для подписки на событие
  on(event, listener) {
    if (!this.events[event]) {
      this.events[event] = [];
    }
    this.events[event].push(listener);
    return this;
  }

  // Метод для удаления подписчика
  off(event, listenerToRemove) {
    if (!this.events[event]) return;

    this.events[event] = this.events[event].filter(listener => listener !== listenerToRemove);
    return this;
  }

  // Метод для вызова всех слушателей определённого события
  emit(event, ...args) {
    if (!this.events[event]) return;

    this.events[event].forEach(listener => {
      listener(...args);  // Вызываем слушателя с переданными аргументами
    });
    return this;
  }

  // Подписка на событие с однократным вызовом
  once(event, listener) {
    const onceListener = (...args) => {
      listener(...args);
      this.off(event, onceListener);  // Удаляем слушателя после первого вызова
    };

    this.on(event, onceListener);
    return this;
  }
}
```


[Оглавление - Задачи 🔼](#menutasks)

<div id="js16"></div>

## 16. Асинхронность

```js
console.log(1);

setTimeout(() => console.log(2));

Promise.resolve().then(() => console. log(3));

Promise.resolve().then(() -> setTimeout(() => console.log(4)));

Promise.resolve(console.log(5)).then(() => console.log(6));

setTimeout(() => console.log(7));

console.log(8);
```

> [!NOTE]
>
> <details>
> <summary>Ответ</summary>
>   	
> // 1 5 8 3 6 2 7 4

[Оглавление - Задачи 🔼](#menutasks)

<div id="js17"></div>

## 17. реализовать Promise.all()

> [!NOTE]
>
> <details>
> <summary>ответ:</summary>
>   	
>   ```js
>    function myPromiseAll(promises) {
>      return new Promise((resolve, reject) => {
>        if (!Array.isArray(promises)) {
>          return reject(new TypeError('Argument must be an array'));
>        }
> 
>        const resultArray = [];
>        let completedPromises = 0;
> 
>        promises.forEach((promise, index) => {
>          Promise.resolve(promise)
>            .then((value) => {
>              resultArray[index] = value;
>              completedPromises++;
> 
>              if (completedPromises === promises.length) {
>                resolve(resultArray);
>              }
>            })
>            .catch((err) => {
>              reject(err);
>            });
>        });
> 
>        if (promises.length === 0) {
>          resolve([]);
>        }
>      });
>    }
>   ```
> 
> </details>

[Оглавление - Задачи 🔼](#menutasks)

<div id="js18"></div>

## 18. реализовать Promise.race()

> [!NOTE]
>   
> <details>
> <summary>ответ:</summary>
> 	
>   ```js
>    function myPromiseRace(promises) {
>      return new Promise((resolve, reject) => {
>        if (!Array.isArray(promises)) {
>          return reject(new TypeError('Argument must be an array'));
>        }
> 
>        for (let promise of promises) {
>          Promise.resolve(promise)
>            .then(resolve)
>            .catch(reject);
>        }
>      });
>    }
>   ```
> 
> </details>

[Оглавление - Задачи 🔼](#menutasks)

<div id="js19"></div>

## 19. реализовать Promise.allSettled()

> [!NOTE]
>   
> <details>
> <summary>ответ:</summary>
> 	
>   ```js
>    function myPromiseAllSettled(promises) {
>      return new Promise((resolve, reject) => {
>        if (!Array.isArray(promises)) {
>          return reject(new TypeError('Argument must be an array'));
>        }
> 
>        const results = [];
>        let completedPromises = 0;
> 
>        promises.forEach((promise, index) => {
>          Promise.resolve(promise)
>            .then((value) => {
>              results[index] = { status: 'fulfilled', value };
>            })
>            .catch((reason) => {
>              results[index] = { status: 'rejected', reason };
>            })
>            .finally(() => {
>              completedPromises++;
>              if (completedPromises === promises.length) {
>                resolve(results);
>              }
>            });
>        });
> 
>        if (promises.length === 0) {
>          resolve([]);
>        }
>      });
>    }
>   ```
> 
> </details>

6. **`Promise.any(iterable)`**

[Оглавление - Задачи 🔼](#menutasks)

<div id="js20"></div>

## 20. реализовать Promise.any()

> [!NOTE]
>   
> <details>
> <summary>ответ:</summary>
> 	
>   ```js
>    function myPromiseAny(promises) {
>      return new Promise((resolve, reject) => {
>        if (!Array.isArray(promises)) {
>          return reject(new TypeError('Argument must be an array'));
>        }
> 
>        let rejections = [];
>        let rejectedCount = 0;
> 
>        promises.forEach((promise, index) => {
>          Promise.resolve(promise)
>            .then(resolve)
>            .catch((error) => {
>              rejections[index] = error;
>              rejectedCount++;
> 
>              if (rejectedCount === promises.length) {
>                reject(new AggregateError(rejections, 'All promises were rejected'));
>              }
>            });
>        });
> 
>        if (promises.length === 0) {
>          reject(new AggregateError([], 'No promises were passed'));
>        }
>      });
>    }
> ```
> 
> </details>

[Оглавление - Задачи 🔼](#menutasks)

