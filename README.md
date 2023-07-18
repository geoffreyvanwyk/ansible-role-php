Ansible Role for PHP
====================

[![build](https://github.com/geoffreyvanwyk/ansible-role-php/workflows/Build/badge.svg?event=push)](https://github.com/geoffreyvanwyk/ansible-role-php/actions?query=workflow%3ABuild)

Installs, configures and extends the [PHP](https://www.php.net) programming language on [Ubuntu](https://www.ubuntu.com) servers. Multiple versions of PHP can be installed simultaneously on the same server.

Requirements
------------

> Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Only [supported versions of PHP](https://php.net/supported-versions.php) are tested to work with this role on long-term support [versions of Ubuntu](https://wiki.ubuntu.com/Releases) that still receive standard support.

Role Variables
--------------

> A description of the settable variables for this role should go here with their default values, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

```yaml
php_version: 8.2
```

The version of PHP that you want to install.

---

```yaml
php_mod_enabled: []
```

The PHP modules (extensions) that you want to enable in addition to the modules that are enabled by default, for example:

```plain
php_mod_enabled:
  - intl
  - mysql
  - xml
```

---

```yaml
php_mod_disabled: []
```

The PHP modules (extensions) that you want to disable in addition to the modules that are disabled by default, for example:

```plain
php_mod_disabled:
  - json
  - mbstring
  - zip
```

---

```yaml
php_ini_cli: []
```

The PHP initialization settings for the command-line, for example:

```plain
php_ini_cli:
  - name: allow_url_fopen
    value: Off
  - name: memory_limit
    value: -1
  - name: date.timezone
    value: "Africa/Johannesburg"
```

---

```yaml
php_ini_apache: []
```

The PHP initialization settings for the Apache web server module for PHP, for example:

```plain
php_ini_apache:
  - name: post_max_size
    value: 128M
  - name: upload_max_filesize
    value: 32M
  - name: max_file_uploads
    value: 2
```

---

```yaml
php_ini_fpm: []
```

The PHP initialization settings for the FastCGI Process Manager module, for example:

```plain
php_ini_fpm:
  - name: max_execution_time
    value: 300
  - name: max_input_time
    value: 600
  - name: max_input_vars
    value: 5000
```

Dependencies
------------

> A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

None.

Example Playbook
----------------

> Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - role: geoffreyvanwyk.php
      php_version: 8.0
      php_mod_enabled:
        - mysql
    - role: geoffreyvanwyk.php
      php_version: 7.4
      php_ini_apache:
        - name: post_max_size
          value: 256M
```

License
-------

Copyright &copy; 2023 Geoffrey Bernardo van Wyk [(https://geoffreyvanwyk.dev)](https://geoffreyvanwyk.dev)

This file is part of Ansible role geoffreyvanwyk.php.

Ansible role geoffreyvanwyk.php is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

Ansible role geoffreyvanwyk.php is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with Ansible role geoffreyvanwyk.php. If not, see <https://www.gnu.org/licenses/>.

Author Information
------------------

[Geoffrey van Wyk](https://geoffreyvanwyk.dev) created this role in 2023.
