# PHP Syntax: Loops and Functions

## Loops

Loops are used to execute a block of code multiple times. PHP supports several types of loops:

- `for` Loop

```php
for ($i = 0; $i < 10; $i++) {
    echo "Number: $i\n";
}
```

- `while` Loop

```php
$i = 0;
while ($i < 10) {
    echo "Number: $i\n";
    $i++;
}
```

- `do...while` Loop

```php
$i = 0;
do {
    echo "Number: $i\n";
    $i++;
} while ($i < 10);
```

- `foreach` Loop

```php
$fruits = ["apple", "banana", "cherry"];
foreach ($fruits as $fruit) {
    echo "Fruit: $fruit\n";
}
```

### Things to Remember About Loops

- `break` and `continue`

  `break` is used to exit a loop prematurely, while `continue` skips the current iteration and moves to the next one.

```php
for ($i = 0; $i < 10; $i++) {
    if ($i == 5) {
        break; // Exit the loop when $i is 5
    }
    echo "Number: $i\n";
}

for ($i = 0; $i < 10; $i++) {
    if ($i % 2 == 0) {
        continue; // Skip even numbers
    }
    echo "Odd Number: $i\n";
}
```

- Nested Loops
  You can nest loops within each other to perform more complex iterations.

```php
for ($i = 0; $i < 3; $i++) {
    for ($j = 0; $j < 3; $j++) {
        echo "i: $i, j: $j\n";
    }
}
```

- Looping through Associative Arrays

```php
$person = [
    "name" => "Alice",
    "age" => 30,
    "city" => "New York"
];
foreach ($person as $key => $value) {
    echo "$key: $value\n";
}
```

## Functions

Functions are reusable blocks of code that can be called with a specific name. They can accept parameters and return values.

- Defining a Function

```php
function greet($name) {
    echo "Hello, $name!";
}
```

- Calling a Function

```php
greet("Alice"); // Output: Hello, Alice!
```

- Function with Default Parameter

```php
function greet($name = "Guest") {
    echo "Hello, $name!";
}

greet(); // Output: Hello, Guest!
```

- Function with Return Value

```php
function add($a, $b) {
    return $a + $b;
}

$result = add(5, 10);
echo "Sum: $result"; // Output: Sum: 15
```

- Function with Variable Number of Arguments

```php
function sum(...$numbers) {
    $total = 0;
    foreach ($numbers as $number) {
        $total += $number;
    }
    return $total;
}

$result = sum(1, 2, 3, 4, 5);
echo "Total: $result"; // Output: Total: 15
```

- Anonymous Functions (Closures)

```php
$greet = function($name) {
    echo "Hello, $name!";
};
$greet("Bob"); // Output: Hello, Bob!
```

- Function with Type Hinting

```php
function multiply(int $a, int $b): int {
    return $a * $b;
}

$result = multiply(5, 10);
echo "Product: $result"; // Output: Product: 50
```

### Things to Remember About Functions

- Function Scope
  Variables defined inside a function are local to that function and cannot be accessed outside of it.

```php
function myFunction() {
    $localVar = "I'm local";
    echo $localVar; // Output: I'm local
}
myFunction();
echo $localVar; // This will cause an error because $localVar is not defined
```

- Global Variables
  You can access global variables inside a function using the `global` keyword.

```php
$globalVar = "I'm global";
function myFunction() {
    global $globalVar;
    echo $globalVar; // Output: I'm global
}
myFunction();
echo $globalVar; // Output: I'm global
```

- Returning Multiple Values
  You can return multiple values from a function using an array.

```php
function getCoordinates() {
    return [10, 20, 30];
}
list($x, $y) = getCoordinates();
echo "X: $x, Y: $y"; // Output: X: 10, Y: 20
```

- References vs. Values
  You can pass arguments by reference using the `&` symbol, allowing the function to modify the original variable.

```php
$num = 5;

function incrementByValue($value) {
    $value++;
}

incrementByValue($num);
echo $num; // Output: 5 (remains unchanged)

function incrementByRef(&$value) {
    $value++;
}

incrementByRef($num);
echo $num; // Output: 6
```

