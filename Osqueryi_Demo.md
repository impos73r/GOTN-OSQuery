# OSQueryi Demo

## Install Chocolatey
Chocolatey is a package manager for Windows

`Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`


## Install OSQuery and osqueryd service
`choco install osquery --params="/InstallService"`

Root directory: `C:\ProgramData\osquery\`

## Restart `osqueryd` service
`Start-Service osqueryd`
