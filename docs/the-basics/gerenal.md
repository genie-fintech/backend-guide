---
title: General
weight: 1
---

### Variables
Variables should be camelCase. It must use readable words which are describe about value.

[good]
```php
    $loanCalculator = new LoanCalculator();
```
[/good]

[bad]
```php
    $LoanCalculator = new LoanCalculator();
    $loan_calculator = new LoanCalculator();
    $l_calculator = new LoanCalculator();
    $l_c = new LoanCalculator();
```
[/bad]


### Void return types

If a method returns nothing, it should be indicated with `void`.
This makes it clearer to the users of your code what your intention was when writing it.

[good]
```php
// in a Laravel model
public function scopeArchived(Builder $query): void
{
    $query->
        ...
}
```
[/good]


### Typed properties

You should type a property whenever possible. Don't use a doc-block.

[good]
```php
class Foo
{
    public string $bar;
}
```
[/good]


[bad]
```
class Foo
{
    /** @var string */
    public $bar;
}
```
[/bad]

### Type casts and intval(), strval(), ... function

In the case of casting int, it's about 300% or 3 times as fast as using intval(). You must use casting int of intval

[good]
```php
$var = (bool) $var;
$var = (float) $var;
$var = (int) $var;
$var = (string) $var;
```
[/good]

[bad]
```php
$var = boolval($var);
$var = floatval($var);
$var = intval($var);
$var = strval($var);
```
[/bad]

### Enums

Values in enums should use PascalCase.

```php
enum AgreementType {  
    case Hp;
    case Title;
}

AgreementType::Hp;
```

Enums don't need to be prefixed as in most cases, it is clear by reading the name that it is an enum.

> E.g. `OrderStatus` or `BookingType` or `Suit`

### Whitespace

Statements should be allowed to breathe. In general always add blank lines between statements, unless they're a sequence of single-line equivalent operations. This isn't something enforceable, it's a matter of what looks best in its context.

[good]
```php
public function getPage($url)
{
    $page = $this->pages()->where('slug', $url)->first();

    if (! $page) {
        return null;
    }

    if ($page['private'] && ! Auth::check()) {
        return null;
    }

    return $page;
}
```
[/good]

[bad]
```php
// Everything's cramped together.
public function getPage($url)
{
    $page = $this->pages()->where('slug', $url)->first();
    if (! $page) {
        return null;
    }
    if ($page['private'] && ! Auth::check()) {
        return null;
    }
    return $page;
}
```
[/bad]

[good]
```php
// A sequence of single-line equivalent operations.
public function up(): void
{
    Schema::create('users', function (Blueprint $table) {
        $table->increments('id');
        $table->string('name');
        $table->string('email')->unique();
        $table->string('password');
        $table->rememberToken();
        $table->timestamps();
    });
}
```
[/good]

Don't add any extra empty lines between `{}` brackets.

[good]
```php
if ($foo) {
    $this->foo = $foo;
}
```
[/good]

[bad]
```php
if ($foo) {

    $this->foo = $foo;
}
```
[/bad]


