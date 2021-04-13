# intellij-codespaces
Run JetBrains IDEs in your [Codespace](https://github.com/features/codespaces) and connect to it via [Projector](https://blog.jetbrains.com/blog/2021/03/11/projector-is-out/).

* Plugins and settings should be maintained as long as you don't delete the Codespace (suspending should be ok).
* Git credentials should be injected via the normal process and work.
* Dotfiles should be installed via the normal Codespaces process.

**Note:** This is more or less just a hack that leverages that fact that Codespaces lets you influence what it runs in Docker and will do port forwarding for you.

## Steps
1. Launch this repo as a Codespace
1. Connect to http://127.0.0.1:8887 in a browser or with the [Projector client application](https://github.com/JetBrains/projector-client/releases).

## Customization
* You can customize which IDE you run via the `FROM` line in the Dockerfile.  The complete list of images that JetBrains publishes can be found [here](https://github.com/JetBrains/projector-docker#run-jetbrains-ide-in-docker).
* You will probably want add any SDKs or other tools you need to the Dockerfile so that they are automatically installed.

## Known Issues
* If you aren't active in VSCode for 30 min, it is probably going to suspend the Codespace due to inactivity :-(.
* No state is saved if you delete the Codespace.
