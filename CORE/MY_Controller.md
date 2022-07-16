# MY_Controller

This is the core controller that extends MX_Controller (take a look to [HMVC library](https://github.com/MrPlugins/wiredesignz-codeigniter-modular-extensions ':target=_blank') ) and will be extended from all your modules' controllers.\
It is made up of 4 different classes for greater modularity and sectorial extensibility.\
In this section we will list the __public__ methods and properties of the class and explain only their basic functionality.

> [!INFO]
> There will be topics for further study in the section dedicated to [Modules](modules/README.md) and everything will be clearer.

## <a> *Shared_Controller Class* </a>

This class is the star of the magic and will be extended by `BackEnd_Controller` and` FrontEnd_Controller`.\
In its constructor, all libraries and functions will be started to initialize *__inCIpit__*.

Each method is obviously overridden in your controllers, but for best practices, the advice is to do it only for some methods when necessary.

### Methods

* `maintenance` Check if *__inCIpit__* is in maintenance mode (see `maintenance_mode` [in app.config](CONFIG?id=appphp-autoloaded)) and exits on relative view into theme pages directory (front or back-end) if exists otherwise print simple 503 error.
* `maintenance_module` Set maintenance mode for a specific module (use it into your controller constructor)<br/> and exits on relative view into theme pages directory (front or back-end) if exists otherwise print simple 503 error.
* `set_assets_method` Load the assets dependencies written into file assets_dependences_loader.php if exists into current o chosen module directory.
* `error_404` Show 404 (Not found) error for each template parts (back and front) - see the 404_override into default route.
* `error_403` Show 403 (Forbidden) error for each template parts (back and front).
* `general_error` Show general error for each template parts (back and front).
* `check_item_relations` Check if an element is related to least one records into provided tables.


* `_remap` This method allow to do paths remap for Back-end and Front-end.

> [!NOTE]
> This is a technical controller, no need to use it.

## <a> *BackEnd_Controller Class* </a>

Extends `Shared_Controller` and is the main controller for the whole Back-end part.\
The login and related checks are started in the constructor.

### Properties

|             |                                                                                                                                                                                                                                                          |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `form_type` | Set the form type into add/edit methods, <br/>Default: "modal"<br/>Possible values: <br/>"modal": check if call a form via ajax<br/>"regular": the system will load a standard layout of a standard page to show form into another page not into a modal |

Enables or not the trash system with soft delete of items.
This depends from the existence of d_date column into main_table;
if d_date column exists the trash system will be activate automatically and into main mage of the module will be show the trash button link

|             |                                                                                                                                                                                                                                                          |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `show_trash` | Shows or not the trash button, <br/>Default: TRUE<br/>Possible values: <br/>TRUE: Shows the trash button<br/>FALSE: Hides the trash button|
| `allow_disable` | Shows or not the disable button for each rows (it also depends on permissions), <br/>Default: TRUE<br/>Possible values: <br/>TRUE: check if call a form via ajax<br/>FALSE: Hides the button |
| `allow_disable_only` | Shows or not only the disable button for each rows and not the delete button (it also depends on permissions and allow_disable property), <br/>Default: TRUE<br/>Possible values: <br/>TRUE: check if call a form via ajax<br/>FALSE: Hides the button |
| `allow_enable` | Shows or not the enable button for each rows into trash part (it also depends on permissions), <br/>Default: TRUE<br/>Possible values: <br/>TRUE: check if call a form via ajax<br/>FALSE: Hides the button | |
| `allow_enable_only` | Shows or not only the enable button for each rows and not the delete button into trash part (it also depends on permissions and allow_enable property), <br/>Default: TRUE<br/>Possible values: <br/>TRUE: check if call a form via ajax<br/>FALSE: Hides the button | |
| `disallow_methods` | Simple list to disable method from your extended controller, <br/>Default: EMPTY<br/>Possible values: <br/>`index`, `my_index`<br/> `add`, `my_add`<br/> `edit`, `my_edit`<br/> `delete`, `my_delete`<br/> `disable`, `my_disable`<br/> `enable`, `my_enable`<br/> `create`, `my_create`<br/> `update`, `my_update`<br/> `trash` | |


### Methods

* `index` It is obviously the initial method, it is used to reach your controller.
* `my_index` Return the view of listing items and must be called back into `index`.
* `listing` Return the elements or an ajax request (tipicaly used to list elements into a table for bootstrapTable autoloaded into `index`).
* `extra_listing` To manipulate the data coming from `get_list` method of [`main_model`](CORE/MY_Model.md).


* `add` Used only if need to add other data to add_form view.
* `my_add` Load add_form after perform some logics.
* `before_create` Callback before creation.
* `create` Create a record after data normalization and validation.
* `my_create` Create a record after perform some logics.
* `after_create` Callback after creation.


* `edit` Used only if need to add other data to edit_form view.
* `my_edit` Load edit_form after perform some logics.
* `before_update` Callback before update.
* `update` Update a record after data normalization and validation.
* `my_update` Update a record after perform some logics.
* `after_update` Callback after update.


* `before_enable` Callback before enable item/s.
* `enable` Enable a record after data normalization and validation.
* `my_enable` Enable item/s after perform some logics.
* `after_enable` Callback after enable item/s.


* `before_disable` Callback before disable item/s.
* `disable` Disable a record after data normalization and validation.
* `my_disable` Disable item/s after perform some logics.
* `after_disable` Callback after disable item/s.


* `trash` Useful method to understand when we are in trash mode.
* `get_disabled_num_rows` Get the number of disabled items for the controller.


* `before_delete` Callback before delete item/s.
* `delete` Delete a record after data normalization and validation.
* `my_delete` Permanently delete record/s after perform some logics.
* `after_delete` Callback after delete item/s.


* `data_validation` Apply validation roles for creation or update.
* `create_update_data_normalization` Normalize data for creation or update.
* `add_edit_data_normalization` Normalize data to pass to the add or edit form.


## <a> *FrontEnd_Controller Class* </a>

It extends `Shared_Controller` and is the main controller for the whole Front-end part.\
The login and related checks are started in the constructor.

### Methods

* Just the constructor


## <a> *MY_Rest_Controller Class* </a>

Extends `REST_Controller` and is the main controller of the RESTFUL API.

### Methods

* Just the constructor