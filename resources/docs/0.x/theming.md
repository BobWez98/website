# Theming

---

- [Views](#views)
- [Blade Directives](#blade-directives)
- [CSS](#css)
- [Javascript](#javascript)

The base theming is located within `rapidez/core` but you can create your own package with all the views, css and js.

<a name="views"></a>
## [Views](#views)

To change the views you can publish them with:
```bash
php artisan vendor:publish --provider="Rapidez\Core\RapidezServiceProvider" --tag=views
```
> {info} It's recommended to only add the views you've changed into your source control for upgradability. To keep track of what you've changed in a view it's a good idea to add the unchanged version to version control before you make any changes.

<a name="blade-directives"></a>
## [Blade Directives](#blade-directives)

Rapidez provides some Blade Directives to easily get information from Magento.

> {info} Keep in mind the output of these directives are cached! So after changing a configuration, block or widget the cache needs te be cleared. See the [caching docs](/{{route}}/{{version}}/caching).

### `@config`

Get a config value for the current store scope with optionally a fallback, example:
```blade
@config('general/locale/timezone', 'Europe/Amsterdam')
```

### `@block`

Get the block contents for the current store scope:
```blade
@block('your_block_identifier')
```

### `@widget`

Get the widget contents for the current store scope:
```blade
@widget('location', 'type', 'handle', $entityId)
```
Have a look at the [current widget locations](https://github.com/rapidez/core/search?l=Blade&q=widget) we've added by default and the widget tables in the database to see how the parameters work.

> {info} Widgets are currently not fully supported. Just simple ones with blocks work fine.

<a name="css"></a>
## [CSS](#css)

Use TailwindCSS as we've done with the base styling or change the `webpack.mix.js` file and use whatever you want. Have a look at the [Laravel Mix docs](https://laravel.com/docs/8.x/mix) for all the available options.

<a name="javascript"></a>
## [Javascript](#javascript)

In `resources/js/app.js` there is just a `require` so you can extend easily. If you'd like to change or overwrite something you can copy the content of the required file and change the parts you'd like.
