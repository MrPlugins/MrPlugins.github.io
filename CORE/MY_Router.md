# MY_Router Class

>[!INFO]
> This class is initialized automatically by the system so there is no need to do it manually.

**Methods**

[fetch_module_class](CORE/MY_Router?id=core_my_router_ext_view_method)\
[fetch_complete_module_class](CORE/MY_Router?id=core_my_router_module_class)

<br/>

## <a id="core_my_router_ext_view_method">*__`fetch_module_class`__* method</a>

Fetch the current module + class (IF class = module will return only module).

```php
/**
* @return string
*/
public function fetch_module_class()
```

Usage

```php
$this->router->fetch_module_class();

// Print string: YOUR_MODULE/YOUR_CONTROLLER
// if module name is equal to controller name
// Print string: YOUR_CONTROLLER -> equal result for $this->router->class
```

<br/><br/>

## <a id="core_my_router_module_class"> *__`fetch_complete_module_class`__* method </a>

Fetch the current module + class.

```php
public function fetch_complete_module_class()
```

Usage

```php
$this->router->fetch_complete_module_class();

// Print string: YOUR_MODULE/YOUR_CONTROLLER
```