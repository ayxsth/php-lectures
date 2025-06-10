# PHP 101

## Introduction:

- PHP - Hypertext Preprocessor
- Server-side scripting language
- Open-source and widely used
- Ideal for web development

## Features:

- Easy to learn and use
- Cross-platform compatibility
- Supports various databases
- Extensive community support
- Rich set of built-in functions
- Object-oriented programming support
- Integration with HTML, CSS, and JavaScript

## Use Cases:

- Dynamic web pages
- Content management systems (CMS)
- E-commerce platforms
- Web applications
- RESTful APIs

## Getting Started:

- Install a web server (e.g., Apache, Nginx)
- Install PHP (e.g., using XAMPP, Laragon, MAMP, or LAMP stack)
- Create a PHP file with `.php` extension
- Use `<?php ... ?>` tags to embed PHP code within HTML
- Run the PHP file on the server to see the output

## Data Types:

- Integer: Whole numbers (e.g., `42`, `-7`)
- Float: Decimal numbers (e.g., `3.14`, `-0.001`)
- String: Sequence of characters (e.g., `"Hello, World!"`, `'PHP'`)
- Boolean: Represents `true` or `false`
- Array: Collection of values (e.g., `array(1, 2, 3)`, `["name" => "Alice", "age" => 30]`)
- Object: Instance of a class (e.g., `$person = new Person();`)
- NULL: Represents a variable with no value (e.g., `$var = null;`)

## Basic Syntax:

- PHP code starts with `<?php` and ends with `?>`

```php
<?php
// Simple PHP script to display "Hello, World!"
echo "Hello, World!";
?>
```

- Statements end with a semicolon `;`

```php
<?php
// Display a simple statement
echo "This is a statement.";
?>
```

- Variables start with `$` followed by the variable name

```php
<?php
// Variable declaration
$name = "John Doe";
$first_name = "Alice";
$last_name = "Smith";

$2nd_name = "Bob"; // Invalid variable name (cannot start with a number)
$first-name = "Charlie"; // Invalid variable name (cannot contain hyphen)
?>
```

- Comments can be single-line (`// comment`) or multi-line (`/* comment */`)

```php
<?php
/*
This is a multi-line comment
This is a second comment line
*/
echo "Comments are useful for documentation."; // Single-line comment
?>
```

- Strings can be enclosed in single quotes `'` or double quotes `"`

```php
<?php
// String examples
$singleQuoteString = 'Hello, World!';
$doubleQuoteString = "Hello, World!";
echo $singleQuoteString;
echo $doubleQuoteString;

$name = "Alice";
echo 'Hello, ' . $name . '!'; // Concatenation with single quotes
echo "Hello, $name!"; // Variable interpolation with double quotes
?>
```

- Output can be displayed using `echo` or `print`

```php
<?php
// Displaying output
echo "This is an echo statement.";
print "This is a print statement.";

echo "<br>"; // Line break for better readability
print "Both echo and print can be used to output text.";

echo ("Hello, World!"); // Parentheses are optional for echo
print("Hello, World!"); // Parentheses are optional for print

echo "Hello", " World!"; // Multiple arguments can be passed to echo
print "Hello", " World!"; // Multiple arguments can't be passed to print
?>
```

- Arrays can be indexed or associative

```php
<?php
// Indexed array
$fruits = array("Apple", "Banana", "Cherry");
// $fruits = ["Apple", "Banana", "Cherry"]; // Short array syntax (PHP 5.4+)
echo $fruits[0]; // Output: Apple
// Associative array
$person = array("name" => "John", "age" => 30);
echo $person["name"]; // Output: John
?>
```

## Expressions and Operators:

- Increment/Decrement operators `++` and `--`

```php
<?php
// Increment and Decrement
$count = 5;
$count++; // Increment by 1
echo $count; // Output: 6
$count--; // Decrement by 1
echo $count; // Output: 5
?>
```

- String concatenation operator `.`

