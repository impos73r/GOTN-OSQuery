# Guardians Of The Network-OSQuery Presentation

Hello Everyone!
This is the repo for the GOTN OSQuery Presenation. We should have some Ansible Stuff as wll as the OSQuery/Kolide Fleet 
stuff in here at some point in the near future.

### Links
[ReadTheDocs](https://osquery.readthedocs.io)

[Install on Windows](https://osquery.readthedocs.io/en/stable/installation/install-windows/)

[OSQuery Intro to SQL](https://osquery.readthedocs.io/en/stable/introduction/sql/)

[Windows Package Install Ansible Docs](http://docs.ansible.com/ansible/latest/win_package_module.html)

### osqueryi
```
.tables # Show all available tables
.schema # Show CREATE statement which displays available columns
.all    # Select everything from a table
.exit
```
#### Example Queries

`SELECT * FROM logged_in_users;`

View all programs that run at startup
`SELECT name, path FROM startup_items;`

`SELECT name FROM chrome_extensions;`

`SELECT * FROM listening_ports ORDER BY pid;`

`SELECT * FROM hash WHERE directory='C:\_CSECTOOLS\';`

Find processes whose binary has been deleted from disk.
`SELECT pid, name, path FROM processes WHERE on_disk = 0;`

