---
title: Condition statements
weight: 3
---

### Bracket position

Always use curly brackets.

[good]
```php
if ($condition) {
   ...
}
```
[/good]

[bad]
```php
if ($condition) ...
```
[/bad]

### Happy path

Generally a function should have its unhappy path first and its happy path last. In most cases this will cause the happy path being in an unindented part of the function which makes it more readable.

[good]
```php
if (! $goodCondition) {
  throw new Exception;
}
```
[/good]


[bad]
```php
if ($goodCondition) {
 // do work
}

throw new Exception;
```
[/bad]

### Avoid else

In general, `else` should be avoided because it makes code less readable. In most cases it can be refactored using early returns. This will also cause the happy path to go last, which is desirable.

[good]
```php
if (! $conditionA) {
   // condition A failed

   return;
}

if (! $conditionB) {
   // condition A passed, B failed

   return;
}

// condition A and B passed
```
[/good]

[bad]
```php
if ($conditionA) {
   if ($conditionB) {
      // condition A and B passed
   }
   else {
     // condition A passed, B failed
   }
}
else {
   // condition A failed
}
```
[/bad]

Another option to refactor an `else` away is using a ternary

[bad]
```php
if ($condition) {
    $this->doSomething();
} 
else {
    $this->doSomethingElse();
}
```
[/bad]

[good]
```php
$condition
    ? $this->doSomething()
    : $this->doSomethingElse();
```
[/good]

### Compound ifs

In general, separate `if` statements should be preferred over a compound condition. This makes debugging code easier.


[good]
```php
if (! $conditionA) {
   return;
}

if (! $conditionB) {
   return;
}

if (! $conditionC) {
   return;
}

// do stuff
```
[/good]

[bad]
```php
if ($conditionA && $conditionB && $conditionC) {
  // do stuff
}
```
[/bad]
