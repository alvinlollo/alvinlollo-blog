---
title: Pawnagotchi plugins using CLI
date: 2024-12-02
tags:
  - Raspberry
  - Debian
  - CLI
  - "#Pwnagotchi"
---
## A command to install plugins

This is the main way of how the pawnagotchi uses plugins, suprisingly it's extremely similar to apt.
```bash
sudo pawnagotchi plugins
```

A way of updating the plugins just like apt just put update in front of the command

```bash
sudo pawnagotchi plugins update
```

## Adding plugin repos to pwnagotchi

If you want to add repos to update from then edit the file: `/etc/pawnagotchi/config.toml`

And add the lines:
```toml
custom.plugins_list = (
"https://a.github.com/repo.zip"

)
```

Make sure to add a comma of you want to add more than one!

```toml
custom.plugins_list = (
"https://a.github.com/repo.zip",
"https://another.github.com/repo.zip"

)
```

## Listing plugins

To list current installable plugins from all repos added just use:

```bash
sudo pawnagotchi plugins list
```
You should use this command after you use the `sudo pwnagotchi plugins update` command to ensure the latest update and repos are correctly added.

## Installing plugins

To install pwnagotchi plugins use the command:

```bash
sudo pawnagotchi plugins install <plugin_name>
```
Use the plugin name on the list command and make sure to check the case

## Further information:

Custom plugins are stored usually on ``/use/local/pwnagotchi/custom-plugins``

So if you have access to FileZilla or some other FTP client you can connect to your pwnagotchi and copy custom plugins. Directly into your pwnagotchi (plugins are .py or python scripts, just so you know).

Just make sure to change 
```conf
permitRootLogin = prohibitPassword
```
to :


which can be found in etc/ssh/sshd.config