# OSQueryi Demo

## Install Chocolatey
Chocolatey is a package manager for Windows

`Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))`


## Install OSQuery and osqueryd service
`choco install osquery --params="/InstallService"`

Root directory: `C:\ProgramData\osquery\`

## Run OSQueryi
From a powershell console: `osqueryi`
Congrats! Now youre up and running with OSQuery.

Check out https://code.facebook.com/posts/844436395567983/introducing-osquery/ & https://code.facebook.com/posts/844436395567983/introducing-osquery/ for some example queries to run.
