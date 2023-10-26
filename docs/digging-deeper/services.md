---
title: Services
weight: 7
---

A controller must have only one responsibility, so move business logic from controllers to service classes.

[good]
```php
public function store(Request $request)
{
    $this->processImage->upload($request->file('image'));

    ...
}

class ProcessImage
{
    public function upload($image): void
    {
        if (!is_null($image)) {
            $image->move(public_path('images') . 'temp');
        }
    }
}
```
[/good]

[bad]
```php
public function store()
{
    if ($request->hasFile('image')) {
        $request->file('image')->move(public_path('images') . 'temp');
    }
    
    ...
}
```
[/bad]

Service don't need to be suffixed as in most cases.

> E.g. `ShortKeyGenerator`

Sometimes you can suffix with 'Service' to distinguishable from other classes.

> E.g. `ImageService`
