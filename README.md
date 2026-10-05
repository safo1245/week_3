# week_3

📚 Chapter 3 — Arrays and Functions in PHP

PHP & MySQL — Chapter 3 Study Notes

This chapter covers Arrays and Functions in PHP, including different types of arrays, array manipulation functions, user-defined functions, parameters and arguments, return values, variable scope, and including external PHP files.

⸻

 Table of Contents

 1. Arrays in PHP
 2. Types of Arrays
 3. Numerically Indexed Arrays
 4. foreach Loop
 5. Associative Arrays
 6. Multidimensional Arrays
 7. Important Array Functions
 8. Functions in PHP
 9. Parameters vs Arguments
 10. Returning a Value
 11. Passing by Value vs Reference
 12. Default Arguments
  13. Variable Scope
 14. Including Files
 15. Exam Quick Review

⸻

1. Arrays in PHP

An array is a variable that stores multiple values under one name.

Each value inside an array is called an element.

An element can be accessed using an index or key.

Example

$fruits = array("Apple", "Orange", "Banana");
echo $fruits[0];

Output

Apple

 Remember: Numeric array indexes normally start from 0.

⸻

2. Types of Arrays

PHP has three main types of arrays:

Type	Description
 Numerically Indexed	Uses numeric indexes
Associative	Uses string keys
Multidimensional	Contains arrays inside another array

⸻

3. Numerically Indexed Arrays

A numerically indexed array stores elements using numeric indexes.

Automatic Indexing

$fruits = array("Apple", "Orange", "Banana");
echo $fruits[0];
echo $fruits[1];
echo $fruits[2];

Manual Indexing

$fruits = array();
$fruits[0] = "Apple";
$fruits[1] = "Orange";
$fruits[2] = "Banana";

Adding Elements

$fruits[] = "Apple";
$fruits[] = "Orange";
$fruits[] = "Banana";

⸻

4. foreach Loop

The foreach loop is specially useful for working with arrays.

It goes through the array one element at a time.

Syntax

foreach ($array as $value) {
    // code
}

Example

$numbers = array(26, 11, 13);
foreach ($numbers as $n) {
    echo "$n ";
}

Output

26 11 13

Calculate Total

$numbers = array(10, 10, 15);
$total = 0;
foreach ($numbers as $n) {
    $total += $n;
}
echo "Total: $total";

Output

Total: 35

 Exam Tip: foreach is commonly used when you want to process every element of an array.

⸻

5. Associative Arrays

An associative array uses strings as keys instead of numeric indexes.

It is useful for storing key/value pairs.

Example

$info = array(
    "id" => "101",
    "name" => "Mohamed Abdi Ali",
    "age" => 20,
    "address" => "Hodan District",
    "status" => "single"
);

Accessing a Value

echo $info["name"];

The => Operator

The => operator connects a key to a value.

"name" => "Mohamed Abdi Ali"

Here:

Key   = name
Value = Mohamed Abdi Ali

⸻

Looping Through Associative Arrays

Values Only

foreach ($info as $value) {
    echo "$value<br>";
}

Keys and Values

foreach ($info as $key => $value) {
    echo "[$key]: $value<br>";
}

⸻

6. Multidimensional Arrays

A multidimensional array is an array containing other arrays.

A two-dimensional array is an array of arrays.

Example

$student = array(
    array("Mohamed", 1990, "Hodan", "0608124390"),
    array("Ahmed", 2001, "Yaaqshiid", "0608124391"),
    array("Jaamac", 1986, "Shangaani", "0608124392")
);

Accessing an Element

echo $student[0][0];

Output:

Mohamed

Nested foreach

foreach ($student as $studentData) {
    foreach ($studentData as $value) {
        echo "$value<br>";
    }
}

 Remember:

$student[row][column]

⸻

7. Important Array Functions

PHP provides built-in functions for accessing and manipulating arrays.

Function	What it does
is_array()	Checks if a variable is an array
in_array()	Checks if a value exists
count()	Counts array elements
sort()	Sorts ascending
rsort()	Sorts descending
asort()	Sorts associative array by value ascending
arsort()	Sorts associative array by value descending
max()	Finds highest value
min()	Finds lowest value
implode()	Converts array to string
explode()	Converts string to array
shuffle()	Randomizes array order
array_merge()	Combines arrays
array_reverse()	Reverses array
array_push()	Adds element to end
array_pop()	Removes last element
end()	Returns last element

