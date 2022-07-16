# Welcome to inCIpit

> A Swiss Army knife for PHP developers

You can use *__inCIpit__* for your projects, to develop what you want in a simple and quick way.\
It includes many tools, shortcode, libraries, helpers to help you with an happy coding.\
*__inCIpit__* has a own smart CRUD that will help you write very short code.

>[!INFO]
> You will find the list of updates in the corresponding section:\
> [*__inCIpit__* changelog](CHANGELOG.md)\
> [*__Documentation__* changelog](CHANGELOG_GUIDE.md)\
>
> *__inCIpit__* comes with a complete module for *__pages__* management, including front-end part, and a "*__products__*" demo module to which this guide will refer many times.

## Overview
Some *__inCIpit__* features:
- Includes HMVC
- Includes Back-end and Front-end (optional) System.\
  *__inCIpit__* includes a simple front-end theme as example to show how it works.
- Full __pages__ module (front/back-end parts)
- Full demo __products__ module with categories management
- Multilanguages.\
   You can translate from back-end panel starting from you main language variables.\
   The variables are avaiable into you js script too.\
   *__inCIpit__* comes with 2 languages by default (English and Italian).
- Multi theme system with a module for the management.
- Permission system
  - Permission based on CRUD like linux UGO.
  - Boolean permission.
  - Permissions dedicated to the single user.
  - All permissions are managed via control panel.
- Roles system (for permissions)
- Multi group system (for permissions)
- Crontabs module.
- Interactive front-end and back-end menu.
- Front-end and back-end login system.
- A lot of shortcodes to write html.
- File manager with Tinymce integration.
- A library to create shortcodes (like Wordpress).
- Maintenance mode for entire system or for a single module.
- Simple upload, integrated with filemanager too.
- Routing system managed from back-end.
- Full integration with PHPMailer.
- BootstrapTable auto integration to list items of CRUD in a simple way.
- Include a customized Stencil version (Template engine).
- Simple assets integration; no need write code into controllers.
- Separated assets for each module.
- CRUD log system
- A lot of js plugins (*__inCIpit__* is jQuery based).
- and much, much more...

> [!TIP]
> Don not forgot *__inCIpit__* is [Codeigniter 3.1.13](https://codeigniter.com/userguide3/) based and for this reason it will respect all the main framework rules.

> [!WARNING|label:ATTENTION]
> This documentation will report only adding features and coding strategies not available into main framework.

## Installation
- Just uncompress downloaded package from Codecanyon it into your hosting space.
- Create a MySQL database.
- Import Incipit_dump.sql into your database.
- Change file applicatin/config/database.php according your db params.
- Use your browser to reach your *__inCIpit__* installation.

That's all, enjoy with *__inCIpit__* !


## Server Requirements
- PHP version __7.3__ or newer is recommended.
 It should work on __5.6__ as well, but we strongly advise you NOT to run such old versions of PHP,\
 because of potential security and performance issues, as well as missing features.
- mb_string extension enabled.
- Apache server with Rewrite module enabled.
- Write permissions on `public` folder

A database is required for most web application programming. Currently supported databases are:

- MySQL (5.1+) via the mysql (deprecated), mysqli and pdo drivers
- Oracle via the oci8 and pdo drivers
- PostgreSQL via the postgre and pdo drivers
- MS SQL via the mssql, sqlsrv (version 2005 and above only) and pdo drivers
- SQLite via the sqlite (version 2), sqlite3 (version 3) and pdo drivers
- CUBRID via the cubrid and pdo drivers
- Interbase/Firebird via the ibase and pdo drivers
- ODBC via the odbc and pdo drivers (you should know that ODBC is actually an abstraction layer)

<!---
## File structure
Only the folders and files affected by the additional features compared to the original framework will be explained.

```text
your project folder
└── application/
|   ├── index.html (the entry file)
|   ├── quickstart.md ( sidebar subpage)
|   ├── README.md ( home page)
|   ├── _navbar.md ( navigation bar)
|   ├── _sidebar.md ( sidebar)
|   ├── _coverpage.md ( coverpage)
|   └── style.css ( you can add your own style or update here then update stylesheet path in `index.html` )
└── assets/
|   ├── css/
|   ├── fonts/
|   └── js/
└── filemanager/
└── modules/
|   ├── system_modules/
|   └── users_modules/
└── public/
└── system/
└── themes/
└── vendor/
└── .htaccess
└── bootstrap.php
└── composer.json
└── composer.lock
└── index.php
```
-->
