# WordPress on Nginx, HHVM, and MariaDB

This is a bare-bones Vagrant framework template for a high-performance website
hosted on Nginx, HHVM, and MariaDB.

The author uses this to manage a development environment for his blog:
[Keita's Blog](http://kkob.us).

## Getting Started

0. [Ansible](http://docs.ansible.com/intro_installation.html#installing-the-control-machine)

0. [VirtualBox](https://www.virtualbox.org)

0. [Vagrant](http://www.vagrantup.com) (version 1.5 or higher is required)

1. The `vagrant-hostsupdater` plugin
    * `$ vagrant plugin install vagrant-hostsupdater`

2. Copy the configuration file.
    * `$ cp config.rb.example config.rb`

3. The configuration file included is adequate as a demonstration,
but you probably want to adjust some variables.

4. `$ vagrant up`

## How To Use

1. Fork the repository.

1. Put your themes files in `themes/`.
	* `themes/` is automatically synced with `/wp-content/themes/`.

2. Put your plugins in `plugins/`.
	* `plugins/` is automatically synced with `/wp-content/plugins/`.

4. Commit your changes and distribute the repository with your co-workers. Please note that this is a template -- if you want to contribute or fix bugs in the template, please make sure that `themes/` and `plugins/` is empty.

## Features

### Import data from a SQL dump file.

Put your SQL dump file in `initial_data.sql`, and set `config.load_sql` values accordingly in `config.rb`. Please note that you probably should *exclude* the `wp_users` and `wp_usermeta` tables from the export.

## Planned Features

- [ ] More WordPress installation options. Eg: Language, version, etc.
- [ ] Auto-install plugins.
- [ ] Import `wp-content/uploads` data from ZIP / gzip file.
- [ ] Import data from a WXR (WordPress Export File).
- [ ] Auto-deploy script.

## License

```
Copyright (C) 2014 Keitaroh Kobayashi

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
```
