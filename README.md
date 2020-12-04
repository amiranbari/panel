See Document here: https://amiranbari.github.io/panel/

config your database in .env

run composer require amiranbari/panel:dev-master

run php artisan vendor:publish - then insert 1 and enter

if you are using laravel8 you should put this in  User.php in Models directory

use Spatie\Permission\Traits\HasRoles;

in User class:
use HasFactory, Notifiable, HasRoles;

add level to fillable fields

chang locale to fa in config/app.php

if you are using laravel7 change composer.json autoload section like below

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
    
if you are using laravel8 change composer.json autoload section like below

   "autoload": {
           "psr-4": {
               "App\\": "app/",
               "Database\\Factories\\": "database/factories/",
               "Database\\Seeders\\": "database/seeders/"
           },
   		"files": [ "app/Tools/helpers.php" ]
       }   
    
run composer dump-autoload

if you are using laravel7 change user provider model in auth.php in config directory like below

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
    
    
add these seeders call in DatabaseSeeder.php

	$this->call(Panel_UserSeeder::class);
	$this->call(Panel_MenuSeeder::class);
	$this->call(Panel_PermissionSeeder::class);
	
php artisan migrate:fresh --seed
  

php artisan serve

go to 127.0.0.1:8000/panel/login

email: admin@gmail.com
password: 123456

enjoy it.

You can see login page below

![alt text](https://github.com/amiranbari/panel/blob/master/images/login.png?raw=true)

You can see Dashboard page below

![alt text](https://github.com/amiranbari/panel/blob/master/images/index.png?raw=true)

You can see Dynamic menu page below

![alt text](https://github.com/amiranbari/panel/blob/master/images/menu.png?raw=true)