⸻

is_array()

Checks whether a variable is an array.

if (is_array($info)) {
    echo "Yes, it is an array";
}

⸻

in_array()

Checks whether a value exists in an array.

if (in_array("Ahmed", $info)) {
    echo "Ahmed exists";
}

⸻

count()

Returns the number of elements.

$numbers = array(10, 20, 30);
echo count($numbers);

Output:

3

⸻

explode()

Converts a string into an array using a separator.

$text = "The quick brown fox";
$words = explode(" ", $text);
print_r($words);

⸻

shuffle()

Randomly changes the order of elements.

shuffle($words);

⸻

array_merge()

Combines arrays.

$a1 = array(1, 2, 3);
$a2 = array(4, 5, 6);
$a3 = array_merge($a1, $a2);

Result:

1, 2, 3, 4, 5, 6

⸻

array_reverse()

Reverses an array.

$array = array(1, 2, 3);
$result = array_reverse($array);

Result:

3, 2, 1

⸻

array_push()

Adds an element to the end.

$array = array(2, 4, 6);
array_push($array, 8);

⸻

array_pop()

Removes the last element.

$array = array(1, 2, 3, 4);
array_pop($array);

The last element 4 is removed.

⸻

8. Functions in PHP

A function is a set of statements that performs a specific task.

Functions are useful because they provide:

 Code reusability
 Less repeated code
 Fewer errors
 Easier-to-read programs
 Reusable operations

A function executes when it is called.

⸻

9. Creating a Function

Syntax

function function_name($parameter) {
    // statements
}

Example

function writeMsg() {
    echo "Hello World!";
}

Calling the Function

writeMsg();

A function can be called multiple times.

⸻

10. Parameters vs Arguments

 Very Important Exam Topic

Parameter

A parameter is a placeholder defined in the function.

function factorial($a) {
    // code
}

Here:

$a = Parameter

Argument

An argument is the actual value passed to the function.

factorial(5);

Here:

5 = Argument

Easy Rule

Parameter → receives the value
Argument  → sends the value

⸻

11. Returning a Value

A function can return a value using return.

Example

function add($a, $b) {
    $result = $a + $b;
    return $result;
}
$total = add(5, 3);
echo $total;

Output:

8

 Important: When return executes, the function stops at that point.

⸻

12. Passing an Array to a Function

A function can receive and return an array.

function passingArray($arr) {
    for ($i = 0; $i < count($arr); $i++) {
        $arr[$i]++;
    }
    return $arr;
}

Call:

$array1 = array(9, 2, 7, 5);
$result = passingArray($array1);

A function can therefore return multiple values through an array.

⸻

13. Passing By Value vs Reference

Passing By Value

Passing by value means the function receives a copy of the variable.

The original variable does not change.

$a = 5;
function test($x) {
    $x++;
}
test($a);
echo $a;

Output:

5

⸻

Passing By Reference

Passing by reference allows the function to change the original variable.

Use &.

$a = 5;
function test(&$x) {
    $x++;
}
test($a);
echo $a;

Output:

6

⭐ Remember

By Value
→ Copy is passed
→ Original does not change
By Reference
→ Original is passed
→ Original can change

⸻

14. Default Arguments

A function parameter can have a default value.

function factorial($a = 5) {
    // code
}

Calling without an argument:

factorial();

PHP uses:

$a = 5

But if we provide a value:

factorial(10);

Then:

$a = 10

⸻

15. Variable Scope

Scope means the part of the program where a variable can be accessed.

Local Variable

A variable declared inside a function has local scope.

function test() {
    $a = 10;
}

$a can be accessed inside the function.

⸻

Global Variable

A variable declared outside a function has global scope.

$a = 5;

⸻

Using global

The global keyword allows a function to access a global variable.

$a = 5;
function test() {
    global $a;
    echo $a;
}
test();

Output:

5

⸻

$GLOBALS

PHP also provides the $GLOBALS superglobal array.

