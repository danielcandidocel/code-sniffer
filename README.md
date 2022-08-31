# Coding Standard

## Table of contents

- [Requirements](#requirements)
- [How to install](#how-to-install)
    - [Enabling the rules](#enabling-the-rules)
    - [Sniffing code in PHPStorm](#sniffing-code-in-phpstorm)



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

### Usage

Run Command:
```bash
./vendor/bin/phpcs
```

### Sniffing code in PHPStorm

See [PHP Code Sniffer in PhpStorm](https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm) on how to set up CodeSniffer in PHPStorm.
