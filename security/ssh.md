# SSH

## Copy SSH Key to Clipboard

```sh
pbcopy < ~/.ssh/id_rsa.pub
```

## List existing SSH keys

```sh
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

## [Generating a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key)

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

---

-   There is no max bit-size defined by the protocol, but server's may kick you if you take too long

    -   2048 used to be safe, now is not
    -   4096 is the best-practice

---

## References

-   [GitHub: Generating an SSH key](https://help.github.com/articles/generating-an-ssh-key)
-   [ServerFault: OpenSSH : Key-based authorization, maximum key length](http://serverfault.com/questions/160268/openssh-key-based-authorization-maximum-key-length)
