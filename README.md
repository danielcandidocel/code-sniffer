# Coding Standard

## Table of contents

- [Requirements](#requirements)
- [How to install](#how-to-install)
    - [Enabling the rules](#enabling-the-rules)
    - [Sniffing code](#sniffing-code)
    - [Sniffing code in PHPStorm](#sniffing-code-in-phpstorm)
- [Change log](#change-log)



## Requirements

- [squizlabs/php_codesniffer](https://github.com/squizlabs/PHP_CodeSniffer) 3.6 or higher

## How to install

```bash
composer require dcandido/quality-tools --dev
```

## How to use

### Enabling the rules

Add it to your project `phpcs.xml` or `phpcs.xml.dist` ruleset:

```xml
<?xml version="1.0"?>
<ruleset name="IMSRuleset">
  <description>The coding standard for AccPayable.</description>

  <rule ref="./vendor/dcandido/quality-tools/ruleset.xml"/>

  <file>app</file>
  <file>bootstrap</file>

  <exclude-pattern>bootstrap/cache/*</exclude-pattern>
  <exclude-pattern>tests/Unit/*</exclude-pattern>
  <exclude-pattern>resources</exclude-pattern>
  <exclude-pattern>bootstrap/autoload.php</exclude-pattern>
  <exclude-pattern>*/migrations/*</exclude-pattern>
  <exclude-pattern>*/seeds/*</exclude-pattern>
  <exclude-pattern>vendor/*</exclude-pattern>
  <exclude-pattern>public/*</exclude-pattern>
  <exclude-pattern>*.js</exclude-pattern>

  <!-- Show progression -->
  <arg value="pv"/> <!-- p for progress, s to see list for each gitblame author, v to see authors with no violations, s include source codes in the report -->
  <arg name="report" value="summary"/><!-- summary, gitblame, source -->
  <arg name="colors"/>
</ruleset>
```

### Sniffing code

The following commands can be added to the `scripts` section of your `composer.json` file to check and fix invalid code. Some optional checks are also included to illustrate how they might work together to check all your code.

```json
{
    "scripts": {
        "composer-validate": "@composer validate --no-check-all --strict",
        "codesniffer-check": "vendor/bin/phpcs --runtime-set ignore_errors_on_exit 1 --runtime-set ignore_warnings_on_exit 1",
        "codesniffer-fix": "vendor/bin/phpcbf --runtime-set ignore_errors_on_exit 1 --runtime-set ignore_warnings_on_exit 1 || exit 0",
        "test": "vendor/bin/phpunit",
        "check": [
            "@composer-validate",
            "@codesniffer-check",
            "@test"
        ]
    }
}
```

### Sniffing code in PHPStorm

See [PHP Code Sniffer in PhpStorm](https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm) on how to set up CodeSniffer in PHPStorm.

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.
