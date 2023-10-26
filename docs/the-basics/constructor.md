---
title: Constructor
weight: 4
---

Use constructor property promotion if all properties can be promoted. To make it readable, put each one on a line of its own. Use a comma after the last one.

[good]
```php
class MyClass {
    public function __construct(
        protected string $firstArgument,
        protected string $secondArgument,
    ) {}
}
```
[/good]

[bad]
```php
class MyClass {
    protected string $secondArgument

    public function __construct(protected string $firstArgument, string $secondArgument)
    {
        $this->secondArgument = $secondArgument;
    }
}
```
[/bad]
