---
title: usage of ssh config
published: 2023-03-09
description: ssh config is more convenient when we use different platform repos
tag: [git, en]
image: ''
category: 'tech'
draft: false
lang: ''
---

# ssh config

When we have other platforms like GitHub and GitLab on our personal computer, the Git info we submit is globally configured through `git config`, which is not what we want. However, setting up Git config separately for each project can be very cumbersome. In this case, we can use `ssh config` to differentiate multiple platforms.

Run `ssh-keygen -t rsa -f ~/.ssh/<filename>`. Here we set the filename to `id_rsa_github`.

Add the generated public key to GitHub SSH key.

Then execute `mkdir ~/.ssh/config`.

Copy the following content into it:

```bash filename="config"
# GitHub
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_github

# GitLab
Host gitlab.com
  HostName gitlab.com
  User git
  IdentityFile ~/.ssh/id_rsa_gitlab
```

Make sure that the `IdentityFile` path is the path of the key you generated.

Then execute `ssh -T git@github.com` to see if the connection is successful.

This way, whether you submit to GitLab or GitHub repositories, the corresponding config information can be automatically recognized.