### Some built-in Functions

- String Functions

```php
echo strlen("Hello"); // Output: 5
echo strtoupper("hello"); // Output: HELLO
echo strtolower("HELLO"); // Output: hello
echo substr("Hello, World!", 7, 5); // Output: World
```

- Array Functions

```php
$fruits = ["apple", "banana", "cherry"];
echo count($fruits); // Output: 3
array_push($fruits, "date");
print_r($fruits); // Output: Array ( [0] => apple [1] => banana [2] => cherry [3] => date )
array_pop($fruits);
print_r($fruits); // Output: Array ( [0] => apple [1] => banana [2] => cherry )
array_shift($fruits);
print_r($fruits); // Output: Array ( [0] => banana [1] => cherry )
array_unshift($fruits, "kiwi");
print_r($fruits); // Output: Array ( [0] => kiwi [1] => banana [2] => cherry )
array_filter($fruits, function($fruit) {
    return $fruit !== "banana"; // Filter out "banana"
});// Output: Array ( [0] => kiwi [1] => cherry )

// [Note]: We are using `print_r` to display arrays in a readable format.
```

- Date Functions

```php
echo date("Y-m-d H:i:s"); // Output: Current date and time
echo strtotime("2023-10-01"); // Output: Timestamp for the given date
echo date("Y-m-d", strtotime("+1 week")); // Output: Date one week from
echo date("Y-m-d", strtotime("-1 month")); // Output: Date one month ago
```

## Exercise

- Use any loop to print this pattern:

```
*
**
***
****
*****
```

```php
for ($i = 1; $i <= 5; $i++) {
    for ($j = 1; $j <= $i; $j++) {
        echo "*";
    }
    echo "\n";
}

$i = 1;
while ($i <= 5) {
    $j = 1;
    while ($j <= $i) {
        echo "*";
        $j++;
    }    echo "\n";
    $i++;
}

$i = 1;
do {
    $j = 1;
    do {
        echo "*";
        $j++;
    } while ($j <= $i);
    echo "\n";
    $i++;
} while ($i <= 5);

for ($i = 1; $i <= 5; $i++) {
    echo str_repeat("*", $i) . "\n";
}
```

- Create a custom function to filter an array of numbers, returning only even numbers. Use a loop to iterate through the array and apply the function.

```php
function filterEvenNumbers($numbers) {
    $evenNumbers = [];
    foreach ($numbers as $number) {
        if ($number % 2 == 0) {
            $evenNumbers[] = $number;
        }
    }
    return $evenNumbers;
}
$numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
$evenNumbers = filterEvenNumbers($numbers);
print_r($evenNumbers); // Output: Array ( [0] => 2 [1] => 4 [2] => 6 [3] => 8 [4] => 10 )
```

- Create a custom function to an array of numbers, returning the number that are greater than a specified threshold. Use a loop to iterate through the array and apply the function.

```php
function filterGreaterThan($numbers, $threshold) {
    $filteredNumbers = [];
    foreach ($numbers as $number) {
        if ($number > $threshold) {
            $filteredNumbers[] = $number;
        }
    }
    return $filteredNumbers;
}
$numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
$threshold = 5
$greaterThanThreshold = filterGreaterThan($numbers, $threshold);
print_r($greaterThanThreshold); // Output: Array ( [0] => 6 [1] => 7 [2] => 8 [3] => 9 [4] => 10 )
```

- Create a replica function of the `array_filter` function that filters an array based on a callback function. Use a loop to iterate through the array and apply the callback.

```php
function customArrayFilter($array, $callback) {
    $filteredArray = [];
    foreach ($array as $item) {
        if ($callback($item)) {
            $filteredArray[] = $item;
        }
    }
    return $filteredArray;
}
$numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
$evenNumbers = customArrayFilter($numbers, function($number) {
    return $number % 2 == 0; // Filter even numbers
});
print_r($evenNumbers); // Output: Array ( [0] => 2 [1] => 4 [2] => 6 [3] => 8 [4] => 10 )
```
