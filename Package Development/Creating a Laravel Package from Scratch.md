# Making a Laravel Package

1. Make a new **Laravel** project
2. Create a new **Package** folder in the root dir
3. Create a new folder (i.e. `contact`) in the Package dir
4. Initialize **Composer** in the contact folder (`composer init`)
	- Enter the corresponding details
		- <vendor_name>\<package_name> like `namespace Ekown\Contact;`
		- Package Description
		- Package Type (usually is `library`)
		- License (standard is `MIT`)
		- Author Name and Email
		- Minimum Stability (i.e. `dev` or `stable`)
		- Required Dependencies (`no`)
		- Required Dev Dependencies (`no`)
5. Change or modify any of the details you have entered above in the `composer.json` file
6. Add the `src` folder. This is where the code of the package would be placed.
7. Create the **Service Provider** for your package (i.e. `ContactServiceProvider.php`) and place it inside the `src` directory
	7.1. Add a namespace, it is usually in this <username>/<package_name> format (i.e. `Ekown/Contact`)
	7.2. Add a use case of Laravel Illuminate's `ServiceProvider` abstract class (i.e. `Illuminate/Support/ServiceProvider`)
	7.3. Extend the **ServiceProvider** class to the created Service Provider class of the package
	7.4. Add two public methods (`boot` and `register`)
8. Add a **PSR-4 autoloader** in the `composer json` file of the package for the namespace of the **ServiceProvider** and point it into the src directory
```	
"autoload": {
    "psr-4": {
        "Ekown\\Contact\\": "src/"
    }
}
```
9. Run the autoload dumper (`composer dump-autoload`)
10. Add the package namespace to the composer json file in the **project's root directory** in the **dev autoload** part
```
"autoload-dev": {
    "psr-4": {
        "Tests\\": "tests/",
        "Ekown\\Contact\\": "packages/contact/src/"
    }
},
```
11. Repeat step#9 for the project root directory
12. Add the **whole** provider namespace in the project's app config file (config/app.php)
```
/*
 * Package Service Providers...
 */
Ekown\Contact\ContactServiceProvider::class,
/*
```
13. Complete!
		
