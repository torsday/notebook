# Fundamental Underpinnings

## The Internet (5 layers)

1. Application
1. Transport
    * everything runs here; for HTTP, that's TCP
1. Network
1. Link
1. Physical


## SSH

### Copy SSH Key to Clipboard

```sh
pbcopy < ~/.ssh/id_rsa.pub
```

### Checking for existing SSH keys

```sh
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

### [Generating a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key/)

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# Creates a new ssh key, using the provided email as a label
```

### Adding a new SSH key to the ssh-agent
