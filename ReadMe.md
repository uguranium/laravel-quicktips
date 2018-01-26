# Laravel Quicktips

**Return array values if value and passed data name is same its possible to use `compact` function.**

```
Route::get('/', function () {
    $name = 'Ugur';
    $age = 27;
    return viev('home',compact('name','age'));
})
```


**Look the artisan commands**

`php artisan`
 
** Tinker (Laravel Shell)**
You can run with this command `php artisan tinker` . Then you can write commands.
For example if you have task table:
```
App\Task::all()
```
