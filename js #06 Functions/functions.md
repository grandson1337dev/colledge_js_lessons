# Functions


## 1. Basics

```javascript
function calculateArea(length, width) {
  let area = length * width;

  console.log(area);
}

calculateArea(3, 5); // запуск функції з параметрами // 15 в консолі
calculateArea(3); // NaN в консолі, оскільки другий параметр не вказано (undefined)
calculateArea(3, 'true'); // NaN в консолі
calculateArea(3, true); // 3 в консолі (true = 1)
calculateArea(3, false); // 0 в консолі (false = 0)
```
- `function` - виклик функції
- `calculateArea()` - ім'я функції
- *length, width* - параметри функції
- команди у фігурних дужках `{...}` - тіло функції

#### `return` - повернення значення
```javascript
function calculateArea(length, width = 1.5) {
  return length * width;
}
let totalArea = 10 * calculateArea(2, 5);
console.log(totalArea); // 100 в консолі
console.log(calculateArea(2)); // 3 в консолі
```
якщо у функції немає `return` або у `return` немає значення - результат функції буде `undefined`


## 2. Параметри за замовчуванням та додаткові аргументи

- Значення параметрів **за замовчуванням**
```javascript
function calculateArea(length, width = 1.5) { // width задано значення за замовчуванням
  let area = length * width;
  console.log(area);
}
calculateArea(3, 5) // 15 в консолі (задано обидва параметри)
calculateArea(3) // 4.5 в консолі (3 * 1.5)
```

- Якщо у функцію **передано більше аргументів**, ніж вона очікує, то **зайві аргументи просто ігноруються**:
```javascript
function multiply(a, b) {
  return a * b;
}
multiply(3, 4, 5, 6); // поверне `12`, аргументи`5` та `6` ігноруються
```

- **rest** оператор `...args`
Якщо потрібно отримати всі аргументи, що передаються, можна використовувати оператор **rest**, наприклад `...args`. В цьому випадку `...args` буде масивом, що містить усі аргументи, передані у функцію:
```javascript
function sum(...args) {
  console.log(args);
}
sum(3, 4); // args = [3, 4]
sum(3, 4, 5, 6); // args = [3, 4, 5, 6]
```

Також при необхідності можна отримати частину аргументів до окремих параметрів, а решту зібрати до масиву.:
```javascript
function sum(x, ...args) {
  console.log(x, args);
}
sum(); // x = undefined, args = []
sum(1, 2); // x = 1, args = [2]
sum(3, 4, 5, 6); // x = 3, args = [4, 5, 6]
```


## 3. Function Declaration & Function Expression

- Функції можна викликати як до, так і після оголошення:
```javascript
const result1 = sum(1, 2);
// пишемо функцію після виклику:
function sum(a, b) {
  return a + b;
}
// а тут викликаємо після оголошення:
const result2 = sum(3, 4);
```

- Іноді буває зручно присвоїти функцію до змінної:
```javascript
const operation = function sum(a, b) {
  return a + b;
};
const result = operation(1, 2); // result = 3
```
Таке створення функції називається **функціональним виразом** (Function Expression). Її можна викликати лише після присвоєння, і лише на ім'я змінної, куди вона присвоєна.


## 4. Arrow Function =>

- **Для максимального скорочення** можна використовувати `=>` після круглих дужок замість `function` перед ними:
```javascript
const sum1 = function(a, b) {
  return a + b;
};
//тепер те саме, тільки стрілочною функцією:
const sum2 = (a, b) => {
  return a + b;
};
```

- **Якщо функція відразу повертає результат**, то `{}` і `return` можна прибрати та записати результат після стрілки:
```javascript
let sum = (a, b) => a + b;
```

- **Якщо параметр лише один**, його можна написати без дужок:
```javascript
let square = a => a * a;
```

- **Якщо параметрів немає**, круглі дужки все одно мають бути:
```javascript
let sum = () => 3 + 5;
```

- Так само, як і у звичайній функції, параметрам можна встановлювати **значення за замовчуванням** та використовувати **rest-оператор**:
```javascript
let f = (a, b = 10, ...args) => {
  console.log(a, b, args);
};
```
