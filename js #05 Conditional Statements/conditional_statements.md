
## 7. Conditional Statements


## 1. If else

```javascript
function greet(age) {
  if (age >= 18) {
    console.log('Hello!');
  } else if (age > 7) {
    console.log('Hi!');
  } else if (age > 3) {
    console.log('Hi, kid!');
  } else {
    console.log('Hi, toddler!');
  }
}

greet(25); // `Hello!` в консолі, перша умова вірна
greet(15); // `Hi!` в консолі, друга умова вірна
greet(6); // `Hi, kid!` в консолі, третя умова вірна
greet(2); // жодна умова не вірна, `Hi, toddler!` в консолі
```

- `if` - виконується, тільки якщо умова вірна;
- `else if` - якщо є кілька умов, крім `if`;
- `else` - можна додати, якщо не виконається жодна з попередніх умов;


## 2. Conditional operator

```javascript
age = 25;
// (умова) ? 'якщо умова True' : 'якщо умова False';
return (age < 18) ? 'Child' : 'Adult';
```


## 3. Checking multiple conditions (`&&` , `||`)

```javascript
if (age >= 18 && isPresent) {
  console.log('Hello!');
}
```

```javascript
// якщо вираз довгий, можна переносити
const result = (age >= 18)
  ? 'Adult'
  : 'Not Adult';
```

#### Ключове слово `return` всередині `if`, для повернення значення

```javascript
function getGreeting(age) {
  if (age >= 18) {
    return 'Hello!';
  } else if (age > 7) {
    return 'Hi!';
  } else if (age > 3) {
    return 'Hi, kid!';
  } else {
    return 'Hi, toddler!';
  }
}

let greeting = getGreeting(6);

console.log(greeting); // `Hi, kid!` в консолі
```
