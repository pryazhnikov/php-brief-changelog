# PHP Changes Timeline

## Changelog

### 30 Nov 2017: PHP 7.2.0 was released

#### Added
* A new type, `object`, has been introduced that can be used for (contravariant) parameter typing and (covariant) return typing of any objects.

#### Changed
* Parameter types from overridden methods and from interface implementations may now be omitted.
* Abstract methods can now be overridden when an abstract class extends another abstract class
* Shared extensions no longer require their file extension (.so for Unix or .dll for Windows) to be specified. This is enabled in the php.ini file, as well as in the `dl()` function.
* The MCrypt extension has now been moved out of the core to PECL. Given the mcrypt library has not seen any updates since 2007, its usage is highly discouraged. Instead, either the [OpenSSL](http://php.net/manual/en/book.openssl.php) or [Sodium](http://php.net/manual/en/book.sodium.php) extension should be used.
* Unquoted strings that are non-existent global constants are taken to be strings of themselves. This behaviour used to emit an E_NOTICE, but will now emit an E_WARNING. In the next major version of PHP, an Error exception will be thrown instead.

#### Deprecated
* The `__autoload()` method has been deprecated because it is inferior to `spl_autoload_register()` 
* Given the security issues of `create_function()` function, this dated function has been deprecated. The preferred alternative is to use anonymous functions.
* `each()` function is far slower at iteration than a normal foreach, and causes implementation issues for some language changes. It has therefore been deprecated.

#### Removed
* The `sql.safe_mode` ini setting has now been removed.

### 01 Dec 2016: PHP 7.1.0 was released

### 21 Jul 2016: the end of life date for PHP 5.5

PHP 5.5 became an unsupported branch. The last release was 5.5.37.

### 03 Dec 2015: PHP 7.0.0 was released

### 03 Sep 2015: the end of life date for PHP 5.4

PHP 5.4 became an unsupported branch. The last release was 5.4.45.

### 28 Aug 2014: PHP 5.6.0 was released

### 14 Aug 2014: the end of life date for PHP 5.3

PHP 5.3 became an unsupported branch. The last release was 5.3.29.

### 20 Jun 2013: PHP 5.5.0 was released

### 01 Mar 2012: PHP 5.4.0 was released

### 06 Jan 2011: the end of life date for PHP 5.2

PHP 5.2 became an unsupported branch. The last release was 5.2.17.

### 30 Jun 2009: PHP 5.3.0 was released

### 07 Aug 2008: the end of life date for 4.4

The end of life for PHP 4.4 also marks the end of life for PHP 4 as a whole.

### 02 Nov 2006: PHP 5.2.0 was released

### 24 Aug 2006: the end of life date for PHP 5.1 

PHP 5.1 became an unsupported branch. The last release was 5.1.6.

### 24 Nov 2005: PHP 5.1.0 was released

### 05 Sep 2005: the end of life date for PHP 5.0

PHP 5.0 became an unsupported branch. The last release was 5.0.5.

### 13 Jul 2004: PHP 5.0.0 was released

## Data Sources

* http://php.net/releases/
* http://php.net/supported-versions.php
* http://php.net/manual/en/appendices.php
* http://php.net/ChangeLog-7.php
* http://php.net/ChangeLog-5.php
* http://php.net/eol.php