$a = 5;
function test() {
    echo $GLOBALS["a"];
}

⸻

16. Superglobal Variables

PHP provides predefined superglobal variables.

Examples:

$_GET
$_SESSION
$_FILES
$_SERVER
$GLOBALS

These variables can be accessed throughout the program.

⸻

17. Static Variables

A static variable:

 Is declared inside a function
 Is accessible only inside that function
 Keeps its value between function calls

 Best practice from the chapter: Keep variables local whenever possible and use global variables only when necessary.

⸻

18. Including Files

PHP allows us to insert another PHP/HTML file into the current file.

Main statements:

include
include_once
require
require_once

This is useful for reusable components such as:

 Header
 Footer
 Navigation menu
 Function libraries

⸻

19. include

Loads another file into the current script.

include "library.php";

The content of library.php is inserted at that point.

⸻

20. include_once

Includes a file only once.

include_once "library.php";

This helps prevent the same file from being included multiple times.

⸻

21. require

Used when the file is essential.

require "library.php";

If the file is missing:

Fatal Error
↓
Script stops

⸻

22. require_once

Includes an essential file only once.

require_once "library.php";

It combines the idea of:

require + include once

⸻

23. include vs require

⭐ Very Important

include	require
Missing file → Warning	Missing file → Fatal error
Script continues	Script stops
Useful for non-essential files	Useful for essential files

Easy Memory Trick

include  → Warning → Continue
require  → Fatal Error → Stop

The chapter specifically explains that require produces a fatal error and stops the script, while include produces a warning and allows execution to continue.

⸻

24. function_exists()

Checks whether a function exists.

if (function_exists("factorial")) {
    echo "This function exists";
}

It can check predefined and user-created functions.

⸻

⭐ Exam Quick Review

Arrays

Array
→ Stores multiple values
Element
→ A value inside an array
Index
→ Numeric position
Key
→ Identifier used to access a value

⸻

Array Types

1. Numerically Indexed Array
2. Associative Array
3. Multidimensional Array

⸻

Important Operators

=>   Key/value association
&    Pass by reference

⸻

Important Loops

for
foreach

⸻

Important Array Functions

is_array()
in_array()
count()
sort()
rsort()
asort()
arsort()
max()
min()
implode()
explode()
shuffle()
array_merge()
array_reverse()
array_push()
array_pop()
end()

⸻

Functions

function
parameter
argument
return

Parameter vs Argument

Parameter = Placeholder
Argument  = Actual value

⸻

Passing Variables

By Value
→ Copy
→ Original unchanged
By Reference
→ Original
→ Original can change

⸻

Scope

Local
Global
Static
Superglobal

⸻

Including Files

include
include_once
require
require_once

Most Important Difference

include
→ Warning
→ Script continues
require
→ Fatal error
→ Script stops

⸻

🎯 Final Chapter Summary

This chapter teaches two major PHP concepts:

🔹 Arrays

Arrays allow PHP programs to store and manage multiple values using:

 Numeric indexes
 String keys
 Multiple dimensions

🔹 Functions

Functions allow programmers to create reusable blocks of code that can:

* Receive parameters
* Accept arguments
* Return values
* Use local/global variables
* Use default arguments
* Pass values by value or reference

The chapter also introduces array functions, variable scope, superglobals, and including external PHP files.

⸻

 One-Minute Revision

ARRAY
│
├── Numeric
├── Associative
└── Multidimensional
ARRAY FUNCTIONS
│
├── count()
├── sort()
├── in_array()
├── explode()
├── implode()
├── array_merge()
├── array_reverse()
├── array_push()
└── array_pop()
FUNCTION
│
├── Parameter
├── Argument
├── return
├── Default Argument
├── By Value
├── By Reference
└── Scope
FILES
│
├── include
├── include_once
├── require
└── require_once

⸻

📌 Source

PHP & MySQL — Chapter 3: Arrays and Functions in PHP

Lecturer: Yahye Ali Isse, MSc Data Science

Topics covered in the chapter include Arrays, Array Functions, Functions, Parameters vs Arguments, Returning Values, Passing by Value/Reference, Default Arguments, Variable Scope, and Including Files.

⸻

⭐ End of Chapter 3 Notes
