- `composer global require laravel/installer`
- `composer create-project laravel/laravel test2`
- в `composer.json` добавляем:
```
  "repositories": [
    {
        "type": "vcs",
        "url": "ssh://root@206.189.105.187:22022/A7/package.platform.git"
    }
],
```
в `require` добавляем:
```
"a7kz/platform": "^1.0"
```
- создаем файл `database/database.sqlite`
- `composer update`
- Do you trust "funkjedi/composer-include-files" to execute code and wish to enable it now? (writes "allow-plugins" to composer.json) [y,n,d,?] y
- в `/config/app` добавляем `\A7kz\Platform\CoreServiceProvider::class,`
- В `composer.json` в поле `extra` добавляем:
```
"extra": {
    "include_files": [
        "vendor/a7kz/platform/src/helpers.php"
    ],
    "laravel": {
        "dont-discover": []
    }
},
```
- В `.env` меняем базу на:
```
DB_CONNECTION=sqlite
#DB_HOST=127.0.0.1
#DB_PORT=3306
#DB_DATABASE=laravel
#DB_USERNAME=root
#DB_PASSWORD=
```

- `php artisan platform:install --install --force`
- `php artisan platform:install --publish --force`
- `npm install`
- `npm run prod`
- `composer dump-autoload`

