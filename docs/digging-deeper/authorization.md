---
title: Authorization
weight: 2
---

Policies must use kebab-case.

```php
Gate::define('update-post', function ($user, $post) {
    return $user->id == $post->user_id;
});
```

```html
@can('update-post', $post)
    <a href="{{ route('posts.update', $post) }}">
        Edit
    </a>
@endcan
```

Try to name abilities using default CRUD words. One exception: replace `show` with `view`. A server shows a resource, a user views it.
