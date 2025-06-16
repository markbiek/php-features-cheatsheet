# PHP CheatSheet

This cheatsheet outlines when some various handy features were introduced in different versions of PHP.

_Obviously not intended to be a comprehensive list._

## PHP 8.4

* Class property hooks. Property hooks can also be defined in interfaces
```
class User {
    public string $phone {
        set (string $newPhone) {
            // validate phone
        }
        get => $this->phone;
    }
}
```

* Asymmetric visibility for class properties. This means a property can be public/protected/private depending on if the property is being read or written. Also works for properties promoted in the constructor
```
class User {
    // This property can only be set from inside the class
    public private(set) string $name;
}
```

* New array functions
  * `array_find` takes a callback and returns the first element for which the callback returns true
  * `array_find_key` which is the same as `array_find` but returns the key
  * `array_any` returns true if at least one element matches the callback
  * `array_all` returns true if all elements match the callback

## PHP 8.3

* Class constants can be typed
* New `json_validate` function

## PHP 8.2

* Read-only classes
```
readonly class Person {
    public function __construct(
        public string $name,
        public string $address,
    ) {}
}
```

* `null`, `true`, and `false are standalone types
```
function bigNope(): false {
    return false;
}
```

* Combine union and intersection types
```
function createAnimal( (Cat|Dog)|null $animal ) {
    // do stuff
}
```

* Traits can have constants, though the constant is only accessible from the class that uses the trait.

## PHP 8.1
* Enums

```
enum Color {
  case Red;
  case Green;
  case Blue;
}
```

* Array unpacking with string keys (unpacking previously only worked with numeric keys)

```
$a1 = ["a" => 1];
$a2 = ["b" => 2];

$newArr = [...$a1, ...$a2];

// ["a" => 1, "b" => 2]
```

* Use `new` for default parameter values or constructor property promotion
	* `function foo( $input = new Bar() )`
* Readonly class properties: `public readonly string $name` (also works with constructor property promotion)
* First-class callable syntax

```
function foo(int $a, int $b) { }

$foo = foo(...);
$foo(1, 2);
```

* Intersection types. Similar to Union types but the input must be _all_ of the specified types.
* New `never` return type for functions. Signifies that the function wills top all program flow.
* New [`array_is_list`](https://www.php.net/manual/en/function.array-is-list.php) function.
* Specify class constants as `final` to prevent them from being overridden during inheritance.

## PHP 8.0
* Union types
	* `function foo(Foo|Bar $input): int|float`
* Nullsafe operator
	* `$dateAsString = $booking->getStartDate()?->asDateTimeString();`
* Named function arguments
	* `function foo(string $a, ?string $c = null)`
	* `foo(a: 'this is a', c: 'this is c')`
* [Attributes](https://www.php.net/manual/en/language.attributes.php)
* Constructor property promotion

```
class Thing {
  public function __construct(
  	public string $name = ''
  ) {}
}

$thing = new Thing('Mark');

echo $this->name;
```
* Match expressions
	* Similar to switch between results can be returned or stored.
	* `break` not needed
	* Strict comparisons
	
```
echo match (8.0) {
  '8.0' => "Oh no!",
  8.0 => "This is what I expected",
};
```

## PHP 7.4
* Type declarations for class properties 
	* Excludes `void` and `callable`
	* Nullable is allowed `private ?string $s;`
* Spread operator to merge arrays
	* `['a', 'b', ...$others]`
* Arrow functions
	* `fn($n) => $n + 1`
	* Automatically inherits variables in the parent scope without needing `use()`
* Null coalescing assignment operator `??=`

## PHP 7.3
* Trailing commas allowed in function calls
	* `function f(arg1, arg2, arg3,)`
	
## PHP 7.2
* `object` type declarations which allows passing or returning any arbitrary class or object
	* `function f(object $thing)`
* Trailing commas in grouped namespaces
	* `use App\Stuff\{Thing1, Thing2, Thing3,}`
	
## PHP 7.1
* Nullable type declarations 
	* `function f(?string $s): ?int`
* `void` function returns 
	* `function f(): void`
* `iterable` type declarations
* Multi-catch exception handling 
	* `catch (Exception1 | Exception2)`
	
## PHP 7.0
*  Type declarations for
	* Function arguments (scalar types like `int`, `string`, etc)
	* Function return values
* Null coalescing operator `??`
* Spaceship operator `<=>`
* Constant arrays using `define()`

## PHP 5.6
* `heredoc` and `nowdoc` strings
* Variadic functions with `...` 
	* `function foo($arg1, ...$moreArgs)`
* Exponentiation with `**`
* Type declarations for
	* Function arguments (classes, arrays, interfaces, or `callback`)
* Grouped namespaces 
	* `use App\Stuff\{Thing1, Thing2, Thing3}`
	
