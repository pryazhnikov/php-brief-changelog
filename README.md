# PHP Changes Timeline

A brief overview of PHP language changes using [keep a changelog](http://keepachangelog.com/en/1.0.0/) principles.

## Changelog

### 2017-11-30: PHP 7.2.0 was released

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

### 2016-12-01: PHP 7.1.0 was released

#### Added
* A `void` return type has been introduced. Functions declared with void as their return type must either omit their return statement altogether, or use an empty return statement. NULL is not a valid return value for a void function.
* Support for specifying the visibility of class constants has been added.
* A new pseudo-type (similar to callable) called *iterable* has been introduced. It may be used in parameter and return types, where it accepts either arrays or objects that implement the Traversable interface.
* Multiple exceptions per catch block may now be specified using the pipe character (`|`). This is useful for when different exceptions from different class hierarchies are handled the same.
* A new function called `pcntl_async_signals()` has been introduced to enable asynchronous signal handling without using ticks.
* Adding new `is_iterable` function.

#### Changed
* Type declarations for parameters and return values can now be marked as *nullable* by prefixing the type name with a question mark. This signifies that as well as the specified type, NULL can be passed as an argument, or returned as a value, respectively.
* The shorthand array syntax (`[]`) may now be used to destructure arrays for assignments (including within *foreach*), as an alternative to the existing `list()` syntax, which is still supported.
* Variables bound to a closure via the use construct cannot use the same name as any superglobals, `$this`, or any parameter.
* You can now specify keys in `list()`, or its new shorthand `[]` syntax. This enables destructuring of arrays with non-integer or non-sequential keys.
* Support for negative string offsets has been added to the string manipulation functions accepting offsets, as well as to string indexing with `[]` or `{}`. In such cases, a negative offset is interpreted as being an offset from the end of the string.
* Previously, a warning would be emitted for invoking *user-defined functions with too few arguments*. Now, this warning has been promoted to an Error exception. This change only applies to user-defined functions, not internal functions.
* `void` and `iterable` cannot be used to name classes, interfaces, or traits.
* Applying the empty index operator to a string (e.g. `$str[] = $x`) throws a fatal error instead of converting silently to array.
* Session IDs will no longer be hashed upon generation. With this change brings about the removal of the following four ini settings: `session.entropy_file`, `session.entropy_length`, `session.hash_function`, `session.hash_bits_per_character`.

#### Fixed
* `DateTime` and `DateTimeImmutable` now properly incorporate microseconds when constructed from the current time, either explicitly or with a relative string (e.g. "first day of next month"). This means that naive comparisons of two newly created instances will now more likely return FALSE instead of TRUE.

### 2016-07-21: the end of life date for PHP 5.5

PHP 5.5 became an unsupported branch. The last release was 5.5.37.

### 2015-12-03: PHP 7.0.0 was released

#### Added
* PHP 7 adds support for *return type declarations*
* The null coalescing operator (`??`) has been added as syntactic sugar for the common case of needing to use a ternary in conjunction with `isset()`
* The spaceship operator is used for comparing two expressions. It returns -1, 0 or 1 when `$a` is respectively less than, equal to, or greater than `$b`.
* Support for anonymous classes has been added via `new class`.

#### Changed
* Array constants can now be defined with `define()`. In PHP 5.6, they could only be defined with `const`.
* Filtered `unserialize()`
* `list()` can no longer unpack string variables. `str_split()` should be used instead.
* `dirname()` now optionally takes a second parameter, **depth**, to get the name of the directory depth levels up from the current directory.
* `setlocale()` function no longer accepts category passed as string. `LC_*` constants must be used instead.
* FPM SAPI module: In PHP 5, a listen directive with only a port number would listen on all interfaces, but only on IPv4. PHP 7 will now accept requests made via both IPv4 and IPv6.

#### Deprecated
* PHP 4 style constructors (methods that have the same name as the class they are defined in) are deprecated, and will be removed in the future.
* Static calls to methods that are not declared static are deprecated, and may be removed in the future.
* The `salt` option for the `password_hash()` function has been deprecated to prevent developers from generating their own (usually insecure) salts. The function itself generates a cryptographically secure salt when no salt is provided by the developer - therefore custom salt generation should not be needed.

#### Removed
* Removed extensions: `ereg`, `mssql`, `mysql`.
* Removed SAPIs: `apache`, `apache_hooks`, `apache2filter`, etc
* Removal of date.timezone Warning
> Previously, a warning was emitted if the date.timezone INI setting had not been set prior to using any date- or time-based functions. Now, this warning has been removed (with date.timezone still defaulting to UTC).

### 2015-09-03: the end of life date for PHP 5.4

PHP 5.4 became an unsupported branch. The last release was 5.4.45.

### 2014-08-28: PHP 5.6.0 was released

### 2014-08-14: the end of life date for PHP 5.3

PHP 5.3 became an unsupported branch. The last release was 5.3.29.

### 2013-06-20: PHP 5.5.0 was released

### 2012-03-01: PHP 5.4.0 was released

### 2011-01-06: the end of life date for PHP 5.2

PHP 5.2 became an unsupported branch. The last release was 5.2.17.

### 2009-06-30: PHP 5.3.0 was released

### 2008-08-07: the end of life date for 4.4

The end of life for PHP 4.4 also marks the end of life for PHP 4 as a whole.

### 2006-11-02: PHP 5.2.0 was released

### 2006-08-24: the end of life date for PHP 5.1 

PHP 5.1 became an unsupported branch. The last release was 5.1.6.

### 2005-11-24: PHP 5.1.0 was released

### 2005-09-05: the end of life date for PHP 5.0

PHP 5.0 became an unsupported branch. The last release was 5.0.5.

### 2004-07-13: PHP 5.0.0 was released

## Data Sources

* http://php.net/releases/
* http://php.net/supported-versions.php
* http://php.net/manual/en/appendices.php
* http://php.net/ChangeLog-7.php
* http://php.net/ChangeLog-5.php
* http://php.net/eol.php
