# Bottom$Up 

<!-- TOC -->
## Table of Contents
   * [Introduction](#introduction)
   * [Repository Details](#repository-details)
   * [Getting Started](#getting-started)
      + [Installation](#installation)
      + [Install composer](#install-composer)
   * [Update](#update)
      + [Update composer](#update-composer)
      + [Install and Run Migrations plugin via composer](#install-migration-plugin-via-composer)
      + [Install Authentication plugin via composer](#install-authentication-plugin-via-composer)
      + [Install Content Blocks plugin via composer](#install-content-blocks-plugin-via-composer)
      + [Install Stripe plugin via composer](#install-stripe-plugin-via-composer)
   * [Code Organisation](#code-organisation)
   * [Frameworks](#frameworks)
   * [Coding Guidelines](#coding-guidelines)
   * [Future Developers](#future-developers)
   * [Contact](#contact)
   * [Acknowledgements](#acknowledgements)

<!-- TOC --><a name="introduction"></a>
## Introduction

Welcome to the Bottom$Up website project repository. This document serves as a guide to help you navigate the codebase structure, understand the codebase, and adhere to the project's coding standards and conventions.

This project was developed using the [CakePHP 4.x](https://book.cakephp.org/4/en/index.html) framework.

The framework source code can be found here: [cakephp/cakephp](https://github.com/cakephp/cakephp).

<!-- TOC --><a name="repository-details"></a>
## Repository Details
### Cloning the Repository

To get a full clone of this repository, including all history commits, run the following command:

```bash
git clone --mirror https://git.infotech.monash.edu/UGIE/ugie-2024/team036/team036-app_fit3048.git
```

### Repository Structure
Here’s an overview of the main directories and files in this CakePHP project:

```bash
team036-app-fit3048/
│
├── config/                         # Configuration files
│   ├── Migrations/                 # Migration files
│   ├── Seeds/                      # Seeded files
│   ├── schema/                     # Schema related files
│   ├── app.php                     # Application configuration
│   ├── bootstrap.php               # Bootstrap file
│   ├── routes.php                  # Routes configuration
│   └── ...                         # Other configuration files
│
├── src/                            # Source files
│   ├── Console/                    # Console
│   ├── Controller/                 # Controllers
│   ├── Model/                      # Models
│   ├── View/                       # Views
│   ├── Application.php             # Application setup file
│   └── ...                         # Other source files
│
├── templates/                      # Template files
│
├── tests/                          # Test cases
│
├── webroot/                        # Webroot files
│   ├── css/                        # CSS files
│   ├── font/                       # Font files
│   ├── img/                        # Image files
│   ├── js/                         # JavaScript files
│   ├── favicon.ico                 # Bottom$Up Favicon
│   └── ...                         # Other webroot files
│
├── .gitignore                      # Git ignore file
├── composer.json                   # Composer configuration
└── README.md                       # This README file
```

<!-- TOC --><a name="getting-started"></a>
## Getting Started

<!-- TOC --><a name="installation"></a>
### Installation

1. Download [Composer](https://getcomposer.org/doc/00-intro.md) or update `composer self-update`.
2. Run `php composer.phar create-project --prefer-dist cakephp/app [app_name]`.

If Composer is installed globally, run

```bash
composer create-project --prefer-dist cakephp/app
```

In case you want to use a custom app dir name (e.g. `/myapp/`):

```bash
composer create-project --prefer-dist cakephp/app myapp
```

You can now either use your machine's webserver to view the default home page, or start
up the built-in webserver with:

```bash
bin/cake server -p 8765
```

Then visit `http://localhost:8765` to see the welcome page.

<!-- TOC --><a name="install-composer"></a>
### Install Composer

Install [composer](https://getcomposer.org) into your CakePHP application and follow the instructions.

```
composer install
```


<!-- TOC --><a name="update"></a>
## Update

<!-- TOC --><a name="update-composer"></a>
### Update Composer

Update [composer](https://getcomposer.org) in your CakePHP application and follow the instructions.

```
composer update
```

<!-- TOC --><a name="install-migration-plugin-via-composer"></a>
### Install and Run Migrations plugin via composer

Install this plugin into your CakePHP application using [composer](https://getcomposer.org).

```
composer require cakephp/migrations
bin/cake plugin load Migrations
```

<!-- TOC --><a name="install-authentication-plugin-via-composer"></a>
### Install Authentication plugin via composer

> **Note:** [This is the official CakePHP documentation on Authentication](https://book.cakephp.org/authentication/3/en/index.html).
> It is strongly recommended you read through that documentation if you face any issues.
> It will provide additional insights from the official CakePHP folk.

Install this plugin into your CakePHP application using [composer](https://getcomposer.org).

```
composer require "cakephp/authentication"
```

<!-- TOC --><a name="install-content-blocks-plugin-via-composer"></a>
### Install Content Blocks plugin via composer

Install this plugin into your CakePHP application using [composer](https://getcomposer.org).

```
composer require ugie-cake/cakephp-content-blocks
```

#### Load the plugin

Using the `cake` CLI:

```php
bin/cake plugin load ContentBlocks
```
#### Create the `content_blocks` table in your database
>**Note:** [This is the official CakePHP quick start guide on CMS](https://book.cakephp.org/5/en/quickstart.html).

> **Note:** This must be done for each environment you deploy your website to (localhost, dev, prod, etc).
> It also requires you to have setup your `app.php` or `app_local.php` file with an appropriate `Datasources` block to connect to the database.

```
bin/cake plugin load ContentBlocks
bin/cake migrations migrate --plugin=ContentBlocks
```

#### Insert defined content blocks into database

Run the "Seed" to create the records in the database:

```
bin/cake migrations seed --seed ContentBlocksSeed
```

#### Run the remaining migrations

Run migrate to finalise the remaining changes to the database:

```
bin/cake migrations migrate
```

<!-- TOC --><a name="install-stripe-plugin-via-composer"></a>
### Install Stripe plugin via composer

Install this plugin into your CakePHP application using [composer](https://getcomposer.org).

```
composer require stripe/stripe-php
```

<!-- TOC --><a name="code-organisation"></a>
## Code Organisation
### Controllers
Controllers handle the request/response cycle. All controllers are stored in the `src/Controller` directory. Each controller should have appropriate actions (methods) to handle various operations.

### Models
Models represent the data structure and business logic. They are stored in the `src/Model` directory and follow CakePHP conventions, such as Table classes for database tables and Entity classes for individual records.

### Views
Views are responsible for rendering the output. They are stored in the `src/View` and `/templates` directories. Each controller has a corresponding directory in `/templates` where view files are stored.

### Configuration
Configuration files are stored in the `/config` directory. This includes database configurations, routes, and application settings.

Read and edit the environment specific `config/app_local.php` and set up the
`'Datasources'` and any other configuration relevant.
Other environment settings can be changed in `config/app.php` or `config/.env`.

<!-- TOC --><a name="frameworks"></a>
## Frameworks

The app uses [Milligram](https://milligram.io/) (v1.3), [Bootstrap](https://getbootstrap.com/) (v4.5.2), [Popper](https://popper.js.org/docs/v2/) (v2.9.2) and [Font Awesome](https://fontawesome.com/minimalist) (v5.15.4) CSS frameworks. 

<!-- TOC --><a name="coding-guidelines"></a>
## Coding Guidelines
### Naming Conventions
- Classes and Methods: Use CamelCase for class names and methods. E.g., VenuesController, registerVenue().
- Variables: Use camelCase for variable names. E.g., $apiKey, $venuesQuery.

### Commit Messages
Use clear and descriptive commit messages.

Follow a consistent format for commit messages. For example:

- [Verb] + [Feature]: [Changed] [status in admin vendor page to a dropdown.]

### Coding Standards
Follow PSR-12 coding standards.

- Ensure all PHP files start with `<?php` and do not include the closing `?>` tag.
- Use spaces instead of tabs for indentation.

<!-- TOC --><a name="future-developers"></a>
## Future Developers
Future developers are encouraged to follow the structure and guidelines outlined in this document. Consistent adherence to these practices will ensure maintainability and scalability of the project.

<!-- TOC --><a name="contact"></a>
## Contact
Project Link: https://git.infotech.monash.edu/UGIE/ugie-2024/team036/team036-app_fit3048
- Andy Chen: ache0100@student.monash.edu
- Racheal Lim: rlim0050@student.monash.edu
- Mark Sibulo: msib0008@student.monash.edu
- Dewmini Subasinghe: ksub0008@student.monash.edu
- Jiaxing Wang: jwan0290@student.monash.edu

<!-- TOC --><a name="acknowledgements"></a>
## Acknowledgements

- [Bootstrap](https://getbootstrap.com/)
- [Font Awesome](https://fontawesome.com/)
- [Milligram](https://milligram.io/)
- [CakePHP 4.x](https://cakephp.org)
- [Undergraduate Industry Experience](https://git.infotech.monash.edu/UGIE)
- [FIT Industry Experience Resource Repository](https://learning.monash.edu/course/view.php?id=12184)
