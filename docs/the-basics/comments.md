---
title: Comments
weight: 2
---

### Doc-blocks

Don't use doc-blocks for methods that can be fully type hinted (unless you need a description).

Only add a description when it provides more context than the method signature itself. Use full sentences for descriptions, including a period at the end.

[good]
```php
class QrCodeService
{
    public static function fromString(string $text): QrCodeService
    {
        // ...
    }
}
```
[/good]

[bad]
```php
// The description is redundant, and the method is fully type-hinted.
class QrCodeService
{
    /**
     * Create a qrcode from a string.
     *
     * @param string $text
     *
     * @return \App\Services\QrCodeService
     */
    public static function fromString(string $text): QrCode
    {
        // ...
    }
}
```
[/bad]

If a variable has multiple types, the most common occurring type should be first.

[good]
```php
/** @var \Illuminate\Support\Collection|\SomeWeirdVendor\Collection */
```
[/good]

[bad]
```php
/** @var \SomeWeirdVendor\Collection|\Illuminate\Support\Collection */
```
[/bad]

If a function requires a doc-block for a single parameter or return type, add all other doc-blocks as well.

[good]
```php
/** 
 * @param string $name
 * @return \Illuminate\Support\Collection<SomeObject> 
 */
function someFunction(string $name): Collection {
    //
}
```
[/good]

[bad]
```php
/** 
 * @return \Illuminate\Support\Collection<SomeObject>
 */
function someFunction(string $name): Collection {
    //
}
```
[/bad]

### Doc-blocks for iterables

When your function gets passed an iterable, you should add a docblock to specify the type of key and value. This will greatly help static analysis tools understand the code, and IDEs to provide autocompletion.

```php
/**
 * @param $myArray array<int, MyObject>
 */
function someFunction(array $myArray) {

}
```

In this example, `typedArgument` needs a docblock too:

```php
/**
 * @param $myArray array<int, MyObject>
 * @param int $typedArgument 
 */
function someFunction(array $myArray, int $typedArgument) {

}
```

The keys and values of iterables that get returned should always be typed.

```php
use \Illuminate\Support\Collection

/**
 * @return \Illuminate\Support\Collection<int,SomeObject>
 */
function someFunction(): Collection {
    //
}
```

If your array or collection has a few fixed keys, you can typehint them too using `{}` notation.

```php
use \Illuminate\Support\Collection

/**
 * @return array{first: SomeClass, second: SomeClass}
 */
function someFunction(): array {
    //
}
```

If there is only one docblock needed, you may use the short version.

```php
use \Illuminate\Support\Collection

/** @return \Illuminate\Support\Collection<int,SomeObject> */
function someFunction(): Collection {
    //
}
```

### Comments

Comments should be avoided as much as possible by writing expressive code. If you do need to use a comment, format it like this:

```php
// There should be a space before a single line comment.

/*
 * If you need to explain a lot you can use a comment block. Notice the
 * single * on the first line. Comment blocks don't need to be three
 * lines long or three characters shorter than the previous line.
 */
```

A possible strategy to refactor away a comment is to create a function with name that describes the comment

[good]
```php
$this->calculateLoans();
```
[/good]

[bad]
```php
// Start calculating loans
```
[/bad]
