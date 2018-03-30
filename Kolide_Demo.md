# Enroll in Kolide Fleet

## Install Chocolatey
Chocolatey is a package manager for Windows

`Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`


## Install OSQuery and osqueryd service
`choco install osquery --params="/InstallService"`

Root directory: `C:\ProgramData\osquery\`

## Download cert and key
Browse to [fleet.scriptingis.life]("https://fleet.scriptingis.life") and login. Click 'Add New Host' in the top right.

`admin : g0tn-d3m0`

Download Kolide Certificate to `C:\ProgramData\osquery\certs\fleet.scriptingis.life.pem`

Edit `osquery.flags` and add:
```
--enroll_secret=L7BNXVfV95+Qsf8lRBGgD3IXI4erIWIG
--tls_server_certs=C:\ProgramData\osquery\certs\fleet.scriptingis.life.pem
--tls_hostname=fleet.scriptingis.life:443
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