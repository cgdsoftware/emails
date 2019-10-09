# Emails

Emails package is an extesion of the Laravel Enso enviroment, designed for sending emails/notifications.

**Note:** *This package cannot be used outside of enso enviroment and is not included in [Laravel Enso Core](https://github.com/laravel-enso/Core) packages.*

### Features
* friendly display of all stored emails together with their status
* default recipients options such as teams or users
* attachments manangement
* email scheduling management
* email priority
* includes front-end assets

### Instalation
* install the package using composer: `composer require laravel-enso/emails`
* add the following line in `schedule` function in `app\Console\Kernel.php` class:
```
    ...
    protected function schedule(Schedule $schedule)
    {
        //other stuff
        $schedule->job(new ScheduleEmails)->everyMinute();
    }
    ...
```
* Also make sure that `ScheduleEmails` class is imported.

**NOTE** *For local schedule testing, you must first run the command:*
```
php artisan schedule:run
```
* adds the following alias in `webackpack.mix.js`
```
.webpackConfig({
        resolve: {
            extensions: ['.js', '.vue', '.json'],
            alias: {
                 //other aliases
                '@emails': `${__dirname}/vendor/laravel-enso/emails/src/resources/js`,
            },
        },
    })
```
* in `resources/js/router.js` file, verify that `RouteMerger` is imported, or import it

`import RouteMerger from '@core-modules/importers/RouteMerger';`

* make sure `routeImporter` is also imported

`import routeImporter from '@core-modules/importers/routeImporter';`

* then use `RouteMerger` to import front-end assets using the alias defined in `webpack.mix.js`

```
(new RouteMerger(routes))
    .add(routeImporter(require.context('./routes', false, /.*\.js$/)))
    .add(routeImporter(require.context('@emails/routes', false, /.*\.js$/)));
```

* in `resources/js/app.js` import the package's icons

`import '@emails/icons'`

* make sure `hot module replacement` is **not** active, and run `yarn dev` or `npm run dev`

### Publishes
* coming soon..

### Icons
The package uses the following icons:
* `paper-plane`

### Contributions

are welcome. Pull requests are great, but issues are good too.

### License

This package is released under the MIT license.


