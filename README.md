# WordPress on Nginx, HHVM, and MariaDB

This is a bare-bones Vagrant framework template for a high-performance website
hosted on Nginx, HHVM, and MariaDB.

The author uses this to manage a development environment for his blog:
[Keita's Blog](http://kkob.us).

## Getting Started

0. [VirtualBox](https://www.virtualbox.org)

0. [Vagrant](http://www.vagrantup.com)

1. The `vagrant-hostsupdater` plugin
    * `$ vagrant plugin install vagrant-hostsupdater`

2. Copy the configuration file.
    * `$ cp config.rb.example config.rb`

3. The configuration file included is adequate as a demonstration,
but you probably want to adjust some variables.

4. `$ vagrant up`

## How To Use

1. Fork the repository.

1. Put your theme files in `theme/`.
	* `theme/` is automatically synced with `/wp-content/themes/{theme_name}`, where `{theme_name}` is the value you configured in `config.rb`

2. Put your plugins in `plugins/`.
	* `plugins/` is automatically synced with `/wp-content/plugins/`.

4. Commit your changes and distribute the repository with your co-workers. Please note that this is a template -- if you want to contribute or fix bugs in the template, please make sure that `theme/` and `plugins/` is empty.

## Features

### Import data from a SQL dump file.

Put your SQL dump file in `initial_data.sql`, and set `config.load_sql` values accordingly in `config.rb`. Please note that you probably should *exclude* the `wp_users` and `wp_usermeta` tables from the export.

## Planned Features

- [ ] More WordPress installation options. Eg: Language, version, etc.
- [ ] Import data from a WXR (WordPress Export File).
- [ ] Auto-deploy script.
