---
title: Routing
weight: 6
---

Public-facing urls must use kebab-case if there are two words in single part.<br>
It should be in plural form.

```
https://core.genies.dev/api/v1/document-export
https://core.genies.dev/api/v1/payment-bulk-upload
```

### API Version

We must create the API controller version group to avoid complications with your application routes.

```
app/
  /Http
     /controllers
        /Api
          /v1
             /UserController.php
          /v2
             /UserController.php
```

Prefer to use the route tuple notation when possible.

[good]
```php
Route::get('customers', [CustomerController::class, 'index']);
```
[/good]


[bad]
```php
Route::get('customers', 'CustomerController@index');
```
[/bad]

[good]
```html
<a href="{{ action([\App\Http\Controllers\CustomerController::class, 'index']) }}">
    Customers
</a>
```
[/good]

Route names must use snake_case with dot notation.

[good]
```php
Route::get('active-users', [UserController::class, 'index'])->name('users.show_active');
```
[/good]

[bad]
```php
Route::get('active-users', [UserController::class, 'index'])->name('users-show-active');
```
[/bad]

All routes have an HTTP verb, that's why we like to put the verb first when defining a route. It makes a group of routes very readable. Any other route options should come after it.

[good]
```php
// all HTTP verbs come first
Route::get('/', [HomeController::class, 'index'])->name('home');
Route::get('customers', [CustomerController::class, 'index'])->name('customers');
```
[/good]

[bad]
```php
// HTTP verbs not easily scannable
Route::name('home')->get('/', [HomeController::class, 'index']);
Route::name('customers')->get([CustomerController::class, 'customers']);
```
[/bad]

Route parameters should use camelCase.

```php
Route::get('news/{newsItem}', [NewsItemController::class, 'index']);
```

A route url should not start with `/` unless the url would be an empty string.

[good]
```php
Route::get('/', [HomeController::class, 'index']);
Route::get('customers', [CustomerController::class, 'index']);
```
[/good]

[bad]
```php
Route::get('', [HomeController::class, 'index']);
Route::get('/customers', [CustomerController::class, 'index']);
```
[/bad]
