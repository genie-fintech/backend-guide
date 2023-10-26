---
title: Helpers
weight: 5
---

You should use snake_case

[good]
```php
function carbon_parse(string $date): Carbon
{
    return Carbon::parse($date);
}
```
[/good]

[bad]
```php
public function carbonParse(string $date): Carbon
{
    return Carbon::parse($date);
}
```
[/bad]
