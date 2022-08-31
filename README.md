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

If you have errors, you will see the following:

```bash
$ phpcs 

FILE: /path/to/code/file1.php
--------------------------------------------------------------------------------
FOUND 5 ERROR(S) AFFECTING 5 LINE(S)
--------------------------------------------------------------------------------
  2 | ERROR | Missing file doc comment
 20 | ERROR | PHP keywords must be lowercase; expected "false" but found "FALSE"
 47 | ERROR | Line not indented correctly; expected 4 spaces but found 1
 51 | ERROR | Missing function doc comment
 88 | ERROR | Line not indented correctly; expected 9 spaces but found 6
--------------------------------------------------------------------------------

FILE: /path/to/code/file2.php
--------------------------------------------------------------------------------
FOUND 1 ERROR(S) AND 1 WARNING(S) AFFECTING 1 LINE(S)
--------------------------------------------------------------------------------
 21 | ERROR   | PHP keywords must be lowercase; expected "false" but found
    |         | "FALSE"
 21 | WARNING | Equals sign not aligned with surrounding assignments
--------------------------------------------------------------------------------
````

You can run phpcbf to fix the errors automatically:
```bash
./vendor/bin/phpcbf
```
```bash
PHPCBF RESULT SUMMARY
----------------------------------------------------------------------
FILE                                                  FIXED  REMAINING
----------------------------------------------------------------------
.../path/to/code/file.php                               7      0
.../path/to/code/file2.php                              5      0
```

### Sniffing code in PHPStorm

See [PHP Code Sniffer in PhpStorm](https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm) on how to set up CodeSniffer in PHPStorm.
