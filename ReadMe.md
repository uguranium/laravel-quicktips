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
 


####Tinker (Laravel Shell)

You can run with this command `php artisan tinker` . Then you can write commands.

For example if you have task table:
```
// get the all tasks
App\Task::all()

// get the id grater than 2
App\Task::where('id','>','2');

// get the just body column for all
App\Task::pluck('body')
```
 
 
#### Reset the migration 

`php artisan migrate:reset`



#### Composer autoload 

Sometimes composer failed or give directory error. Try `composer dump-autoload`


#### Create the model with migration and controller 

`php artisan make:model Task -mc`
The important thing is if model Task table name Tasks (create_table_tasks), if model Post teble is Posts (create_table_posts),


#### Sometimes in model better to use regular scope 
Without scope inside model:
```
...
    public static function incomplete () {
        return static::where('completed', 0)->get();
    }
...
```
now we can get incompleted rows but we can not make more where query or cant use other functions more. When we use scopes like:

```
public function scopeIncomplete() { 
  return static::where('completed',0);
}

``` 

now we can use 

```
ModelName::Incomplete()->where('id' , '>', 3)->get();

```

#### Controller quickly model using
we have show function under controller like this:

```
...
// Id is come from route and we are under TaskController

public function show($id) {
    $task = Task::find($id);
    return $task;
}
...
```

But also we can use like 

```
...
// Its inportant to task variable same as route name (like tasks/{$task})

public function show(Task $task) {
    return $task
}
...
```

#### How layouts are work
Lets try to explain with examples and standarts

First its better to use layouts under views/layouts folder. And for example we have posts layouts
```
 views/layouts
    /footer.blade.php
    /header.blade.php
    /master.blade.php <-- Main blade layout
 views/posts
    /index.blade.php
```

```
// Location: views/layouts/master.blade.php

@include(layouts.header)

<div>
    @yield(content)
<div>

@include(layouts.footer)
```

```
// Location: views/posts/index.blade.php

@extends(layouts.master)

    @section(content)
        My Post
    @endsection

@include(layouts.footer)
```











