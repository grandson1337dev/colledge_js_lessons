
# Loops (цикли)

 
## 1. Цикл for

```javascript
for (let age = 1; age <= 5; age = age + 1) { 
  console.log(`I am ${age}`);
}
```
- початкова команда `let age = 1`, яка виконується один раз перед початком циклу
- умова `age <= 5`, яка перевіряється перед кожною ітерацією циклу
- команда `age = age + 1`, яка виконується після кожної ітерації циклу

## 2. Скорочення присвоєння

```javascript
age -= 5; // age = age - 5;
age *= 5; // age = age * 5;
age /= 5; // age = age / 5;
age %= 5; // age = age % 5;
age++; // age += 1; // ++ називається інеремент
age--; // age -= 1; // -- називається декремент
```

## 3. Перебір символів у зворотному напрямку

```javascript
for (let i = 3; i > 0; i--) {
  console.log(i);
}
```

## 4. Приклад суми чисел з кроком (за допомогою циклу функції)

```javascript
function sumFromTo(min, max, step) {
  let sum = 0;

  for (let n = min; n <= max; n += step) {
    sum += n;
  }

  return sum;
}

console.log(
  sumFromTo(1, 5, 2) // 9
);
```

## 5. break & continue

- `break` - дозволяє в будь-який момент вийти з циклу, навіть якщо умова досі істинна. Після цієї команди виконання циклу повністю переривається, і починає виконуватись код, наступний після циклу:

```javascript
for (let i = 2; i > 1; i++) {
  if (i === 9) {
    break;
  }
  console.log(i);
}
```
Тепер, як тільки `i` буде дорівнювати `9`, цикл закінчиться. Значення `9` навіть не надрукується у консолі.

- `continue` - перейти до наступної ітерації циклу, не виконуючи команди, що стоять у тілі циклу.

```javascript
for (let i = 1; i <= 10; i++) {
  if (i % 2 !== 0) {
    continue;
  }
  console.log('Even number');

  if (i === 4) {
    console.log(i);
  }
}
```

## 6. while & do while

- `while` - коли не знаємо наперед, скільки разів потрібно виконати ту чи іншу команду. Наприклад, при розкладанні числа на дільники чи пошуку залишку; `while` буде виконуватися, поки його умова істинна.

```javascript
let value = 22;

while (value >= 5) {
  value -= 5; // 17, 12, 7, 2
}

console.log(value); // 2
```

- `do while` - якщо необхідно перевіряти умову після першої ітерації (а не до); він подібний до циклу `while`, але перевіряє умову вже після виконання тіла циклу.

```javascript
let i = 7;

do {
  console.log(i);
  i++;
} while (i < 3);
```

- `while(true)` - нескінченний цикл, поки умова істинна.

```javascript
while (true) {
  let n = Math.random();

  if (n < 0.9) {
    break;
  }

  console.log(n);
}
```
І тепер не важливо, де стоїть `while`, на початку чи наприкінці, вихід із циклу відбудеться лише якщо спрацює `break`.


## 7. switch

Іноді у програмі необхідно виконати різні дії залежно від певного значення. Це можна зробити за допомогою блоків `else if`:

```javascript
const number = 2;

if (number === 1) {
  console.log('Number is 1');
} else if (number === 2) {
  console.log('Number is 2'); // у консолі побачимо 'Number is 2'
} else if (number === 3) {
  console.log('Number is 3');
} else {
  console.log('Other number');
}
```


У такому разі кожен `if` може містити більше однієї умови або щось інше ніж `===`. Тому, читаючи цей код, ми повинні уважно перевіряти кожну умову, щоб правильно зрозуміти, як це працює.

Якщо ж така гнучкість нам не потрібна, і ми тільки перевіряємо точне значення будь-якої змінної або виразу, можна використовувати конструкцію `switch`, яка завжди перевіряє строгу рівність.

```javascript
const number = 2;

switch (number) {
  case 1:
    console.log('Number is 1');
    break;

  case 2:
    console.log('Number is 2'); // у консолі побачимо 'Number is 2'
    break;

  case 3:
    console.log('Number is 3');
    break;

  default:
    console.log('Other number');
}
```

- Як `switch` працює: 
- ми обчислюємо значення виразу в дужках `()` після оператора `switch`; 
- потім ми порівнюємо його зі значенням, записаним після першого `case`; 
- якщо ці значення рівні, ми виконуємо всі команди з цього `case` у ключове слово `break` і виходимо з `switch`; 
- якщо ні, ми перевіряємо значення наступного `case`; 
- якщо значення не співпало з жодним `case`, ми виконуємо всі команди з блоку `default` і виходимо з `switch`.

- використання `case` без `break`
Іноді зручно об'єднати кілька "case" разом. Для цього між ними не ставлять 'break'. Тоді виконуються всі команди після `case`, які підійшли за умовою і до найближчого `break` або до завершення `switch`:

```javascript
case 1:
  // ...
  break;

case 2:
case 3: 
case 4: 
  // ...
  break;
  
default:
  // ...
```

- Використання `switch` разом з `return`
Якщо використовується `switch` всередині функції, то в `case` можна написати `return` замість `break`. Тоді функція повертатиме значення з 'case', а команди після 'return' не виконуватимуться:

```javascript
const number = 2;

function printMessage(number) {
  switch (number) {
    case 1:
      return 'Number is 1';

    case 2:
      return 'Number is 2'; // функція поверне 'Number is 2'

    case 3:
      return 'Number is 3';

    default:
      return 'Other number';
   }
}

console.log(printMessage(number)); // 'Number is 2'
```

Приклад із кількома аргументами:
```javascript
function findCalculationType(a, b, res) {
  switch (res) {
    case a + b:
      return 'addition';

    case a - b:
      return 'subtraction';

    case a * b:
      return 'multiplication';

    case a / b:
      return 'division';
  }
}
```

Якщо `switch` ми хочемо перевірити довільні умови, а не точне змінне значення, можна використовувати `switch (true)`:
```javascript
function getWord(count) {
  switch (true) {
    case count <= 4:
      return 'a few';
  
    case count < 10:
      return 'several';

    default:
      return 'a lot';
  }
}
```
Але такий синтаксис може заплутати, тому в такій ситуації краще використовувати блоки `if else`.
