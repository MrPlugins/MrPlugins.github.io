# MY_Model

This is the core model that extends CI_Model and will be extended from all your modules' models.\
It is made up of 4 different classes for greater modularity and sectorial extensibility.\
In this section we will list the __public__ methods and properties of the class and explain only their basic functionality.

> [!INFO]
> There will be topics for further study in the section dedicated to [Modules](modules/README.md) and everything will be clearer.

### Properties
|                           |                                                                                                 |
|---------------------------|-------------------------------------------------------------------------------------------------|
| `main_table`              | Main DB table without alias.                                                                    |
| `main_permission_table`   | DB Table on which permissions will be applied. If not defined it will be equal to `main_table`. |
| `main_permission_context` | Permission context to set on `main_table` or on `main_permission_table` if defined.             |

### Metodi

* `gets` Get results from a table quickly.


* `set_permission_listing` Set permissions for the query in the `listing` method.\
  It is automatically called into main_query to set the permissions based on main_permission_table and main_permission_context.\
  You can can call this method in other query too but pay attention to query builder.
* `query_search` Filters for the main_query on `main_table`,\
    it's useful for the advanced search.\
    Normally you can call this method into a model, and putting in it all the logic for the search\
    E.g. $this->db->where('come_column','some_value') etc...
* `main_query` Query on main table includig `query_search`.
* `get_list` Get the list of items includig pagination.
* `paginate` Pagiante get_list method results.\
    Possible pagination by page number or offset directly.


* `before_create` Callback before creation.
* `create` Create a record.
* `after_create` Callback after creation.


* `before_update` Callback before update.
* `update` Update a record based on the uniqid.
* `after_update` Callback after update.


* `update_pivot` Update child elements linked to a parent element via uniqid columns.\
  The method will create new items, delete removed items and update old items.
* `update_pivot_to_disable_children` The same scope of `update_pivot` but used to disable function.


* `before_enable` Callback before enable.
* `enable` Enable the disabled record/s.
* `after_enable` Callback after enable.


* `enable_pivot` Enable child row linked to a parent.


* `before_delete` Callback before disable.
* `delete` Delete record/s.
* `after_delete` Callback after disable.


* `delete_pivot` Delete child row linked to a parent.


* `before_disable` Callback before disable.
* `disable` Disable the enabled record/s.
* `after_disable` Callback after disable.


* `disable_pivot` Disable child row linked to a parent.


* `get_disabled_num_rows` Return disabled items number. Userful for trash.


* `check_item_relations` Check if an element is related to least one records into provided tables.
* `filter_data` Filter out any data passed that have a matching column in the table.
* `set_error_delimiters` Set the error delimiters
* `set_error` Set an error message
* `errors_array` Get the error messages as an array
* `errors` Get the error message as string.
* `set_message_delimiters` Set the message delimiters.
* `set_message` Set a message.
* `messages_array` Get the messages as an array.
* `messages` Get the messages as string.


## <a> *Shared_Model Class* </a>

It extends `MY_Model`.

### Methods

* Just the constructor


## <a> *BackEnd_Model Class* </a>

It extends `Shared_Model` and is the main model for the whole Back-end part.

### Methods

* Just the constructor


## <a> *FrontEnd_Model Class* </a>

It extends `Shared_Model` and is the main model for the whole Front-end part.

### Methods

* Just the constructor