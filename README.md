
# Laravel base web application for writing comments
## Used technologies
- ```PHP```
- ```Laravel```
- ```MySQL```
- ```TailwindCSS```


## How to run
1. ```git clone https://github.com/Nslkh/cars```
2. Enter you credentials in .env file
     - Database info
    ```
   ...
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=cars
    DB_USERNAME=root
    DB_PASSWORD=
   ...
   
  

## What's made
- `CRUD APP`

## Screenshots
## Main Page
![](https://hosty.xxx/i/54ac4d515b1e0a0aa0e199d46a9cf7e5b0de2e2b.jpg)

## Create
![](https://hosty.xxx/i/60f9cbe2547bc25df210828f36f989065b7cf5d1.jpg)


## More Detailed  APP Instruction

## Creat  laravel app 
- ```laravel new cars```

- ```composer require laravel-frontend-presets/tailwindcss --dev```
- ```php artisan ui tailwindcss```
- ```npm install && npm run dev```

## Model & Migration
- ```php artisan make:model Car -m```

## Controller
- ```php artisan make:controller CarsController --resource```


## Detailed Explanation
- Go to web.php  --create ```route```
- ```Route::resource('/', CarsController::class); ``` Here we want to pull in all the methods that we have in our cars controller 
- Go to CarsController  // We dont need to define every single route in our web.php file  Instead we've  defined them in one  single command
    - ```public function index()```
   - {
       - ```return view('index');```
   -  } 
- Go to resources, views  delete ```welcome.blade.php ``` -- create ```cars folder - index.blade.php```
- Go to resources, views   -- create ```layouts folder - app.blade.php```

## Database
- ```create db and Enter you credentials in .env file```
- ```php artisan migrate```

## How to retrieve data with eloquent 
- Go to Models -- Car  method 
- protected $table = 'cars';
- protected $primaryKey = 'id';// false if u dont want
- Go to CarsController
-   ```$cars = Car::all();```
- return view('index', [
    - ```'cars' => $cars```
- ]);

-  ```In our index.blade.php we are looping and getting data from our db```
## We are done with Index Page

## Proceed with the create method

- return view('cars.create');
- Go to views cars folder - Create ``` create.blade.php```
- Go to CarsController
- $car = new Car;
    - ```$car->name = $request->input('name');```
    - ```$car->founded = $request->input('founded');```
    - ```$car->description = $request->input('description');```
    - ```$car->save();```

##  The other way to create data by Passing array to model

- $car = Car::create([
   - ```'name' => $request->input('name'),```
   - ```'founded' => $request->input('founded'),```
   - ```'description' => $request->input('description'),```
- ]);

- return redirect('/cars')

- Go to Models Car 
- create method     ```protected $fillable = ['name', 'founded', 'description']```

## We are done with Create Page

## Update 
- Go to views cars folder - Create ```edit.blade.php```
- Go to CarsController
- ```$car = Car::find($id)->first();```
   - ```return view('cars.edit')->with('car', $car);```

-  ```$car = Car::where('id', $id)```
    ```- ->update([```
        - ```'name' => $request->input('name'),```
        - ```'founded' => $request->input('founded'),```
        - ```'description' => $request->input('description'),```
- ]);   


## We are done with Update Page

## Delete 
- Go to CarsController
 - $car = Car::find($id)->first();

    - $car->delete();

      -  return redirect('/cars');

## Continuation of the project to make it more functional      

## What is Eloquent Serialization
...
So what we have done so far was doing a request to the DB in order to find one or multiple rows ,
## why serialization is used
 we're returning collection which u can see as an array on steroids but what if u want to convert it into a string thats when u could use serialization ,
- Serialization can be very complex for db records
- Methods
    - To Array
    - To Json
...

