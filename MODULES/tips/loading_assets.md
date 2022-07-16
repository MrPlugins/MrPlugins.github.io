You can load assets in different ways within your controllers or views.\

*__inCIpit__* integrates [Stencil](https://github.com/MrPlugins/stencil ':target=_blank'), a template engine that has been customized and enriched with different methods and functions.\
See [Stencil helper](HELPERS/stencil.md) and [library](LIIBRARIES/stencil.md)

## assets_dependences_loader.php

The most important method is the `extra_assets_load` used by the `set_assets_method` method in [Shared_Controller](CORE/My_controller?id=-shared_controller-class-):\
in each module, in the root, you can create a file called `assets_dependences_loader.php` and inside create an array of assets to load into the various methods of your controller.

Structure of an assets_dependences_loader.php file:
```php
$assets_dependence_array['products_main'] = [
    'js' => [abs_module_url($this->CI->router->module) . '/assets/js/products_main.js']
    ,'main_js' => [
        'js/plugins/tinymce/tinymce.min.js'
        ,'js/plugins/jquery.ba-throttle-debounce.min.js'
        ,'js/plugins/seo_link_manager.js'
        ,'js/plugins/jquery.multiadd.js'
    ],
    'main_preApp_js' => ['js/plugins/bootstrap-switch/bootstrap-switch.min.js']
    ,'main_css' => ['js/plugins/bootstrap-switch/bootstrap-switch.min.css']
    ,'css' => [abs_module_url($this->CI->router->module) . '/assets/css/products_main.css']
];
```

Possible keys:

- To load assets before main css and js. This method points to the files in the directory <code>APP_ROOT/assets</code>\
<code>main_preApp_css</code>\
<code>main_preApp_js</code>

- To load assets before main css and js. This method points to the files in the directory <code>APP_ROOT/themes/back_end OR front_end/assets</code>\
<code>preApp_css</code>\
<code>preApp_js</code>

- To load css or js code before main css and js and write it into controller or into views directly.\
<code>preApp_css_code</code>\
<code>preApp_js_code</code>

- To load assets after main css and js. This method points to the files in the directory <code>APP_ROOT/assets</code>\
<code>main_css</code>\
<code>main_js</code>

- To load assets after main css and js. This method points to the files in the directory <code>APP_ROOT/themes/back_end OR front_end/assets</code>\
<code>css</code>\
<code>js</code>

- To load css or js code after main css and js and write it into controller or into views directly.\
<code>css_code</code>\
<code>js_code</code>

>[!INFO]
> You can use these methods directly into controller, e.g. $this->stencil->js([abs_module_url($this->CI->router->module) . '/assets/js/products_main.js\'])

> [!WARNING|label:ATTENTION]
> The order of assets into arrays is important for dependencies



it is very important to note that the array key is `products_main`;\
the `_main` suffix will automatically load the assets declared within the` index` method of your controller
<br/> and automatically passes it to the view (this is declared in the `Backend_Controller`).

Let's see the interested part in the `Products.php` controller:

```php
class Products extends BackEnd_Controller {
	// set the main properties
	public $main_table,
			$perms = 'products',
			$assets = 'products_', <- this is the magic
			$form_view,
			$search_view,
			$title_icon = 'fa fa-cubes',
			$page_title = '',
			$translation_table = '';

	public function __construct()
	{
        .....
```
the property <code>$assets</code> is setted to `products_` and it's the prefix of array key into <code>$assets_dependence_array</code>.

For the not autload assets via `_main` suffix, you can use the method <code>$this->set_assets_method()</code> into your controller.
For example:
if the sctructure of your <code>assets_dependences_loader.php</code> would be
```php
$assets_dependence_array['SOME_KEY'] = [
    'js' => [abs_module_url($this->CI->router->module) . '/assets/js/products_main.js']
    ,'main_js' => [
        'js/plugins/tinymce/tinymce.min.js'
        ,'js/plugins/jquery.ba-throttle-debounce.min.js'
        ,'js/plugins/seo_link_manager.js'
        ,'js/plugins/jquery.multiadd.js'
    ],
    'main_preApp_js' => ['js/plugins/bootstrap-switch/bootstrap-switch.min.js']
    ,'main_css' => ['js/plugins/bootstrap-switch/bootstrap-switch.min.css']
    ,'css' => [abs_module_url($this->CI->router->module) . '/assets/css/products_main.css']
];
```

you could have loaded the assets in this way into your method:
<code>$this->set_assets_method('SOME_KEY')</code>

> [!TIP]
> You can pass php variables value into js file of the module.
> Just use then $data['jsGeneralVar']['your_key'] = $SOME_PHP_VARIABLE_VALUE;
> in your js file you will have the variable `your_key` available and you will call it with <code>jsGV.your_key</code>

> [!TIP]
> All php strings language are available into your js files and you can call them via <code>lang.PHP_LANGUAGE_STRING</code>

>[!INFO]
> To understand more it is also necessary to take a look at the slice footer.php within the LTE theme we use for the backend.

## assets_dependences_loader_general.php

the logic is the same of assets_dependences_loader.php but this assets will be loaded for entire platform not only when you reach the specific module.
