---
title: Views
weight: 10
---

View files must use kebab-case.

```
resources/
  views/
    payment-invoice.blade.php
```

```php
class PaymentInvoiceController
{
    public function index() {
        return view('payment-invoice');
    }
}
```

## Blade Templates

Indent using four spaces.

```html
<a href="/make-payment">
    Make Payment
</a>
```

Don't add spaces after control structures.

```html
@if($condition)
    Something
@endif
```
