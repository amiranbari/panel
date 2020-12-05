Documentation can be found here: https://amiranbari.github.io/panel/

1) Config your database in .env.

2) Run:
`composer require amiranbari/panel:dev-master`

3) Run: `php artisan vendor:publish` - Then select 1.

#### Laravel 8 
Put this in `User.php` in Models directory

`use Spatie\Permission\Traits\HasRoles;`

In User class:
`use HasFactory, Notifiable, HasRoles;`

Add `level` to `fillable` fields.

Chang locale to `fa` in `config/app.php`

Change `composer.json` autoload section like below"
```
   "autoload": {
           "psr-4": {
               "App\\": "app/",
               "Database\\Factories\\": "database/factories/",
               "Database\\Seeders\\": "database/seeders/"
           },
   		"files": [ "app/Tools/helpers.php" ]
       }   
 ```
 
#### Laravel 7 

Change `composer.json` autoload section like below
```
   "autoload": {
        "psr-4": {
            "App\\": "app/"
        },
        "classmap": [
            "database/seeds",
            "database/factories",
            "app/Models/"
        ],
        "files": [
            "app/Tools/helpers.php"
        ]
    }
```
Run: `composer dump-autoload`

Change user provider model in `auth.php` in config directory like below:
```
    'providers' => [
        'users' => [
            'driver' => 'eloquent',
            'model' => App\Models\User::class,
        ],

        // 'users' => [
        //     'driver' => 'database',
        //     'table' => 'users',
        // ],
    ],
    
 ```   
Add these seeders call in `DatabaseSeeder.php`:
```
	$this->call(Panel_UserSeeder::class);
	$this->call(Panel_MenuSeeder::class);
	$this->call(Panel_PermissionSeeder::class);
```

- `php artisan migrate:fresh --seed`
  
- `php artisan serve`

Go to `127.0.0.1:8000/panel/login`

Email: `admin@gmail.com`
Password: `123456`

Enjoy it.

You can see login page below

![alt text](https://github.com/amiranbari/panel/blob/master/images/login.png?raw=true)

You can see Dashboard page below

![alt text](https://github.com/amiranbari/panel/blob/master/images/index.png?raw=true)

You can see Dynamic menu page below

![alt text](https://github.com/amiranbari/panel/blob/master/images/menu.png?raw=true)
