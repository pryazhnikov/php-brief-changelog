# PHP Brief Changelog

A brief overview of PHP language changes using [keep a changelog](http://keepachangelog.com/en/1.0.0/) principles.

The main goal of this project is to build the changes summary of PHP language.

## Changelog

### 2022-12-08: PHP 8.2.0 was released

### 2022-11-28: the end of life date for PHP 7.4

PHP 7.3 became an unsupported branch. The last release was 7.4.33.

### 2021-12-06: the end of life date for PHP 7.3

PHP 7.3 became an unsupported branch. The last release was 7.3.33.

### 2021-11-25: PHP 8.1.0 was released

### 2020-11-30: the end of life date for PHP 7.2

PHP 7.2 became an unsupported branch. The last release was 7.2.34.

### 2020-11-26: PHP 8.0.0 was released


### 2019-12-01: the end of life date for PHP 7.1

PHP 7.1 became an unsupported branch. The last release was 7.1.33.

### 2019-11-28: PHP 7.4.0 was released

#### Added

* Added FFI: a new extension, which provides a simple way to call native functions, access native variables, and create/access data structures defined in C libraries. ([documentation](https://www.php.net/manual/en/book.ffi.php))
* Typed properties
* Arrow functions ([documentation](https://www.php.net/manual/en/functions.arrow.php))
* Null coalescing assignment operator
  
  Usage example: `$array['key'] ??= computeDefault();`
* Unpacking inside arrays
* Numeric literal separator (value example: `1_000_000`)
* Weak references ([documentation](https://www.php.net/manual/en/class.weakreference.php))
* Added the `mb_str_split()` function, which provides the same functionality as str_split(), but operating on code points rather than bytes.

#### Changed

* Trying to use values of type `null`, `bool`, `int`, `float` or resource as an array (such as `$null["key"]`) will now generate a notice.
* `fn` is now a reserved keyword. In particular, it can no longer be used as a function or class name. It can still be used as a method or class constant name.

#### Deprecated

* Curly brace syntax for accessing array elements and string offsets is deprecated ([RFC](https://wiki.php.net/rfc/deprecate_curly_braces_array_access))
* `(real)` cast and `is_real()` function are deprecated.
  
  Use `(float)` and `is_float()` instead.
* The `money_format()` function is deprecated. It can be replaced by the intl `NumberFormatter` functionality.
* Nested ternary operations must explicitly use parentheses to dictate the order of the operations.

#### Security

* As of PHP 7.4.11, the _names_ of incoming cookies are no longer url-decoded for security reasons.

### 2019-01-10: the end of life date for PHP 7.0

PHP 7.0 became an unsupported branch. The last release was 7.0.33.

### 2018-12-31: the end of life date for PHP 5.6

PHP 5.6 became an unsupported branch. The last release was 5.6.40.

### 2018-12-06: PHP 7.3.0 was released

#### Added

* Added support for references in `list()` and array destructuring ([RFC](https://wiki.php.net/rfc/list_reference_assignment)).
* Trailing commas in function and method calls are now allowed.
* Added support for the SameSite cookie directive.
* Added `array_key_first()` & `array_key_last()` functions.
* Added `is_countable()` function.
* Added `hrtime()` function to get high resolution time.

#### Changed

* Implemented flexible heredoc and nowdoc syntax ([RFC](https://wiki.php.net/rfc/flexible_heredoc_nowdoc_syntaxes)).
* The Multibyte String data tables have been updated for Unicode 11.
* Performance of the Multibyte String extension has been significantly improved across the board.
* The PCRE extension has been upgraded to PCRE2, which may cause minor behavioral changes ([RFC](https://wiki.php.net/rfc/pcre2-migration)).
* If an SPL autoloader throws an exception, following autoloaders will not be executed. Previously all autoloaders were executed and exceptions were chained.
* The cyclic GC has been enhanced, which may result in considerable performance improvements.

#### Deprecated

* The declaration and use of case-insensitive constants has been deprecated.
* Declaring a function called `assert()` inside a namespace is deprecated.

#### Fixed

* `mysqli` & `pdo_mysql` extensions: prepared statements now properly report the fractional seconds for `DATETIME`, `TIME` and `TIMESTAMP` columns with decimals specifier (e.g. `TIMESTAMP(6)` when using microseconds). Formerly, the fractional seconds part was simply omitted from the returned values.

#### Security

* As of PHP 7.3.23, the names of incoming cookies are no longer url-decoded for security reasons.

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
