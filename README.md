# PHP Cheat Sheet

### PHP local server

`php -S localhost:3000`

### Comments
```
// one line comment

/* 
This is a multiple-lines comment block 
that can be used on multiple lines
*/
```
### Naming conventions
```
// PHP opening/closing tag
<?php
  echo "Hello World!!";
?>
// if no closing tag the rest of the file will be considered PHP

// Short syntax for PHP echo
<?= "Hello World" ?>

//Enable strict typing (first line of your PHP file)
<? declare(strict_types=1);

// Include a PHP file
require 'app/Product.php'

// Create a namespace
namespace App;

// Use a namespace
use App\Product;

$firstName = 'Jhon'  // camelCase
function updateProduct() // camelCase
class ProductItem // StudlyCaps
const ACCESS_KEY = '123abc'; // all upper case with underscore separators 
Output & Input
echo 'Hello World!!';

// Debug output
var_dump($names);
print_r($products);

// Input from console
$name = readline('What is your name : ');
```
### Variables Declaration
```
$name = 'Jhon'; //string
$isActive = true; //boolean
$number = 25; //integer
$amount = 99.95; //float
$fruits = ['orange', 'apple', 'banana'] //array
const MAX_USERS = 50; //constant
define('MAX_USERS', 50); //constant

// Assign 'by reference' with the & keyword
$name_2 = &$name_1

// Type conversion
$age = (int)readline('Your age: ');
echo 'Your age is' . (string)$age;

echo gettype($age); // int

echo is_int($age); // true
echo is_float(12.5); // true
echo is_string($name); // true
```
### Strings
```
// String can use single quote
$name = 'Mike'
// or double quote
$name = "Mike"

// Double quote string can escape characters \n = new line  \t = tab  \\ = backslash
echo "Hello Mike\nHello David";

// Double quote string can do interpolation
echo "Hello $name";

// string concat
echo 'Hello ' . $name;

// string length
echo strlen($name);

// Remove space(s) before and after
echo trim($text)

// Convert to lowercase / uppercase
echo strtolower($email);
echo strtoupper($name);

// Converts the first character to uppercase
echo ucfirst($name);  // 'Mike' 

// Replace text a by text b in $text
echo str_replace('a', 'b', $text);

// String Contains (PHP 8)
echo str_contains($name, 'ke')  # true

// Find numeric position of first occurrence 
$pos = strpos($name, 'k'); # 2

// Returns portion of string (offset / length)
echo substr($name, 0, $pos); # Mi 
```
### Numbers
```
// Shortcut addition assignment
$value = 10
$value++ // 11
// or
$value += 1 // 11

// Shortcut subtraction assignment
$value = 10
$value-- // 9
// or
$value -= 1 // 9

// Check if numeric
echo is_numeric('59.99'); # true

// Round a number
echo round(0.80);  // returns 1

// Round a number with precision
echo round(1.49356, 2));  // returns 1.49

// Random number 
echo(rand(10, 100)); # 89
```
### Conditionals
```
// If / elseif / else
if ($condition == 10) {
    echo 'condition 10'
} elseif  ($condition == 5) {
    echo 'condition 5'
} else {
    echo 'all other conditions'
}

// And condition = &&
if ($condition === 10 && $condition2 === 5) {
    echo '10 and 5'
}

// Or condition = ||
if ($condition === 10 || $condition2 === 5) {
    echo '10 or 5'
}

// One line 
if ($isActive) return true;

// Null check
if (is_null($name)) {
    do something...
}

//Comparaison operation
== // equal no type check
=== // equal with type check
!= //not equal
|| //or
&& //and
> //greater than
< //less than

// Ternary operator (true : false)
echo $isValid ? 'user valid' : 'user not valid';

//Null Coalesce Operator
echo $name ?? 'Mike';  //output 'Mike' if $name is null

//Null Coalesce Assignment
$name ??= 'Mike';

// Null Safe Operator (PHP 8) will return null if one ? is null
echo $user?->profile?->activate();

// Null Safe + Null Coalesce (if null will return 'No user profile')
echo $user?->profile?->activate() ?? 'Not applicable';

//Spaceship operator return -1 0 1
$names = ['Mike', 'Paul', 'John']
usort($names, function($a, $b) {
    return $a <=> $b;
}
// ['John', 'Mike', 'Paul']

// Return false when convert as boolean
false, 0, 0.0, null, unset, '0', '', []

// Compare same variable with multiple values
switch ($color) {
    case 'red':
        echo 'The color is red';
         break;
    case 'yellow':
        echo 'The color is yellow';
        break;
    case 'blue':
        echo 'The color is blue';
        break;
    default:
        echo 'The color is unknown';
}

// Match Expression (PHP 8)
$type = match($color) {
    'red' => 'danger',
    'yellow', 'orange' => 'warning',
    'green' => 'success',
    default => 'Unknown'
};

// Check if variable declare
isset($color['red']);  # true
```
### Loops and Iterations
```
//for loop
for ($i = 0; $i < 20; $i++) {
    echo "i value = " . i;
}

//while loop
$number = 1;
while ($number < 10) {
    echo 'value : ' . $number ;
    $number += 1;
}

//do while
$number = 1;
do {
    echo 'value : ' . $number ;
    $number += 1;
} while ($number < 10);

// foreach with break / continue exemple
$values = ['one', 'two', 'three'];
foreach ($values as $value) {
    if ($value === 'two') {
        break; // exit loop
    } elseif ($value === 'three') {
        continue; // next loop iteration
    }
}
```
### Arrays
```
//Array declaration can contain any types
$example = ['Mike', 50.2, true, ['10', '20']];

//Array declaration
$names = ['Mike', 'Peter', 'Shawn', 'John'];

// Direct access to a specific element
$name[1] //output Peter

// How to access an array in an array
$example[3][1] // 20

//add a element to an array
$names[] = 'Micheal';

// Array merge
$array3 = array_merge($array1, $array2);

// Merge with spreading operator (also work with associative array)
$array3 = [...$array1, ...$array2];

// Array Concat with Spread Operator
$names = ['Mike', 'Peter', 'Paul'];
$people = ['John', ...$names]; // ['John', 'Mike', 'Peter', 'Paul']

//Remove array entry:
unset($names['Peter']);

//Array to string
echo implode(', ', $names) //output Mike, Shawn, John, Micheal

// String to Array
echo explode(',', $text); // ['Mike', 'Shawn', 'John']


//loop for each array entry
foreach($names as $name) { 
   echo 'Hello ' . $name;
}

// Number of items in a Array
echo count($names);  

//Associative array declaration (key => value):
$person = ['age' => 45, 'genre' => 'men'];

//Add to ass. array:
$person['name'] = 'Mike';

//loop ass. array key => value: 
foreach($names as $key => $value) { 
   echo $key . ' : ' . $value
}

// Check if a specific key exist
echo array_key_exists('age', $person);

// Return keys
echo array_keys($person); // ['age', 'genre']

// Return values
echo array_values($person) // [45, 'men']

//Array filter (return a filtered array)
$filteredPeople = array_filter($people, function ($person) {
    return $names->active;
})

// Array map (return transform array):
$onlyNames = array_map(function($person) {
    return ['name' => $person->name];
}, $people)

# Search associative array
$items = [
        ['id' => '100', 'name' => 'product 1'],
        ['id' => '200', 'name' => 'product 2'],
        ['id' => '300', 'name' => 'product 3'],
        ['id' => '400', 'name' => 'product 4'],
    ];

# search all value in the 'name' column
$found_key = array_search('product 3', array_column($items, 'name'));
# return 2
```
### Functions
```
//function declararion
function name($firstName, $lastName = 'defaultvalue') {
    return "$firstName $lastName"
}

//function call
name('Mike', 'Taylor');

//function call with named parameters (PHP 8)
name(firstName: 'Mike', lastName: 'Taylor'); // order can change

//function variables params
function name(...$params) {
    return $params[0] . “ “ . params[1];
}

// Closure function
Route::get('/', function () {
     return view('welcome');
});

// Arrow functions
Route::get('/', fn () => view('welcome');


// Typed parameter and typed return
function display(string $first, string $last) : string {
    return "$first $last";
}

// Typed or null
function display(?string $name) {
    ...
}

// Union type (or)
function display(string|int $data) {
    ...
}

// Intersection type (and)
function count_and_interate(Iterator&Countable $value) {
    ...
}

// Return any type (mixed)
function logInfo(string $info) : mixed {
    ...
}

// No return (void)
function logInfo(string $info) : void {
    ...
}
```
### Enumerations
```
// Declaration
enum InvoiceStatus
{
    case Sent;
    case Paid;
    case Cancelled;
}

// The enum can then be use as a type
function printInvoiceStatus(InvoiceStatus $status)
{
    print($status->name);
}

printInvoiceStatus(InvoiceStatus::Sent);
// Sent

// enum with return value and public function exemple
enum InvoiceStatus : int
{
    case Sent = 0;
    case Paid = 1;
    case Cancelled = 2;

    public function text() : string
    {
        return match ($this) {
            self::Sent => 'Sent',
            self::Paid => 'Paid',
            self::Cancelled => 'Cancelled'
        };
    }
}

function getInvoiceStatus(InvoiceStatus $status)
{
    print($status->text());
    print($status->value);
}

getInvoiceStatus(InvoiceStatus::Paid);
// Paid1
```
### Files
```
// Get the current dir
$current_dir = __DIR__;

// Check if file exist
if (file_exists('/posts/first.txt')) {
  do some stuff
}

// Read file content into one variable
$post = file_get_contents($file);

//File read
$file = fopen("test.txt", "r");

//Output lines until EOF is reached
while(! feof($file)) {
  $line = fgets($file);
  echo $line. "<br>";
}
fclose($file);

// File write (csv)
$file = fopen('export.csv', 'a');
$array = ['name' => 'Mike', 'age' => 45];

//Write key name as csv header
fputcsv($file, array_keys($array[0]));

//Write lines (format as csv)
foreach ($array as $row) {
    fputcsv($file, $row); 
}
fclose($file);
```
### Errors
```
//Throw Error
if (someCondition) {
    throw new Exception('Data format error');
}

//Catch the Error
try {
  $db->checkData($data);
} catch (Exception $e) {
    echo $e->getMessage();
}
```
### OOP
```
//class declaration
class Person 
{
}

// object instantiation
$person = new Person

//class properties and constructor
class Person 
{
   protected $firstName;
   protected $lastName;
   public function __construct($firstName, $lastName) {
        $this->firstName = $firstName;
        $this->lastName = $lastName
   }

// Constructor Property Promotion (PHP 8)
class Person 
{
    public function __construct(protected $firstName, protected $lastName) 
    {

    }

// Getter and Setter
class Person
{
    private $name;

    public function setName($name){
        if(!is_string($name)){
            throw new Exception('$name must be a string!');
        }
        $this->name = $name;
    }

    public function getName(){
        return $this->name;
    }
}

// Readonly properties (PHP 8.1)
class Person 
{
    public function __construct(
        public readonly string $firstName, 
        public readonly string $lastName
    ) {

    }
}

//static constructor
public static function create(...$params) {
    return new self($params)
}
$person = Person::create(‘Mike’, ‘Taylor’);

// Static Method
class greeting {
  public static function welcome() {
    echo "Hello World!";
  }
}

// Call static method
greeting::welcome();

// Static method call
class greeting {
  public static function welcome() {
    echo "Hello World!";
  }

  public function __construct() {
    static::welcome();
  }
}
new greeting();

// Static constant
class Connection
{
  const MAX_USER = 100;
}
echo Connection::MAX_USER # 100

// class inheritance
class Customer extends Person
{
    public function name()
    {
        parent::name();
        echo 'Override method';  
    }
}

// self keyword reference current class (not modify by inheritance late binding like static will be)
self::welcome();

// Interface
interface Animal {
  public function makeSound();
}

class Cat implements Animal {
  public function makeSound() {
    echo "Meow";
  }
}
$animal = new Cat();
$animal->makeSound();

//Trait (mix-in)
trait HelloWorld {
    public function sayHello() {
        echo 'Hello World!';
    }
}

class Greetings {
    use HelloWorld;
}
$object = new Greetings();
$object->sayHello();
```
