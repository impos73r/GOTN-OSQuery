# Enroll in Kolide Fleet

## Install Chocolatey
Chocolatey is a package manager for Windows

`Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`


## Install OSQuery and osqueryd service
`choco install osquery --params="/InstallService"`

Root directory: `C:\ProgramData\osquery\`

## Download cert and key
Browse to the hostname of your kolide UI and login. Click 'Add New Host' in the top right.

Download Kolide Certificate to `C:\ProgramData\osquery\certs\fleet.scriptingis.life.pem`

Edit `osquery.flags` and add:
```
--enroll_secret= {{SECRET KEY}}
--tls_server_certs= {{KEY FILE}}
--tls_hostname= {{HOSTNAME}}
--host_identifier=hostname
--enroll_tls_endpoint=/api/v1/osquery/enroll
--config_plugin=tls
--config_tls_endpoint=/api/v1/osquery/config
--config_tls_refresh=10
--disable_distributed=false
--distributed_plugin=tls
--distributed_interval=3
--distributed_tls_max_attempts=3
--distributed_tls_read_endpoint=/api/v1/osquery/distributed/read
--distributed_tls_write_endpoint=/api/v1/osquery/distributed/write
--logger_plugin=tls
--logger_tls_endpoint=/api/v1/osquery/log
--logger_tls_period=10
  ```
  
  ## Restart `osqueryd` service
`Start-Service osqueryd`
