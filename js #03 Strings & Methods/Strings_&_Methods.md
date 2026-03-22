
# Strings


## 1. Робота з рядками та елементами рядків

- `\` - екранування (деякі символи після слешу - не символи коду)
```javascript
const str = 'This is \' line';
console.log(str); // `This is ' line
console.log('There\'s a lot of loot');
```

- `\n` - перенесення на новий рядок або порожній рядок

- `\t` - додати табуляцію до рядка

- `length` - довжина рядка
```javascript
const name = 'Stanislav';
console.log(name.length); // 9
```

- **Символ в рядку** - `name[3]` - починається з 0
```javascript
const name = 'Stanislav';
console.log(name[3]); // n
```
#### *або нова функція `at`, `charAt`*:
```javascript
const name = 'Stanislav';
console.log(name.at(1)); // t
console.log(name.at(-2)); // a - передостанній з кінця
console.log(name.charAt(3)); // n
```
але `charAt` (на відміну від `at`) не вміє з кінця брати символи і поверне порожній рядок. Обидві функції повернуть порожній рядок, якщо потрібної позиції `name[99]` немає.

- Обчислити **індекс останнього символу**
```javascript
const name = 'Stanislav';
console.log(name[name.length - 1]); // v
```

- **Конкатенація** - об'єднання (склеювання) рядків за допомогою оператора `+`
```javascript
const name = 'Stanislav';
const lastName = 'Cherevko';
console.log(name[0] + lastName[0]); // SC
console.log('Mr. ' + name + ' ' + lastName); // Mr. Stanislav Cherevko
```
#### *конкатенація рядків та чисел:*
```javascript
console.log('12' + 34); // '1234'
console.log(12 + '34'); // '1234'
```

- **Інтерполяція** - вставка змінних/значень у рядок. Для цього використовується синтаксис `${...}` та зворотні лапки ```(` `)```
```javascript
const name = 'Stanislav';
const lastName = 'Cherevko';
console.log(`Mr. ${name} ${lastName}`); // Mr. Stanislav Cherevko
```


## 2. Ітерація рядків

#### *Перебір символів рядка за індексом, за допомогою циклу `for`*
```javascript
const title = 'String';

for (let i = 0; i < title.length; i++) {
  console.log(title[i]);
}
```
```javascript
// перебір у зворотному порядку
const title = 'String';

for (let i = title.length - 1; i >= 0; i--) {
  console.log(title[i]);
}
```

#### *Перебір за допомогою `for of` без індексу*
```javascript
const title = 'String';

// char - елемент рядка title
for (let char of title) {
  console.log(char);
}
```

#### *Заміна символів за допомогою циклу*
```javascript
let title = 'Working with Strings';
let result = ''; // створили порожній рядок для запису результату

for (let i = 0; i < title.length; i++) {
  if (title[i] === ' ') {
    result += '-';
  } else {
    result += title[i];
  }
}

console.log(result); 
```

#### *Та ж заміна символів за допомогою `for of` та функції*
```javascript
// приймаємо рядок, символ під заміну, символ на який міняємо
function replaceAll(input, char, replacement){
  let result = '';

  for (let ch of input) {
    if (ch === char){
      result += replacement;
    } else {
      result += ch;
    }
  }
 
  return result;
}

let title = 'Working with Strings';

