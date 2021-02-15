# PHP CheatSheet

This cheatsheet outlines when some various handy features were introduced in different versions of PHP.

_Obviously not intended to be a comprehensive list._

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
* `heretic` and `nowdoc` strings
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
* Variadic functions with `...` 
	* `function foo($arg1, ...$moreArgs)`
* Exponentiation with `**`
* Type declarations for
	* Function arguments (classes, arrays, interfaces, or `callback`)
* Grouped namespaces 
	* `use App\Stuff\{Thing1, Thing2, Thing3}`
	
