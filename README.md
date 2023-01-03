1. composer require "darkaonline/l5-swagger"
2. open your config/app.php and add this line: L5Swagger\L5SwaggerServiceProvider::class
3. php artisan vendor:publish --provider "L5Swagger\L5SwaggerServiceProvider"
4. Connect Database.
5. Run: php artisan migrate:fresh --seed
6. Insert the codes in Controller and TodoController
7. Run: php artisan l5-swagger:generate





1. composer require "darkaonline/l5-swagger"
2. php artisan vendor:publish --provider "L5Swagger\L5SwaggerServiceProvider"
3. paste in the .env file
   L5_SWAGGER_CONST_HOST=http://project.test/api/v1
4. paste this in the controller
/**
 * @OA\Info(
 *    title="APIs For Thrift Store",
 *    version="1.0.0",
 * ),
 *   @OA\SecurityScheme(
 *       securityScheme="bearerAuth",
 *       in="header",
 *       name="bearerAuth",
 *       type="http",
 *       scheme="bearer",
 *       bearerFormat="JWT",
 *    ),
 */
5. paste this in HomeController
/**
    * @OA\Post (
    *     path="/api/home",
    *     summary="Home Data",
    *     description="",
    *     tags={"Home"},
    *     @OA\Parameter(
    *         name="name",
    *         in="query",
    *         description="Provide your name",
    *         required=true
    *      ),
    *     @OA\Response(
    *          response=200,
    *          description="OK",
    *          @OA\MediaType(
    *              mediaType="application/json",
    *          )
    *      ),
    *
    * )
*/

public function index(Request $request)
{
    return response()->json([
        'name' => $request->input('name'),
        'message' => 'Hello world!',
    ]);
}

6. paste this in route
Route::post('/home', [HomeController::class, 'index']);

7. Run: php artisan l5-swagger:generate
