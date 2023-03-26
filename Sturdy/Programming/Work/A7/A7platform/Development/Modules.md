
# Модули

## Как создавать новый модуль

Для того, чтобы создать новый модуль, нужно добавить папку с названием модуля
и внутри нее создать класс который наследуется от `App\Services\Modules\Module`
и имплементировать абстрактный метод `rootDirectory()` который должен
вернуть путь к корневой папке модуля.

```php
namespace App\Modules\Example\ExampleModule;

use App\Services\Modules\Module;

class ExampleModule extends Module
{

    public function rootDirectory() : string
    {
        return __DIR__;
    }

}
```

После этого нужно в файле конфигурации `/app/config/modules.php`
добавить новый модуль в ключ `modules`.

Структура классов в модуле произвольная, но необходимо придерживаться
спецификации PSR-4.

```php
'modules' => [
    // ...
    App\Modules\Example\ExampleModule::class,
    // ...
],
```

## Активация модуля

По умолчанию модуль включен всегда если не передан параметр
`enabled => false` в файл конфигурации `config/{module}.php`

## Роутинг

Модуль автоматически считывает все файлы в папке `routes` и подключает их.
Ничего делать не нужно.

Например, если в папке `routes` есть файл `api.php`
то он подключится автоматически с `api` префиксом и middleware.

Если же в папке `routes` есть файл `web.php`
то он подключится автоматически с `web` middleware.

```
RiskParticipants <- Папка модуля
├───routes
│   └───api.php
│   └───web.php
├───RiskParticipantsModule.php <- Класс модуля
```

Далее пишите роутинг как привыкли:

```php
// modules/RiskParticipants/routes/api.php

use Illuminate\Support\Facades\Route;

Route::get('risk-participants', ...); /
// http://<host>/api/risk-participants
```

Если необходимо изменить путь к файлу роутинга,
То нужно перезаписать метод `routePaths()` в классе модуля.
Необходимо придерживаться фармата массива как в примере.

```php
namespace App\Modules\Example\ExampleModule;

use App\Services\Modules\Module;

class ExampleModule extends Module
{

    public function routePaths() : array {
        // Пути могут быть как строкой так и массивом
        return [
            'web' => 'routes/web.php',
            'api' => ['routes/api.php'],
        ];
    }

}
```

## Конфигурация

Модуль автоматически считывает php-файл в папке `config` в названию
класса модуля без `Module` в snake_case и подключает его.

```
RistParticipants <- Папка модуля
├───config
│   └───risk_participants.php
├───RiskParticipantsModule.php <- Класс модуля
```

Далее можно использовать конфигурацию как обычно

```php
config('risk_participants.example');
```

Чтобы переопределить пути для конфигураций необходимо перезаписать
метод `configPaths()` в классе модуля.