# Boolean


```javascript
const a = 2;
console.log(
  a === 2, // true // сувора рівність
  a !== 2, // false // сувора нерівність
  a > 2, // false
  a < 2, // false
  a >= 2, // true
  a <= 2, // true
);
```

## 1. Логічні оператори ( `!` , `&&` , `||` )

- **Оператор заперечення** (`!`)
```javascript
const age = 25;
let isAdult = age >= 18;
console.log(isAdult); // true
console.log(!isAdult); // false
```

- **Логічне і** (`&&`)
```javascript
let cash = 50;
let price = 40;
let hasEnoughCash = cash >= price;
let age = 25;
let isAdult = age >= 18;
let canBuy = isAdult && hasEnoughCash; 
console.log(canBuy); // true
```
- `&&` - має більший пріоритет, ніж `||`:
```javascript
console.log(1 && 2 || 3 && 4); // 2
```
Спочатку ми перевіряємо `1 && 2`, результатом є `2`. Потім перевіряємо `3 && 4`, результатом є `4`. І нарешті, ми маємо `2 || 4`, тому результатом обчислення виразу є `2`.

- `&&` - повертає перший операнд, якщо він помилковий у логічному сенсі, інакше другий:
```javascript
console.log(1 && true); // true
console.log(1 && 2); // 2
console.log(0 && 1); // 0
console.log(1 && 0); // 0
console.log(1 && false); // false
console.log(0 && false); // 0
```
- При використанні кількох операторів `&&` підряд ми отримаємо перше хибне значення, або останнє, якщо хибних немає:
```javascript
console.log(1 && 2 && 3); // 3
console.log(1 && 2 && true); // true
console.log(1 && 0 && true); // 0
console.log(1 && false && true); // false
```

- **Логічне АБО** (`||`)
```javascript
console.log(10 || null); // 10
console.log(null || 10); // 10
console.log(0 || 1); // 1
console.log('' || undefined); // undefined
```
```javascript
let cash = 50;
let creditCard = 20;
let price = 40;
let hasEnoughCash = cash >= price;
let hasEnoughCredit = creditCard >= price;
let canBuy = hasEnoughCash || hasEnoughCredit; 
console.log(canBuy); // true
```
- `||` - повертає перше **TRUE (1)**
```javascript
console.log(1 || 0 || 2); // 1
console.log(false || 0 || 3); // 3
console.log(0 || 1 || false || 3); // 1
```

- На практиці можна використовувати для встановлення значення змінної за умовчанням:
```javascript
const user = currentUser || 'Unknown';
```
