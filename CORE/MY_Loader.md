# MY_Loader Class

>[!INFO]
> This class is initialized automatically by the system so there is no need to do it manually.

**Methods**

[ext_view](CORE/MY_Loader?id=core_my_loader_ext_view_method)\
[module](CORE/MY_Loader?id=core_my_loader_module_method)\
[database](CORE/MY_Loader?id=core_my_loader_database_method)

<br/><br/>

## <a id="core_my_loader_ext_view_method">*__`ext_view`__* method </a>

<!-- <a id="core_my_loader_ext_view_method">

?> *__`ext_view`__* method

</a> -->

Loading view outside main view folder.

```php
/**
* @param  string  $view   view to load
* @param  array   $vars   data to pass to view
* @param  boolean $return Set to TRUE if you want to return the value rather than add to the view (Defaults to FALSE)
* @return mixed
*/
public function ext_view($view, $vars = [], $return = FALSE)
```

Use it like a normal view.

```php
$this->load->ext_view('YOUR_VIEW'...)
```

<br/><br/>

## <a id="core_my_loader_module_method">*__`module`__* method </a>

<!-- <a id="core_my_loader_module_method">

?> *__`module`__* method

</a> -->

Load a module controller with alias.

```php
public function module($module, $params = NULL, $alias = FALSE)
```

<br/><br/>

## <a id="core_my_loader_database_method">*__`database`__* method </a>

<!-- <a id="core_my_loader_database_method">

?> *__`database`__* method

</a> -->

Load the database drivers.\
To load MY_DB_mysql_driver class too if file exists into libraries,\
it's is usefull to perform pagination for _main_query method of MY_model

```php
public function database($params = '', $return = FALSE, $query_builder = NULL)
```
> [!WARNING]
> This is a technical method, no need to use it.