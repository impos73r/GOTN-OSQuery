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

Check for accessibility tools cmd.exe file replacement backdoor.

`SELECT * FROM hash WHERE (path='c:\\windows\\system32\\osk.exe' OR path='c:\\windows\\system32\\sethc.exe' OR path='c:\\windows\\system32\\narrator.exe' OR path='c:\\windows\\system32\\magnify.exe' OR path='c:\\windows\\system32\\displayswitch.exe') AND sha256 IN (SELECT sha256 FROM hash WHERE path='c:\\windows\\system32\\cmd.exe' OR path='c:\\windows\\system32\\WindowsPowerShell\\v1.0\\powershell.exe' OR path='c:\\windows\\system32\\explorer.exe') AND sha256!='e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855';`
