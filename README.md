<p align="center"><img src="https://res.cloudinary.com/dtfbvvkyp/image/upload/v1566331377/laravel-logolockup-cmyk-red.svg" width="400"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 1500 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[Many](https://www.many.co.uk)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- **[OP.GG](https://op.gg)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).


## Laravel 7 Database Seeder Example
- In this Section, i will show you how to create database seeder in laravel 7 and what is command to create seeder and how to run that seeder in laravel 7. so you have to just follow few step get how it's done.

#### Step 1. Basic Configuration
- For creating a new project, new need to run the below command in your terminal, laravel new `laravel-seeder`
- Now, we need to connect this newly created laravel project with the database.
- Go to your database administration tool ( `sequel pro, phpMyAdmin etc.` ) and make a new database and give it a name `laravel-seeder`
- To connect database and laravel project each other, we should change the .env file of project.
- Open your editor and change the below lines in `.env` file.
- Customize at `AppServiceProvider.php` in `project\app\Providers`
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel-seeder
DB_USERNAME=root
DB_PASSWORD=
```
- Various fields are host number, port number, database name, username, password etc.
- Change these fields as per your computer configurations and now you have connected your database and laravel project.

#### Step 2. Creating a Seeder
- Laravel gives command to create seeder in laravel. so you can run following command to make seeder in laravel application.
- Create Seeder Command:
```
php artisan make:seeder UserSeeder
```
- after run above commands, it will create one file `UserSeeder.php`,  on seeds folder. All seed classes are stored in the database/seeds directory.
- Then you can write code of create admin user using model in laravel.

- `database/seeds/UserSeeder.php`
```
<?php

use Illuminate\Database\Seeder;
use App\User;

class UserSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        User::create([
            'name' => 'John',
            'email' => 'John@gmail.com',
            'password' => bcrypt('12345678'),
        ]);
        User::create([
            'name' => 'Ronald',
            'email' => 'Ronald@gmail.com',
            'password' => bcrypt('12345678'),
        ]);
        User::create([
            'name' => 'Gary',
            'email' => 'Gary@gmail.com',
            'password' => bcrypt('12345678'),
        ]);
    }
}
```

## Way 1: Run Single Seeder
```
php artisan db:seed --class=UserSeeder
```

##  Way 2: Run All Seeders
- In this way, you have to declare your seeder in DatabaseSeeder class file. then you have to run single command to run all listed seeder class.
- So can list as bellow:
- `database/seeds/DatabaseSeeder.php`
```
<?php

use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        $this->call(UserSeeder::class);
    }
}
```
- Now you need to run following command for run all listed seeder:

`php artisan db:seed`

#### If you want to rollback and rerun all migrations, and then reseed:
- `$ php artisan migrate:refresh --seed`
- The migrate:refresh --seed command is a shortcut to these 3 commands:
```
    $ php artisan migrate:reset     # rollback all migrations
    $ php artisan migrate           # run migrations
    $ php artisan db:seed           # run seeders
```
- Now i think you will understand how seeding is work and we have to use in our laravel app.
- I hope it can help you...

