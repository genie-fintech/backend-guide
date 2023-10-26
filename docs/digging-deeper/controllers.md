---
title: Controllers
weight: 4
---

Controllers that control a resource must use the plural resource name.

```php
class PostController
{
    ...
}
```

Try to keep controllers simple and stick to the default CRUD keywords (`index`, `create`, `store`, `show`, `edit`, `update`, `destroy`). Extract a new controller if you need other actions.

In the following example, we could have `PostController@favorite`, and `PostController@unfavorite`, or we could extract it to a separate `FavoritePostController`.

```php
class PostController
{
    public function create()
    {
        ...
    }

    ...

    public function favorite(Post $post)
    {
        request()->user()->favorites()->attach($post);

        return response(null, 200);
    }

    public function unfavorite(Post $post)
    {
        request()->user()->favorites()->detach($post);

        return response(null, 200);
    }
}
```

Here we fall back to default CRUD words, `store` and `destroy`.<br>
This is a loose guideline that doesn't need to be enforced.

```php
class FavoritePostController
{
    public function store(Post $post)
    {
        request()->user()->favorites()->attach($post);

        return response(null, 200);
    }

    public function destroy(Post $post)
    {
        request()->user()->favorites()->detach($post);

        return response(null, 200);
    }
}
```
