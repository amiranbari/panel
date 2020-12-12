Documentation can be found here: https://amiranbari.github.io/panel/

1) Config your database in .env.

2) Run:
`composer require amiranbari/panel:dev-master`

3) Run: `php artisan vendor:publish` - Then select 1.

4) Chang locale to `fa` in `config/app.php`

#### Laravel 8 
Put this in `User.php` in Models directory

`use Spatie\Permission\Traits\HasRoles;`

In User class:
`use HasFactory, Notifiable, HasRoles;`

Add `level` to `fillable` fields.

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
	$this->call(Panel_MenuSeeder::class);
	$this->call(Panel_PermissionSeeder::class);
	$this->call(Panel_UserSeeder::class);
```

- `php artisan migrate --seed`
  
- `php artisan serve`

Go to `127.0.0.1:8000/panel/login`

Email: `admin@gmail.com`
Password: `123456`

Enjoy it.
