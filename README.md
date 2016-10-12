# adapt_authoring-bash
Bash script to automate the installation process

## Supported parameters

| Name | Description |
| :----- | :---------- |
| `test` | Installs a fresh staging copy of the AT, with appropriate settings. Server is run using forever |
| `install app` | Installs a fresh production copy of the AT, with the stored default settings |
| `install db` | Installs a fresh copy of the database, with the stored default settings |
| `update server` | Pulls down the latest server code |
| `update framework` |  Updates the framework core and plugins |

## Functions

### Test install (i.e. `test`)
1. Cleans old install
   * Stops the forever script
   * Deletes old install 
   * Drops old database
1. Gets latest server code
1. Installs node dependencies
1. Runs server install script (install.js) with config values stored in script
1. Starts forever script

### Clean install (i.e. `install app`)
1. Cleans old install
   * Stops the forever script
   * Deletes old install 
   * Drops old database
1. Gets latest server code
1. Installs node dependencies
1. Runs server install script (install.js) with config values stored in script
1. Starts forever script

### DB install (i.e. `install db`)
1. Cleans old install
   * Drops old database
1. Installs node dependencies
1. Runs server install script (install.js) with config values stored in script

### Server update (i.e. `update server`)
1. Stops the forever script
1. Checks production branch for new commits (and pulls)
1. Installs node dependencies
1. Rebuilds front-end

### Framework update (i.e. `update framework`)
1. Stops the forever script
1. Checks for new releases (tags)
1. Checks out latest tag (if applicable)
1. Updates adapt plugins (adapt install)
