---
layout: post
title: What is .bash_profile?
description: What does .bas_profile do?
summary: A blog post to inform users on what .bash_profile does.
tags: linux
---

The `.bash_profile` is a script that runs whenever you start a new shell session, if you’re using Bash as your default shell. This file is located in your home directory and is used to configure your shell session. It can contain various commands to set environment variables, define functions, adjust the command prompt, set aliases, and more.

It’s important to note that `.bash_profile` is only run for login shells (i.e., shells that are started when you log in to your system). For non-login shells, Bash runs `.bashrc` instead. Some users choose to source `.bashrc` from their `.bash_profile` to ensure that the same configurations are applied to both login and non-login shells.

Here’s a simple example of a `.bash_profile` file:

```bash
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs
PATH=$PATH:$HOME/bin

export PATH
```

This `.bash_profile` does a few things:

* It first checks if a file named `.bashrc` exists in the home directory. If it does, it sources it. This means it runs the file in the current shell, not a subshell, so any changes made in `.bashrc` will affect the current shell.

* Then it adds `$HOME/bin` to the `PATH`. The `PATH` is an environment variable that tells your shell where to look for programs to run. So if you have scripts in `$HOME/bin`, you can run them from anywhere.

* Finally, it exports the `PATH`, making the changes available to all child sessions initiated from this session. This means any terminal sessions you start from this session will have the updated `PATH`.

Remember, this is just an example. Your `.bash_profile` can contain other environment variables, functions, and commands depending on your needs.