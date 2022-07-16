## Preamble

The basic logic is programming in HMVC, which is why inCIpit is based on the creation of modules.\
This pattern allows to be extremely modular and keep the logics separate for each module.\
For now the modules will be created manually, but a tool will be provided to create the skeleton of a module directly from the CLI or from the control panel come with the next updates.

The modules are divided into two macro groups (just for convenience): `system_moules` and `user_modules`.\
It's important to know that you can develop a module into `themes/front_end` directory too, this's useful when you want develop a theme with own features for back and front-end part;\
to do so, just create `modules` folder into theme directory and follow the documentation below.\
if necessary, you can create other directories by editing the configuration file, but it is recommended not to do so.

>[!TIP]
> For simplicity, in this guide we will refer to a dummy module called <span style="font-size:18pt;"> *__products__* </span> which you will find in the *__inCIpit__* installation package.\
It is a perfet example to show back and fron-end part of *__inCIpit__*.\
You can [uninstall](TIPS_AND_TRICKS/UNISTALL_DUMMY_PRODUCTS_MODULE.md) it at any time.

### system_moules

Where all system modules are located.\
In this directory we can find some modules already:

- `api`
- `appareance`
- `crontabs`
- `filemanager`
- `languages`
- `login`
- `settings`
- `themes`
- `users`
- `utilities`

!> Please do not remove these modules.

### user_modules

Where you will do the magic creating your own modules.

## The base logic of a module

Each module can have a part dedicated to the __Back-end__ and one to the __Front-end__ or simply one of the two.\
For this reason, both in the controllers and in the models there is a folder called `admin` where the Back-end logics will be developed.

?> The `admin` folder is a convention, don't change its name;\
 if you want to reach the backend from a different url, use the `application/config/app.php` configuration file by editing the `admin_segment` variable.

A module has the same typical structure as the `application` folder:
* assets (*__inCIpit__* feature)
* config
* controllers
* language
* libraries
* models
* views

## Module directory structure

```
your project folder
└── modules/
    ├── system_modules/ (folder with system modules)
    └── user_modules/ (your modules directory)
        └── YOUR_MODULE_NAME/ (this will be your module folder name; it will be unique)
            |
            ├──assets/ (OPTIONAL - the assets folder)
            |  ├── css/
            |  ├── fonts/
            |  └── js/
            |
            ├──config/ (OPTIONAL - the configuration files folder)
            |  |
            |  ├── admin/ (configurations files for back-end)
            |  |   ├── your_module_admin_config_1.php
            |  |   ├── your_module_admin_config_2.php
            |  |   └── your_module_admin_config_3_.php
            |  |
            |  ├── your_module_front_config_1.php (OPTIONAL - for frontend)
            |  ├── your_module_front_config_2.php (OPTIONAL - for frontend)
            |  ├── your_module_front_config_3.php (OPTIONAL - for frontend)
            |  └── routes.php (OPTIONAL - see Codeigniter routes on official documentation)
            |
            ├──controllers/ (REQUIRED - controllers for back and front-end)
            |  |
            |  ├── admin/ (REQUIRED - the back-end controllers)
            |  |   ├── YOUR_MODULE_NAME.php (tipically the main controller, called like module controller - HMVC logic)
            |  |   └── another_controller.php (OPTIONAL - another controller for back-end)
            |  |
            |  ├── YOUR_MODULE_NAME.php (OPTIONAL - a frontend controller)
            |  └── another_controller.php (OPTIONAL - another controller for frontend)
            |
            ├──language/ (REQUIRED - languages folder for back and front-end)
            |  |
            |  ├── english/ (REQUIRED - default languageg)
            |  |   ├── admin/ (REQUIRED - the back-end languages files)
            |  |   |   ├── permissions_contexts_lan.php (REQUIRED - the lang file with permission translations variables)
            |  |   |   ├── back_end_lang_file_01.php (OPTIONAL)
            |  |   |   └── back_end_lang_file_02.php (OPTIONAL)
            |  |   |
            |  |   ├── front_end_lang_file_01.php (OPTIONAL)
            |  |   └── front_end_lang_file_02.php (OPTIONAL)
            |  |
            |  └── italian/ (OPTIONAL - the back-end controllers)
            |      ├── admin/ (the back-end languages files)
            |      |   ├── permissions_contexts_lan.php (the lang file with permission translations variables)
            |      |   ├── back_end_lang_file_01.php (OPTIONAL)
            |      |   └── back_end_lang_file_02.php (OPTIONAL)
            |      |
            |      ├── front_end_lang_file_01.php (OPTIONAL)
            |      └── front_end_lang_file_02.php (OPTIONAL)
            |
            ├──libraries/ (OPTIONAL - the module libraries)
            |  |
            |  ├── lib_01.php
            |  └── lib_2.php
            |
            ├──models/ (REQUIRED - models for back and front-end)
            |  |
            |  ├── admin/ (REQUIRED - the back-end models)
            |  |   ├── Model_name_back_end.php
            |  |   └── Another_model_back_end.php
            |  |
            |  ├── Model_name_front_end.php (OPTIONAL - a frontend model)
            |  └── another_model_front_end.php (OPTIONAL - another model for frontend)
            |
            ├──views/ (REQUIRED - the views folder)
            |  |
            |  ├── view_01.php
            |  └── view_02.php
            |
            ├── assets_dependences_loader.php (OPTIONAL - to define into an array all assets that will be loaded into all your controllers when you are into module from browser)
            └── assets_dependences_loader_general.php (OPTIONAL - to define into an array all assets that will be loaded in all page of platform; for example you can set a observer)
```