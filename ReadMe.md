# Laravel Quicktips

Return array values if value and passed data name is same its possible to use `compact` function.

```
Route::get('/', function () {
    $name = 'Ugur';
    $age = 27;
    return viev('home',compact('name','age'));
})
```
