# JavaScript Practice Notes

A collection of small JavaScript exercises and examples for future revision.

---

## Name Capitalization

```javascript
var name = "tyleR";

name = name.toLowerCase();

var finalName =
    name.slice(0, 1).toUpperCase() +
    name.slice(1);

alert("Hello, " + finalName + "!");
```

Output:

```text
Hello, Tyler!
```

### Notes

- `toLowerCase()` converts the whole string to lowercase.
- `slice(0, 1)` gets the first character.
- `toUpperCase()` capitalizes the first character.
- `slice(1)` gets the rest of the name.

---

## Dog Age Calculator

```javascript
var dogAge = prompt("How old is your dog?");

var humanAge = ((dogAge - 2) * 4) + 21;

alert(
    "Your dog is " +
    humanAge +
    " years old in human years!"
);
```

### Formula

```text
((dogAge - 2) × 4) + 21
```

---

## Milk Bottle Calculator

```javascript
function getMilk(money) {
    var bottles = Math.floor(money / 1.5);

    alert(
        "You get " +
        bottles +
        " bottles of milk."
    );
}

getMilk(
    prompt("How much money do you have?")
);
```

### Notes

- `Math.floor()` rounds down.
- Each bottle costs `1.5`.

---

## Life in Weeks Calculator

```javascript
function lifeInWeeks(age) {
    var yearsRemaining = 90 - age;

    var days = yearsRemaining * 365;
    var weeks = yearsRemaining * 52;
    var months = yearsRemaining * 12;

    alert(
        "You have " +
        days +
        " days, " +
        weeks +
        " weeks, and " +
        months +
        " months left."
    );
}

lifeInWeeks(
    prompt("What is your current age?")
);
```

---

## Milk Calculator with Change

```javascript
function getMilk(money) {
    alert(
        "You get " +
        calcBottles(money, 1.5) +
        " bottles of milk."
    );

    alert(
        "Your change is $" +
        calcChange(money, 1.5)
    );
}

function calcBottles(
    startingMoney,
    costPerBottle
) {
    return Math.floor(
        startingMoney / costPerBottle
    );
}

function calcChange(
    startingAmount,
    costPerBottle
) {
    return (
        startingAmount % costPerBottle
    ).toFixed(2);
}

getMilk(
    prompt("How much money do you have?")
);
```

### Notes

- `%` returns the remainder.
- `toFixed(2)` formats a number to two decimal places.

---

## Milk Calculator with Change — Simplified

```javascript
function getMilk(money) {
    alert(
        "You get " +
        Math.floor(money / 1.5) +
        " bottles of milk."
    );

    alert(
        "Your change is $" +
        (money % 1.5).toFixed(2)
    );
}

getMilk(
    prompt("How much money do you have?")
);
```

---

## BMI Calculator

```javascript
function bmiCalculator(weight, height) {
    var bmi =
        weight / Math.pow(height, 2);

    return Math.round(bmi);
}

var bmi = bmiCalculator(
    prompt("Enter your weight in kg:"),
    prompt("Enter your height in meters:")
);
```

### Formula

```text
BMI = weight / height²
```

---

## Dice Roll

```javascript
var n = Math.random();

n = n * 6;

n = Math.floor(n) + 1;

alert(n);
```

### Simplified Version

```javascript
alert(
    Math.floor(Math.random() * 6) + 1
);
```

### Notes

- `Math.random()` returns a number from `0` up to but not including `1`.
- Multiplying by `6` creates a range from `0` up to but not including `6`.
- `Math.floor()` produces an integer from `0` to `5`.
- Adding `1` gives a number from `1` to `6`.

---

## Love Calculator

```javascript
prompt("What is your name?");
prompt("What is your partner's name?");

var loveScore =
    Math.floor(Math.random() * 100) + 1;

if (loveScore > 70) {
    alert(
        "Your love score is " +
        loveScore +
        "%. You love each other like Kanye loves Kanye."
    );
} else if (loveScore > 30) {
    alert(
        "Your love score is " +
        loveScore +
        "%."
    );
} else {
    alert(
        "Your love score is " +
        loveScore +
        "%. You go together like oil and water."
    );
}
```

---

## Strict Equality vs Loose Equality

```javascript
var a = 1;
var b = "1";

typeof a; // number
typeof b; // string

if (a === b) {
    console.log(
        "Same value and type"
    );
}

if (a == b) {
    console.log(
        "Same value after type conversion"
    );
}
```

### Notes

```text
=== checks value and type
== checks value after type conversion
```

Prefer:

```javascript
===
```

---

## BMI Calculator with Interpretation

