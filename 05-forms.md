# PHP Forms

## Methods

Methods are used to specify how form data is sent to the server. The two most common methods are:

- `GET`: Appends form data to the URL, making it visible in the browser's address bar. Suitable for non-sensitive data.
- `POST`: Sends form data in the request body, keeping it hidden from the URL and browser history. Suitable for sensitive data.

> [Note: PHP Global Variables](https://www.php.net/manual/en/reserved.variables.php) like `$_GET` and `$_POST` are used to access form data sent via these methods.

```php
// Example of a form using GET method
<form method="GET">
    <input type="text" name="username" placeholder="Enter your username">
    <input type="submit" value="Submit">
</form>

<pre>
$_GET:
  <?php
    print_r($_GET);
  ?>
</pre>
```

```php
// Example of a form using POST method
<form method="POST">
    <input type="text" name="username" placeholder="Enter your username">
    <input type="submit" value="Submit">
</form>

<pre>
$_POST:
  <?php
    print_r($_POST);
  ?>
</pre>
```

## Input Types

Input types define the kind of data that can be entered into a form field. Common input types include:

- `text`: A single-line text input.
- `password`: A single-line text input that hides the entered characters.
- `email`: A single-line text input for email addresses.
- `number`: A single-line text input for numeric values.
- `checkbox`: A checkbox input for boolean values.
- `radio`: A radio button input for selecting one option from a set.
- `submit`: A button to submit the form.
- `reset`: A button to reset the form fields to their default values.

```php
// Example of various input types
<form method="POST">
    <input type="text" name="username" placeholder="Enter your username">
    <input type="password" name="password" placeholder="Enter your password">
    <input type="email" name="email" placeholder="Enter you email">
    <input type="number" name="age" placeholder="Enter your age">
    <input type="checkbox" name="subscribe" value="yes"> Subscribe to newsletter
    <input type="submit" value="Submit">
    <input type="reset" value="Reset">
</form>
```

## Form Validation

Form validation is crucial to ensure that the data submitted by users meets specific criteria before processing it. PHP provides several ways to validate form data, including:

- **Client-side validation**: Using HTML5 attributes like `required`, `minlength`, `maxlength`, and `pattern` to enforce rules before submission.
- **Server-side validation**:
  Using PHP to check the submitted data after the form is submitted. This is essential for security and to handle cases where client-side validation is bypassed.

```php
<?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $username = trim($_POST["username"]);
        $password = trim($_POST["password"]);
        $email = trim($_POST["email"]);
        $age = trim($_POST["age"]);
        $errors = [];

        if (empty($username)) {
            $errors["username"] = "Username is required.";
        } else {
            unset($errors["username"]);
        }

        if (empty($password)) {
            $errors["password"] = "Password is required.";
        } elseif (strlen($password) < 6) {
            $errors["password"] = "Password must be at least 6 characters long.";
        } else {
            unset($errors["password"]);
        }

        if (empty($email)) {
            $errors["email"] = "Valid email is required.";
        } elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
            $errors["email"] = "Invalid email format.";
        } else {
            unset($errors["email"]);
        }

        if (empty($age)) {
            $errors["age"] = "Valid age is required.";
        } elseif (!is_numeric($age) || $age < 0) {
            $errors["age"] = "Age must be a positive number.";
        } else {
            unset($errors["age"]);
        }

        if (empty($errors)) {
            // Process the form data (e.g., save to database, send email, etc.)
            echo "Form submitted successfully!";
        }
    }
?>
```

## Summary

Forms in PHP are essential for collecting user input and processing it securely. Understanding the different methods (`GET` and `POST`), input types, and validation techniques is crucial for building robust web applications. Always ensure to validate and sanitize user input to prevent security vulnerabilities such as SQL injection and cross-site scripting (XSS).

## Exercise

Create a simple registration form that collects the following information:

- Username
- Password
- Email
- Age
- Subscription preference (checkbox)

Implement server-side validation to ensure:

- Username is required and at least 3 characters long.
- Password is required and at least 6 characters long.
- Email is required and must be in a valid format.
- Age is required and must be a positive number.
  Display appropriate error messages for any validation failures and show the submitted data if the form is successfully submitted.
