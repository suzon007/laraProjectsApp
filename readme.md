#Project and Task App

Project and Task App is a PHP **laravel 5** framework based application inspired by this [tutorial](https://www.flynsarmy.com/2015/02/creating-a-basic-todo-application-in-laravel-5-part-1/).


##Features

- Uses Bootstrap Framework.
- Simple interface.
- CRUD functionalities.
##How to use the App
- Open http://dummy.url/projects Here you will find the Option to create project. If you had any, they will also be there. 

- In the create project page(http://dummy.url/projects/create) You can add your project's name and it's slug. The slug will be used in the URL field. After submitting your project it will take you the Projects page with the newly created Project. You can use EDIT or DELETE option.

-  Click on any project. You can add Task to it, edit or delete the tasks.
###Enjoy!

##Requirements

- [Composer](https://getcomposer.org/)
- [Laravel 5.0](https://laravel.com/docs/5.0)
- [Laravel Form Helpers](https://www.flynsarmy.com/2015/02/install-illuminatehtml-laravel-5/)

##Setup

1. Setup your database by editing the env file.

```
DB_HOST=localhost
DB_DATABASE=your_db_name
DB_USERNAME=db_user_name
DB_PASSWORD=your_pass
```
2. Perform the migration:
```
php artisan migrate

```
##Model
We have two model Task and Projects


##Controller

We have two controller. **ProjectsController** and **TasksController** in our App/Http/Controllers folder. 

In the ProjectsController the method **store**, **update**, **destroy**, **create**, **show** methods respectively store, update, destroy, create and show the Projects.
Similarly same thing happen in TaskController for the Tasks. 

##Url Slug
We use this piece of code in route to use slug like  /projects/my-first-project/tasks/buy-milk instead of /projects/1/tasks/2.
```
Route::bind('tasks', function($value, $route) {
	return App\Task::whereSlug($value)->first();
});
Route::bind('projects', function($value, $route) {
	return App\Project::whereSlug($value)->first();
});
```
This will override the default behavior for the tasks and projects wildcards in php artisan routes.

##Model Route Binding
Provided controller methods with object instead of ID (in our route)
```
Route::model('tasks', 'Task');
Route::model('projects', 'Project');
```
And in controllers passed the object to the controller method like this
```
public function edit(Project $project)
```

##Model Relations
On the /app/Project.php 
```
public function tasks()
{
	return $this->hasMany('App\Task');
}
```
On the /app/Task.php
```
public function project()
{
	return $this->belongsTo('App\Project');
}
``` 


##Layouts
In the folder *resources/views* **app.blade.php** is our main controller layout. 


