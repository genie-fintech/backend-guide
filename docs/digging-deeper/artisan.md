---
title: Artisan
weight: 1
---

The names given to artisan commands should all be kebab-cased.

[good]
```bash
php artisan delete-old-records
```
[/good]

[bad]
```bash
php artisan deleteOldRecords
```
[/bad]

A command should always give some feedback on what the result is. Minimally you should let the `handle` method spit out a comment at the end indicating that all went well.

```php
// in a Command
public function handle()
{
    // do some work

    $this->comment('All ok!');
}
```

When the main function of a result is processing items, consider adding output inside of the loop, so progress can be tracked. Put the output before the actual process. If something goes wrong, this makes it easy to know which item caused the error.

At the end of the command, provide a summary on how much processing was done.

```php
// in a Command
public function handle()
{
    $this->comment("Start processing items...");

    // do some work
    $items->each(function(Item $item) {
        $this->info("Processing item id `{$item-id}`...");

        $this->processItem($item);
    });

    $this->comment("Processed {$item->count()} items.");
}
```
