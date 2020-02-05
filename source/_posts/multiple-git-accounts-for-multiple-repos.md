---
title: Git-How to set multiple accounts for different git repository
tags:
  - Git
  - SSH
id: 1
categories:
  - Git
  - Linux
date: 2014-02-03 06:40:12
---

<u>*Question*</u>

I have a github account for my personal projects and blogs. Meanwhile my company is also using git, but I just have one laptop. I shall be able to access both of them from my laptop.

<u>*Solution*</u>

Solution is always simple and cheap. I am using cygwin as default shell. Please use it as a reference if you are using windows.

# Step 1: Generate different key files

Obviously different git sites need to have solely key file.

```
$ ssh-keygen -t rsa -C "scopic78@hotmail.com" -f id_rsa_git_hub
$ ssh-keygen -t rsa -C "scott.wu@mycompany.com" -f id_rsa_company
```

Now you will get 4 files: id_rsa_git_hub, id_rsa_git_hub.pub, id_rsa_company, id_rsa_company.pub

# Step 2: Register your pub key

You need to register pub keys into github and private git server, such as gerrit. No tips. You shall know how to do it.

# Step 3: ssh configuration

This is most important step. You need to create a file named “config” in your ~/.ssh folder. The content :

```
##Github
Host github
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa_git_hub
##private gerrit
Host work
HostName gerrit.mycompany.com
User git
IdentityFile ~/.ssh/id_rsa_company
```

Now everything is done. You can clone repos from different platform.

# Step 4: Git configuration

As you known Git is using your user.name and user.email to show author in project. Please don’t forget to configure your git. Later I will write something about this basic git configuration.