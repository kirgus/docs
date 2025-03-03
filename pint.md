---
git: 535e79c4e6681738769d93695c34dcd51d832d71
---

# Laravel Pint

<a name="introduction"></a>
## Введение

[Laravel Pint](https://github.com/laravel/pint) - это оптимизированный инструмент для форматирования кода на PHP для минималистов. Pint построен на основе PHP-CS-Fixer и обеспечивает простой способ поддержания чистого и последовательного стиля кода.

Pint автоматически устанавливается с каждым новым приложением Laravel, так что вы можете начать использовать его сразу. По умолчанию Pint не требует какой-либо настройки и автоматически исправляет проблемы со стилем кода в вашем коде, следуя оптимизированному стилю кодирования Laravel.

<a name="installation"></a>
## Установка

Pint включен в последние версии фреймворка Laravel, поэтому установка обычно не требуется. Однако для старых приложений вы можете установить Laravel Pint через Composer:
```shell
composer require laravel/pint --dev
```

<a name="running-pint"></a>
## Запуск Pint

Вы можете указать Pint исправить проблемы со стилем кода, вызвав двоичный файл `pint`, который доступен в каталоге `vendor/bin` вашего проекта:

```shell
./vendor/bin/pint
```

Вы также можете запустить Pint для определенных файлов или каталогов:

```shell
./vendor/bin/pint app/Models

./vendor/bin/pint app/Models/User.php
```

Pint отобразит подробный список всех файлов, которые он обновляет. Вы можете просмотреть еще больше информации об изменениях сделанных Pint, указав опцию `-v` при вызове Pint:

```shell
./vendor/bin/pint -v
```

Если вы хотите, чтобы Pint просто проверил ваш код на наличие ошибок стиля, не внося изменения в файлы, вы можете использовать опцию `--test`:

```shell
./vendor/bin/pint --test
```

Если вы хотите, чтобы Pint модифицировал только те файлы, которые имеют незафиксированные изменения согласно Git, вы можете использовать опцию `--dirty`:

```shell
./vendor/bin/pint --dirty
```

<a name="configuring-pint"></a>
## Настройка Pint

Как уже упоминалось, для Pint не требуется какая-либо конфигурация. Однако, если вы хотите настроить предустановки, правила или проверяемые папки, вы можете сделать это, создав файл `pint.json` в корневом каталоге вашего проекта:

```json
{
  "preset": "laravel"
}
```

Кроме того, если вы хотите использовать файл `pint.json` из определенного каталога, вы можете указать опцию `--config` при вызове Pint:

```shell
pint --config vendor/my-company/coding-style/pint.json
```

<a name="presets"></a>
### Предустановки (Presets)

Предустановки определяют набор правил, которые могут использоваться для исправления проблем со стилем кода в вашем коде. По умолчанию Pint использует предустановку `laravel`, которая исправляет проблемы, следуя оптимизированному стилю кодирования Laravel. Однако вы можете указать другую предустановку, предоставив опцию `--preset` Pint:

```shell
pint --preset psr12
```

Если хотите, вы также можете установить предустановку в файле `pint.json` вашего проекта:

```json
{
  "preset": "psr12"
}
```

В настоящее время поддерживаемые предустановки Pint следующие: `laravel`, `per`, `psr12` и `symfony`.

<a name="rules"></a>
### Правила

Правила - это стандарты стиля, которые Pint будет использовать для исправления проблем со стилем кода в вашем коде. Как уже упоминалось выше, предустановки - это предопределенные группы правил, которые подходят для большинства проектов на PHP, поэтому обычно вам не нужно беспокоиться о отдельных правилах, которые они содержат.

Однако, если вы хотите, вы можете включить или отключить определенные правила в вашем файле `pint.json`:

```json
{
  "preset": "laravel",
  "rules": {
    "simplified_null_return": true,
    "braces": false,
    "new_with_braces": {
      "anonymous_class": false,
      "named_class": false
    }
  }
}
```

Pint построен на основе [PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer). Поэтому вы можете использовать любые из его правил для исправления проблем стиля кода в вашем проекте: [Конфигуратор PHP-CS-Fixer](https://mlocati.github.io/php-cs-fixer-configurator).
<a name="excluding-files-or-folders"></a>
### Исключение файлов / каталогов

По умолчанию Pint будет проверять все файлы `.php` в вашем проекте, за исключением тех, которые находятся в каталоге `vendor`. Если вы хотите исключить больше каталогов, вы можете сделать это, используя опцию конфигурации `exclude`:

```json
{
  "exclude": [
    "my-specific/folder"
  ]
}
```

Если вы хотите исключить все файлы, подходящие под определенный шаблон имени, вы можете сделать это, используя опцию конфигурации `notName`:

```json
{
  "notName": [
    "*-my-file.php"
  ]
}
```

Если вы хотите исключить файл, указав точный путь к нему, вы можете сделать это, используя опцию конфигурации `notPath`:

```json
{
  "notPath": [
    "path/to/excluded-file.php"
  ]
}
```
