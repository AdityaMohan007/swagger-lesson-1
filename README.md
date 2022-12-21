1. composer require "darkaonline/l5-swagger"
2. open your config/app.php and add this line: L5Swagger\L5SwaggerServiceProvider::class
3. php artisan vendor:publish --provider "L5Swagger\L5SwaggerServiceProvider"
4. Connect Database.
5. Run: php artisan migrate:fresh --seed
6. Insert the codes in Controller and TodoController
7. Run: php artisan l5-swagger:generate