```php
<?php
// String concatenation
$firstName = "John";
$lastName = "Doe";
$fullName = $firstName . " " . $lastName;
echo $fullName; // Output: John Doe
?>
```

- Equality operators `==`, `!=`

```php
<?php
// Equality operators
$a = 5;
$b = "5";

if ($a == $b) {
    echo "Equal"; // Output: Equal
} else {
    echo "Not equal";
}

if ($a != $b) {
    echo "Not identical";
} else {
    echo "Identical"; // Output: Identical
}
?>
```

- Identity operators `===`, `!==`

```php
<?php
// Identity operators
$a = 5;
$b = "5";

if ($a === $b) {
    echo "Identical"; // Output: Not identical
} else if ($a%2 == 0) {
    echo "Even";
} else {
    echo "Not identical";
}

if ($a !== $b) {
    echo "Not identical"; // Output: Not identical
} else {
    echo "Identical";
}
?>
```

- Ternary operator `? :`

```php
<?php
// Ternary operator
$age = 18;
$status = ($age >= 18) ? "Adult" : "Minor";
echo $status; // Output: Adult
?>
```

- Side-effects assignment operators `+=`, `-=`, `*=`, `/=`

```php
<?php
// Side-effects assignment operators
$x = 10;
$x += 5; // Equivalent to $x = $x + 5
echo $x; // Output: 15
$x -= 3; // Equivalent to $x = $x - 3
echo $x; // Output: 12
$x *= 2; // Equivalent to $x = $x * 2
echo $x; // Output: 24
$x /= 4; // Equivalent to $x = $x / 4
echo $x; // Output: 6
?>
```

## Conversion/Type Casting:

- Type casting can be done using `(type)` syntax

```php
<?php
// Implicit type conversion
$number = 10; // Integer
$floatNumber = 3.14; // Float
$sum = $number + $floatNumber; // Implicit conversion to float
echo $sum; // Output: 13.14

// Explicit type casting
$number = "10"; // String
$intNumber = (int)$number; // Convert to integer
$floatNumber = (float)$number; // Convert to float
echo $intNumber; // Output: 10
echo $floatNumber; // Output: 10.0
?>
```

---

## Assignments:

Create a PHP script that generates a simple student profile using only the PHP concepts you've learned today: variables, strings, arrays, expressions, operators, output, conditionals, and type casting.

Your script should display your basic student info, skillset, graduation plan, and GPA progress, with the following requirements:

### Instructions:

- Declare and assign values to the following variables:
  - `$first_name`
  - `$last_name`
  - `$age`
  - `$university`
  - `$course_name`
  - `$is_final_year` (use `true` or `false`)
- Display this information using both:

  - String interpolation (`"Hello, $first_name"`)
  - String concatenation (`"Hello, " . $first_name`)
    Example Output:

  ```
  Hi, I’m Aisha Khan.
  I’m 21 years old, currently studying Computer Science at Taylor’s University.
  ```

- Use an `if` or **ternary operator** to display whether you’re in your final year:

  - If `true`: `I’m in my final year`.
  - If `false`: `I still have time to graduate`.

- Create an indexed array called `$skills` with at least three academic or technical skills you have (e.g., "Python", "Research", "HTML"). Display each skill on its own line using `echo`.

  Example Output:

  ```
  My Skills:
    - Python
    - Problem-solving
    - HTML
  ```

- Use the `+=` operator to add 2 years to your current age, and display how old you’ll be by graduation:
  Example Output:

  ```
  By the time I graduate, I’ll be 23 years old.
  ```

- You received your GPA from the system as a string:

  ```php
    $gpa_string = "3.75";
  ```

  - Convert it to a float
  - Add `0.25` to it
  - Display your updated GPA using `echo`

  Example Output:

  ```
  My current GPA is 3.75.
  ```

- Add comments in your code:
  - One single-line comment using `//`
  - One multi-line comment using `/* ... */`
