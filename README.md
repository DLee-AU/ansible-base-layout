# Ansible 2.7 Content Organisation

as per https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html
```
ansible-base-layout
├── filter_plugins/                 # if any custom filter plugins, put them here (optional)
├── group_vars/                     # here we assign variables to particular groups
│   ├── db_servers/
│   └── webservers/
├── host_vars/                      # here we assign variables to particular systems
│   ├── hostA/
│   └── hostZ/
├── library/                        # if any custom modules, put them here (optional)
├── module_utils/                   # if any custom module_utils to support modules, put them here (optional)
└── roles/
    ├── common/
    │   ├── defaults/               #
    │   │   └── main.yml            #  <-- default lower priority variables for this role
    │   ├── files/                  #
    │   │   ├── bar.txt             #  <-- files for use with the copy resource
    │   │   └── foo.sh              #  <-- script files for use with the script resource
    │   ├── handlers/               #
    │   │   └── main.yml            #  <-- handlers file
    │   ├── library/                # roles can also include custom modules
    │   ├── lookup_plugins/         # or other types of plugins, like lookup in this case
    │   ├── meta/                   #
    │   │   └── main.yml            #  <-- role dependencies
    │   ├── module_utils/           # roles can also include custom module_utils
    │   ├── README.md
    │   ├── tasks/                  #
    │   │   └── main.yml            #  <-- tasks file can include smaller files if warranted
    │   ├── templates/              #  <-- files for use with the template resource
    │   │   └── ntp.conf.j2         #  <------- templates end in .j2
    │   ├── tests/                  #
    │   │   ├── inventory           #
    │   │   └── test.yml            #
    │   └── vars/                   #
    │       └── main.yml            #  <-- variables associated with this role
    └── fooapp/                     # same kind of structure as "common" was above, done for the fooapp role
        ├── defaults/
        ├── files/
        ├── handlers/
        ├── library/
        ├── lookup_plugins/
        ├── meta/
        ├── module_utils/
        ├── tasks/
        ├── templates/
        ├── tests/
        └── vars/
```
