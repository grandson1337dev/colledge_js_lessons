## Arrays (Масиви)

- **Створення масива**
```javascript
let cities = ['Kyiv', 'London', 'Paris'];
console.log(cities); // ['Kyiv', 'London', 'Paris']
```
- **Кортеж (tuple)** - масив з різними типами
```javascript
let person = ['John', 25, false];
```
- **Довжина масива**
```javascript
let cities = ['Kyiv', 'London', 'Paris'];
console.log(cities.length); // 3
```
- **Отримання елемента за індексом**
```javascript
let cities = ['Kyiv', 'London', 'Paris'];
console.log(cities[0]); // Kyiv
console.log(cities[1]); // London
console.log(cities[cities.length - 1]); // останній елемент // Paris
```
- **Заміна елемента за індексом**
```javascript
let cities = ['Kyiv', 'London', 'Paris'];
cities[2] = 'New York';
console.log(cities); // в консолі - ['Kyiv', 'London', 'New York']
```
- **Додати елемент до кінця масиву**
```javascript
let cities = ['Kyiv', 'London', 'Paris'];
cities[cities.length] = 'New York'; // довжина = новий елемент масиву
console.log(cities); // в консоли - ['Kyiv', 'London', 'Paris', 'New York']
```
**але правильніше додати через** `push()`
```javascript
let cities = ['Kyiv', 'London', 'Paris'];
cities.push('Amsterdam', 'New York'); // push() додає всі елементи в кінець
console.log(cities); // в консолі - ['Kyiv', 'London', 'Paris', 'Amsterdam', 'New York']
```

#### Робота з масивами рядків

- `split()` - **розрізає рядок за вказаним роздільником**

```javascript
const text = 'one two three four five'

// не додали роздільник - розіб'є на всі символи рядка
const chars = text.split('');
console.log(chars); // ['o', 'n', 'e', ...]

// поставили як роздільник пробіл - розіб'є через пробіл слова
const words = text.split(' ');
console.log(words); // ['one', 'two', 'three', ...]

// роздільником може виступати рядок
const text = 'one two three four five';
const words = text.split(' f');

console.log(words); // ['one two three', 'our', 'ive']
```

- `join()` - **об'єднання елементів масиву в рядок**

```javascript
const fruits = ['apple', 'banana', 'cherry', 'date'];
const joinedString = fruits.join(', '); // роздільник - кома та пробіл

console.log(joinedString); // у консоль виведеться рядок 'apple, banana, cherry, date'
```

#### Пошук елемента масиву

```javascript
const words = ['apple', 'banana', 'cherry', 'date'];

// використовуємо метод .includes() для пошуку елемента в масиві
console.log(words.includes('apple')); // true

// використовуємо метод .indexOf() для пошуку індексу, з якого починається елемент
console.log(words.indexOf('apple'));// 0
```
