# Selenium

A portable software testing framework for web applications.


## Installation & Setup

```sh
brew install selenium-server-standalone
```

```sh
# To have launchd start selenium-server-standalone at login:
ln -sfv /usr/local/opt/selenium-server-standalone/*.plist ~/Library/LaunchAgents

# Then to load selenium-server-standalone now:
launchctl loa~/Library/LaunchAgents/homebrew.mxcl.selenium-server-standalone.plist

# Or, if you don't want/need launchctl, you can just run:
selenium-server -p 4444
```
