## APP Instruction

## Creat  laravel app 
- laravel new cars

- composer require laravel-frontend-presets/tailwindcss --dev
- npm install && npm run dev 

## Model & Migration
- php artisan make:model Car -m

## Controller
- php artisan make:controller CarsController --resource


## Detailed Explanation
- Go to web.php  --create route 
- Route::resource('/', CarsController::class);  Here we want to pull in all the methods that we have in our cars controller 
- Go to CarsController  `````// We dont need to define every single route in our web.php file  Instead we've  defined them in one  single command
    public function index()
    {
        return view('index');
    } ````` 
- Go to resources, views  delete welcome.blade.php  -- create cars folder - index.blade.php