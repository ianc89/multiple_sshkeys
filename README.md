# multiple_sshkeys
_How to use multiple GitHub accounts with ssh keys_

In some instances you may need to use multiple ssh keys for different accounts (ie personal, work, etc). This is not as painful as it first seems.

# Generate the ssh keys

Follow the GitHub instructions for generating your ssh key: https://docs.github.com/en/authentication/connecting-to-github-with-ssh

```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Place into a well defined file, eg `~/.ssh/id_github_personal`

Then do the same but for your other account:
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Place into a well defined file, eg `~/.ssh/id_github_work`

You will need to add both of these to your ssh-agent
```
ssh-agent -k ~/.ssh/id_github_personal
ssh-agent -k ~/.ssh/id_github_work
```
and also copy the relevant information into your github ssh-key account
```
pbcopy < ~/.ssh/id_github_personal.pub
pbcopy < ~/.ssh/id_github_work.pub
```