```javascript
function bmiCalculator(weight, height) {
    var bmi =
        weight / Math.pow(height, 2);

    var roundedBmi = Math.round(bmi);

    if (bmi < 18.5) {
        return (
            "Your BMI is " +
            roundedBmi +
            ", so you are underweight."
        );
    } else if (bmi <= 24.9) {
        return (
            "Your BMI is " +
            roundedBmi +
            ", so you have a normal weight."
        );
    } else {
        return (
            "Your BMI is " +
            roundedBmi +
            ", so you are overweight."
        );
    }
}

var bmi = bmiCalculator(
    prompt("Enter your weight in kg:"),
    prompt("Enter your height in meters:")
);

alert(bmi);
```

---

## Leap Year Calculator

```javascript
function isLeap(year) {
    if (year % 400 === 0) {
        return "Leap year.";
    }

    if (year % 100 === 0) {
        return "Not leap year.";
    }

    if (year % 4 === 0) {
        return "Leap year.";
    }

    return "Not leap year.";
}

isLeap(
    prompt("Enter a year:")
);
```

### Rule

A leap year:

```text
is divisible by 400
```

or:

```text
is divisible by 4
but not divisible by 100
```

---

## Array and Guest List

```javascript
var guestList = [
    "Angela",
    "Jack",
    "Pam",
    "James",
    "Lara",
    "Jason"
];

console.log(guestList);

console.log(guestList[2]);

console.log(guestList.length);

var guestName =
    prompt("What is your name?");

if (guestList.includes(guestName)) {
    alert("Welcome!");
} else {
    alert("You are not on the list.");
}
```

### Notes

- Array indexes start at `0`.
- `includes()` checks whether an array contains a value.
- `length` returns the number of items.

---

## FizzBuzz with While Loop

```javascript
var output = [];
var count = 1;

function fizzBuzz() {
    while (count <= 100) {
        if (
            count % 3 === 0 &&
            count % 5 === 0
        ) {
            output.push("FizzBuzz");
        } else if (count % 3 === 0) {
            output.push("Fizz");
        } else if (count % 5 === 0) {
            output.push("Buzz");
        } else {
            output.push(count);
        }

        count++;
    }

    console.log(output);
}

fizzBuzz();
```

---

## FizzBuzz with For Loop

```javascript
for (
    var count = 1;
    count <= 100;
    count++
) {
    if (
        count % 3 === 0 &&
        count % 5 === 0
    ) {
        console.log("FizzBuzz");
    } else if (count % 3 === 0) {
        console.log("Fizz");
    } else if (count % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(count);
    }
}
```

### Important

Check divisibility by both `3` and `5` first.

---

## 99 Bottles of Beer

```javascript
var bottles = 99;

while (bottles >= 0) {
    if (bottles > 1) {
        console.log(
            bottles +
            " bottles of beer on the wall, " +
            bottles +
            " bottles of beer."
        );

        console.log(
            "Take one down and pass it around, " +
            (bottles - 1) +
            " bottles of beer on the wall."
        );
    } else if (bottles === 1) {
        console.log(
            "1 bottle of beer on the wall, " +
            "1 bottle of beer."
        );

        console.log(
            "Take one down and pass it around, " +
            "no more bottles of beer on the wall."
        );
    } else {
        console.log(
            "No more bottles of beer on the wall, " +
            "no more bottles of beer."
        );

        console.log(
            "Go to the store and buy some more, " +
            "99 bottles of beer on the wall."
        );
    }

    bottles--;
}
```

---

## Fibonacci Sequence

```javascript
function fibonacciGenerator(n) {
    var output = [];

    if (n === 1) {
        output = [0];
    } else if (n === 2) {
        output = [0, 1];
    } else {
        output = [0, 1];

        for (var i = 2; i < n; i++) {
            var nextNumber =
                output[output.length - 1] +
                output[output.length - 2];

            output.push(nextNumber);
        }
    }

    return output;
}

fibonacciGenerator(10);
```

Output:

```text
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```

### Pattern

Each number is the sum of the previous two numbers.

---

## Higher-Order Functions

```javascript
function add(num1, num2) {
    return num1 + num2;
}

function subtract(num1, num2) {
    return num1 - num2;
}

function multiply(num1, num2) {
    return num1 * num2;
}

function divide(num1, num2) {
    return num1 / num2;
}

function calculator(
    num1,
    num2,
    operator
) {
    return operator(num1, num2);
}
```

Examples:

```javascript
calculator(5, 3, add);
// 8

calculator(5, 3, subtract);
// 2

calculator(5, 3, multiply);
// 15

calculator(6, 3, divide);
// 2
```  

### Notes

A higher-order function can:

- Accept another function as an argument.
- Return another function.

Here, `calculator()` accepts an operation function through the `operator` parameter.

---

## Main Concepts Covered

- Variables
- Strings
- Numbers
- Functions
- Parameters
- Return values
- Conditionals
- Arrays
- Loops
- Random numbers
- Modulus
- Equality operators
- Higher-order functions
