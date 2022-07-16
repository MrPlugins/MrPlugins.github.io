# MY_Config Class

>[!INFO]
> This class is initialized automatically by the system so there is no need to do it manually.
>
> The difference with the original method is that it can also fetch configurations from database

<!-- ?> [*__`item`__* method](#core_my_config_item_method) -->
## <a >*__`item`__* method </a>

Fetch a config file item from database.

```php
/**
* @param   string  $item   Config item name
* @param   string  $index  Index name
* @return  string|null     The configuration item or NULL if the item doesn't exist
*/
public function item($item, $index = '')
```

Use it with regular codeigniter syntax.

```php
$this->config->item('item_name');
```