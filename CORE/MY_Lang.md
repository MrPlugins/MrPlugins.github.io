# MY_Lang Class

>[!INFO]
> This class is initialized automatically by the system so there is no need to do it manually.


<!-- ?> [*__`line`__* method](#core_my_lang_line_method) -->
## <a >*__`line`__* method </a>

Fetch a single line of text from the language array. Takes variable number\
of arguments and supports wildcards in the form of '%1', '%2', etc.\
Overloaded function.


```php
/**
* @access public
* @return mixed false if not found or the language string
*/
public function line($line, $log_errors = TRUE)
```

Use like php function sprintf.

```php
// Into your language files
$lang['some_key'] = 'Some string with %1 %2.';
```

```php
//the actual usage
echo $this->lang->line('some_key','first','second');

// Print string: Some string with first second.
```
