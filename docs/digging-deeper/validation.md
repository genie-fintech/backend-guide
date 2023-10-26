---
title: Validation
weight: 9
---

When using multiple rules for one field in a form request, avoid using `|`, always use array notation. Using an array notation will make it easier to apply custom rule classes to a field.

[good]
```php
public function rules()
{
    return [
        'email' => ['required', 'email'],
    ];
}
```
[/good]

[bad]
```php
public function rules()
{
    return [
        'email' => 'required|email',
    ];
}
```
[/bad]


All custom validation rules must use snake_case:

```php
Validator::extend('organisation_type', function ($attribute, $value) {
    return OrganisationType::isValid($value);
});
```
