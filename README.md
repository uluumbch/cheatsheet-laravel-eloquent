# laravel eloquent cheatsheet

here is some of laravel eloquent syntax that commonly used with example :

## Retrieval

This list of method return one data or collection of data
| Method | Description | Example |
| --------------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| all() | Retrieve all records | `$users = User::all();` |
| find() | Retrieve a record by primary key | `$user = User::find(1);` |
| findOrFail() | Retrieve a record by primary key or throw an exception if not found | `$user = User::findOrFail(1);` |
| first() | Retrieve the first record | `$user = User::first();` |
| get() | Retrieve multiple records | `$users = User::get();` |
| pluck() | Retrieve a single value from the first result of a query | `$name = User::where('name', 'John')-&gt;pluck('name');` |
| count() | Count the number of records in the query | `$count = User::count();` |
| sum() | Calculate the sum of values in a column | `$total = User::sum('balance');` |
| avg() | Calculate the average of values in a column | `$average = User::avg('age');` |
| min() | Retrieve the minimum value in a column | `$min = User::min('age');` |
| max() | Retrieve the maximum value in a column | `$max = User::max('age');` |

## CRUD

This list of method used for CRUD operations
| Method | Description | Example |
| --------------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| create() | Create a new record | `$user = User::create(['name' =&gt; 'John', 'email' =&gt; 'john@example.com']);` |
| update() | Update an existing record | `$user = User::find(1); $user-&gt;update(['name' =&gt; 'Jane']);` |
| delete() | Delete a record | `$user = User::find(1); $user-&gt;delete();` |

## Relationships

| Method          | Description                                               | Example                                                                                             |
| --------------- | --------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| save()          | Save a new or update an existing record                   | `$user = new User(['name' =&gt; 'John', 'email' =&gt; 'john@example.com']); $user-&gt;save();`      |
| with()          | Eager load relationships with the query                   | `$users = User::with('posts')-&gt;get();`                                                           |
| has()           | Add a constraint for the existence of related records     | `$users = User::has('posts')-&gt;get();`                                                            |
| doesntHave()    | Add a constraint for the non-existence of related records | `$users = User::doesntHave('posts')-&gt;get();`                                                     |
| belongsTo()     | Define a one-to-one relationship                          | `class Post extends Model { public function user() { return $this-&gt;belongsTo('App\User'); } }`   |
| hasOne()        | Define a one-to-one inverse relationship                  | `class User extends Model { public function post() { return $this-&gt;hasOne('App\Post'); } }`      |
| hasMany()       | Define a one-to-many relationship                         | `class User extends Model { public function posts() { return $this-&gt;hasMany('App\Post'); } }`    |
| belongsToMany() | Define a many-to-many relationship                        | `class User extends Model { public function roles() { return $this->belongsToMany('App\Role'); } }` |
| withPivot()     | Access pivot table columns in a many-to-many relationship | `$users = User::find(1)->roles()->withPivot('created_at')->get();`                                  |

## Conditions

| Method         | Description                              | Example                                                                    |
| -------------- | ---------------------------------------- | -------------------------------------------------------------------------- |
| where()        | Add a basic where clause to the query    | `$users = User::where('votes', '>', 100)->get();`                          |
| orWhere()      | Add an or where clause to the query      | `$users = User::where('votes', '>', 100)->orWhere('name', 'John')->get();` |
| whereIn()      | Add a where in clause to the query       | `$users = User::whereIn('id', [1, 2, 3])->get();`                          |
| whereBetween() | Add a where between clause to the query  | `$users = User::whereBetween('votes', [1, 100])->get();`                   |
| whereNull()    | Add a where null clause to the query     | `$users = User::whereNull('updated_at')->get();`                           |
| whereNotNull() | Add a where not null clause to the query | `$users = User::whereNotNull('updated_at')->get();`                        |

## Sorting or Grouping

| Method    | Description                        | Example                                          |
| --------- | ---------------------------------- | ------------------------------------------------ |
| orderBy() | Set the order of the query results | `$users = User::orderBy('name', 'desc')->get();` |
| groupBy() | Group the query results            | `$users = User::groupBy('account_id')->get();`   |
| having()  | Add a having clause to the query   | `$users = User::having('sum', '>', 100)->get();` |

## Limiting Result

This method return data with limit moptions
| Method | Description | Example |
| --------------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| skip() | Skip a number of records in the query | ` $users = User::skip(10)->get();` |
| take() | Take a number of records from the query | `$users = User::take(10)->get();` |

> Note: User in the examples above is the model name and can be replaced with your own model name.