console.log(
  replaceAll(title, ' ', '-')
);
```


## 3. Методи рядків

- `.toLowerCase()` `.toUpperCase()` - регістр тексту
```javascript
let phrase = 'Hello my world!';
console.log(phrase.toLowerCase()); // hello my world!
console.log(phrase.toUpperCase()); // HELLO MY WORLD!
```
- `.replace()` - заміна першого знайденого входження

- `.replaceAll()` - заміна ВСІХ входжень
```javascript
let phrase = 'Hello my world!';
// Чутливий до регістру!
console.log(phrase.replaceAll(' ', '-')); // Hello-my-world!
console.log(phrase.replaceAll('my', '**')); // Hello ** world!
```

- `.includes()` - пошук підрядка
```javascript
let phrase = 'Hello my world!';
// Чутливий до регістру!
console.log(phrase.includes(' ')); // true
console.log(phrase.includes('Hell')); // true
console.log(phrase.includes('hell')); // false
```

- `.indexOf()` - пошук індекса (або `.lastIndexOf()` з кінця)
```javascript
let phrase = 'Hello my world!';
// Чутливий до регістру!
console.log(phrase.indexOf(' ')); // 5
console.log(phrase.indexOf('my')); // 6
// Якщо нічого не знайдено – поверне -1
console.log(phrase.indexOf('mmm')); // -1
```

- `.trim()` - видалення всіх пробілів на початку і в кінці рядка
```javascript
const name = '       Stanislav     ';
console.log(name.trim()); // 'Stanislav'
```

- `.padStart()` - додає новий рядок на початок існуючого рядка. Синтаксис - `padStart(targetLength, padString)`, де `targetLength` - довжина рядка в результаті, а `padString` - рядок, який ми і додамо до існуючого рядка (значення за промовчанням - пробіл)
```javascript
const word = 'fruit';
console.log(word.padStart(10, '*')); // '*****fruit'
console.log(word.padStart(10, ' ')); // '     fruit'
console.log(word.padStart(10)); // '     fruit'
console.log(word.padStart(19, '0123456789')); // '01234567890123fruit'
```

- `.padEnd()` - те саме, що і `padStart`, тільки в кінець рядка

- `.repeat()` - метод, що повторює рядок вказану кількість разів
```javascript
const newString = 'John'.repeat(2);
console.log(newString); // 'JohnJohn'
```

- `.startsWith()` - чи починається рядок з певного підрядку (або закінчується - `.endsWith()`)

- `slice()` - метод для отримання частини рядка (підрядки). Він приймає 2 аргументи: 
- індекс, з якого починається копіювання символів; 
- індекс, на якому закінчується копіювання символів. Символ цього індексу не буде включений. Якщо не вказати символ закінчення – бере від зазначеного початку до кінця рядка.

```javascript
const text = '0123456789';
console.log(

// символ з індексом 5 не буде враховано
text.slice(1, 5), // '1234'

// беремо перші 8 символів
text.slice(0, 8), // '01234567'

// якщо початок більше кінця, отримуємо порожній рядок
text.slice(5, 1), // ''

// без аргументів отримуємо весь рядок
text.slice(), // '0123456789'

// якщо другий аргумент не передано, беремо все до кінця
text.slice(2), // '23456789'

// якщо індекс початку занадто великий, отримаємо порожній рядок
text.slice(15), // ''

// негативні індекси рахуються з кінця
text.slice(-5, -2), // '567'

// беремо останні 3 символи
text.slice(-3), // '789'

// всі символи, крім 0-го та останнього
text.slice(1, -1), // '12345678'
);
```

*Цей метод можна використовувати, щоб зібрати новий рядок із частин:*
```javascript
const text = 'I have 4 dogs';

// 'I have five dogs'
const text2 = text.slice(0, 7) + 'five' + text.slice(-5);

// 'We don't have dogs'
const text3 = `We don't ${text.slice(2, 6)} ${text.slice(-4)}`
```

#### *Змінити регістр можна лише для літер. Ця особливість дозволяє перевірити, чи є символ літерою.:*
```javascript
function isLetter(ch) {
  return ch.toLowerCase() !== ch.toUpperCase();
}

console.log(
  isLetter('a'), // true
  isLetter('B'), // true
  isLetter('1'), // false
  isLetter(','), // false
  isLetter(' '), // false
);
```

#### *Функція повернення кількості приголосних літер у рядку:*
```javascript
function countConsonants(input) {
  let count = 0;

  for (let i of input) {
    const isConsonant = 'bcdfghjklmnpqrstvwxz'.includes(i.toLowerCase());
    if (isConsonant) {
      count++;
    }
  }

  return count;
}
```

#### *Функція кількості літер у рядку (без символів):*

```javascript
function countLetters(input) {
  let count = 0;

  for (let i of input) {
    const ifLetter = i.toLowerCase() !== i.toUpperCase();

    if (ifLetter) {
      count++;
    }
  }

  return count;
}
```


## 4. Код символу та порівняння рядків

- Символ у рядок можна додати за кодом. Наприклад, символ "©" можна додати такими способами:
```javascript
console.log('\xA9');
console.log('\u00A9');
console.log('\u{A9}');
```

- `.charCodeAt()` - метод отримання коду символу. Параметром цей метод приймає індекс символу у рядку:
```javascript
'Apple'.charCodeAt(0) // `65` - это код `A`
```
можна навпаки, з коду отримати символ методом `.fromCharCode()`:
```javascript
String.fromCharCode(65); // 'A'
```

- 
У JavaScript рядки порівнюються посимвольно, а точніше за кодом символів. Порівнюючи рядки, слід враховувати низку особливостей: 
- малі (строчні) літери більше, ніж великі (прописні);
- спецсимволи та літери з діакритичними знаками, наприклад `Ö`, йдуть після основного алфавіту.

Щоб порівняти рядки з урахуванням особливостей алфавіту та регістру, існує метод `.localeCompare()`. Він має синтаксис `str1.localeCompare(str2)` і повертає число:
- негативне, якщо рядок `str1` менше `str2`;
- Позитивне, якщо рядок `str1` більше `str2`;
- `0`, якщо рядки дорівнюють.
```javascript
console.log('Ö' < 'Z'); // false
// АЛЕ...
console.log('Ö'.localeCompare('Z')); // -1
```


## 5. Перетворення Числа на Рядок і назад

- перетворення числа на рядок:
```javascript
const n = -123;
console.log(
	String(n), // '-123' - методом String()
	n.toString(), // '-123' - методом .toString()
	`${n}`, // '-123' - інтерполяцією
	'' + n, // '-123' - конкатенацією
);
```

- якщо потрібно з рядка в число, можна зробити **приведенням типів**:
```javascript
const digits = '123';
console.log(
	Number(digits), // 123 - методом Number
	+digits, // 123 - методом +
);
```
