# How write your controllers

In this section you will find the best practices to write your controllers at best according to the "rules" of *__inCIpit__*.\


## Let's begin

A controller can extend both `BackEnd_Controller` and` FrontEnd_Controller`, depending on the part being developed.\
Let's start with a controller that concerns the Back-end part as it is the most complex one and that you will find yourself developing in a software in most cases.

The `BackEnd_Controller` is always regulated and controlled by the login (see the constructor in [MY_Controller.php](CORE/My_controller.md));\
The main controller of a module is called with the same name as the module (this is not mandatory, but it allows you to use a direct uri by passing the module path - see [HMVC library](https://github.com/MrPlugins/wiredesignz-codeigniter-modular-extensions ':target=_blank'));\
obviously you can create as many controllers as you want in `YOUR_MODULE/controllers` folder.

## Back-end controller
A back-end controller is normally written to represent data (typically in a table with an auto-loaded bootstrapTable) on which we can perform operations: edit, obtain information, delete, create new records, perform a search, etc.

This guide will list the standard properties and methods for basic CRUD operations,\
obviously you can implement and extend the code as you see fit and overwrite every single method excluding the *__inCIpit__* logic at any time.

###  Preliminary actions to be done manually

it is necessary (but if you want you can develop a method to do this automatically) load the permission context for your module in the database "table `permissions_context` "if it is foreseen. <br/>
Enter the following parameters:<br/>
- <code>uniqid</code>: a unique 21-character alphanumeric string; to generate it you can use the set_uniqid () function found in the self-loaded helper `My_string_helper.php`
- <code>context</code>: context to be defined
- <code>description</code>: language string for the context that you will find in the control panel when assigning permissions
- <code>crud</code>: 1 defines if it is a CRUD-based permission, 0 if it is a simple action (YES/NO)
- define the language string for your context in the `permissions_contexts_lan.php` file ([see the structure of a module](modules/README?id=module-directory-structure))

### Default property

`main_table` defines the table on which to apply the CRUD\
`perms` defines the permission context for this module\
`assets` prefix of the assets that will be loaded\
`form_view` definisce la vista per un eventuale form di inserimento/modifica\
`search_view` defines the view for searching\
`title_icon` you can define an icon (typically with fontawesome) visible next to the page title\
`page_title` defines the page title (typically the translation string)

*__For other properties go to [BackEnd_Controller Class properties](CORE/My_controller?id=properties)__*


###  `construct` *__Method__*

- Normally the reference model is loaded which, by convention and collision avoidance, has the same name as the controller but with the suffix `_model` and loaded with an alias `main_model`.\
  <code>$this->load->model($this->router->module.'/admin/YOUR_MODEL_model','main_model');</code>
- you can load language files\
  <code>$this->load->language($this->router->module.'/admin/YOUR_LANG_FILE');</code>
- define the default properties:
  - <code>$this->main_table = $this->main_model->main_table;</code>
  -	<code>$this->form_view = $this->router->module.'/YOUR_MODULE_VIEW_DIR/form';</code>
  -	<code>$this->search_view = $this->router->module.'/YOUR_MODULE_VIEW_DIR/search';</code>
  -	<code>$this->page_title = $this->lang->line($this->page_title);</code>
- define global permissions for the module in question.
  <code>if(! $this->ion_auth->permission($this->perms)) return $this->error_403();</code>

### `index` *__Method__*

This method lists the results of the main query.\
it is possible to set a series of variables to be passed to the `my_index` method of the MY_Controller called at the end.

Se si usa la logica di *__inCIpit__*, alcuni di questi dati sono obbligatori per poter effettuare la query del model e mostrare i risultati in modo corretto:\
verranno spiegate le funzionalità principali con i commenti direttamente nel codice in modo da semplificare la guida.

If you use the logic of *__inCIpit__*, some of this data is required in order to query the model and display the results correctly: \
the main features will be explained with comments directly in the code in order to simplify the guide.


To organize the data to show in the bootstrapTable table

```php
    /*
     * This is array configuration for the main table
     * The table will be loaded with bootstrapTable plugin
     */
    $colModel = [
      'Name to show into first column of the table' => [
        'field' => 'table_column_name'
        ,'formatter' => 'this is a js function to format data and it\'s optional'
      ]
      ,[
        'Name to show into second column of the table' => [
        'field' => 'table_column_name'
        ,'formatter' => 'this is a js function to format data and it\'s optional'
      ]
        //... add your logic here for other columns //
    ];
```

```php
	public function index()
	{

		$data = [
			'colModel' => $colModel
			,'table_order_by' => 'YOUR_TABLE_FIELD_TO_ORDER_BY'
			,'table_sort_order' => 'asc'
			,'add_button' => ['tags' => ['id' => 'btn_add_item']]
			,'legend' => [
				['color' => '#ff851b', 'label' => lang('legend_to_confirm_label')]
				,['color' => '#d73925', 'label' => lang('legend_disabled_lable')]
			]
		];

		$this->my_index($data);
	}

```

The CRUD methos are implemented automatically, please take a look to [MY_Controller.php](CORE/My_controller.md)

## Front-end controller

Just exteds <code>Shared_Controller</code> and fell free to implement your logics.

Don't forget that everything will be clearer by having the code and sample modules within the package handy.