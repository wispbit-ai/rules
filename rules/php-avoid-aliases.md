---
include: "app/controllers/api/*.php"
title: Avoid aliases for new routes in PHP
tags: php
---

Only use route aliases for backward compatibility with renamed or moved routes. Do not add aliases to newly created routes.

Bad:

```php
// Adding an alias to a new route
Route::put('/api/users/{id}')
    ->alias('/api/user/{id}');

// Another framework example
$router->map('GET', '/products/{productId}', 'ProductController::show')
    ->alias('product.show.alt');
```

Good:

```php
// New route without an alias
Route::put('/api/users/{id}');
```
