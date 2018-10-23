# ansible-mysql

# CI Status

* Master: [![Build Status](https://travis-ci.com/Scaffa85/ansible-mysql.svg?branch=master)](https://travis-ci.com/Scaffa85/ansible-mysql)
* Develop: [![Build Status](https://travis-ci.com/Scaffa85/ansible-mysql.svg?branch=develop)](https://travis-ci.com/Scaffa85/ansible-mysql)

This role should fullfill these requirements:

* Role should support multiple mysql versions (5,5 and 5,6)
* Role should support multiple OS systems (Centos, Ubuntu)
* Root password must be set.
* List of databases should be able to be passed and have them pre-created.

# Map

```
├── site.yml < this is the playbook which runs the entire installation
├── roles
│   ├── mysql
│   │   ├── tasks
│   │   │   ├── yum_disable_5_7.yml < These three 'disable' tasks remove un-necessary repositories.
│   │   │   ├── yum_disable_5_6.yml < They enable only the version dictated in the
│   │   │   ├── yum_disable_5_5.yml < mysql_servers.yml vars.
│   │   │   ├── Ubuntu-16.yml < Anything specific to Ubuntu
│   │   │   ├── main.yml < Parent task for everything in this directory
│   │   │   ├── install_repo_yum.yml < Only runs on yum based installations.
│   │   │   ├── install_repo_deb.yml < Only runs on apt based installations.
│   │   │   └── CentOS-7.yml < Anything specific to CentOS
│   │   ├── handlers
│   │   │   └── main.yml < Any hooks to be called from a task (i.e restart service)
│   │   ├── files
│   │   └── default
│   │       └── main.yml < Default variables for testing.
│   └── common
│       ├── vars
│       ├── templates
│       ├── tasks
│       │   └── main.yml < Some common installation packages not unique to MySQL
│       ├── module_utils
│       ├── meta
│       ├── lookup_plugins
│       ├── library
│       ├── handlers
│       ├── files
│       └── defaults
├── README.md
├── module_utils
├── library
├── host_vars
├── hosts
├── group_vars
│   ├── mysql-servers.yml < Variables that are only included by hosts in the [mysql-servers] group
│   └── all.yml < Variables that are included for all.
├── filter_plugins
└── ansible-create.py < The script which created the directory structure.
```

