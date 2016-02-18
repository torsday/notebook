# SSH

## Copy SSH Key to Clipboard

```sh
pbcopy < ~/.ssh/id_rsa.pub
```

## Checking for existing SSH keys

```sh
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

## [Generating a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key/)

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# Creates a new ssh key, using the provided email as a label
```

## Adding a new SSH key to the ssh-agent



Ensure ssh-agent is enabled; start the ssh-agent in the background.

```sh
eval "$(ssh-agent -s)"
Agent pid 59566
```

Add your SSH key to the ssh-agent:

```sh
ssh-add ~/.ssh/id_rsa
```


## References

* [GitHub: Generating an SSH key](https://help.github.com/articles/generating-an-ssh-key/)
