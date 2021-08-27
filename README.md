# Argon

Minecraft client written in Python. Work in progress, not all versions may be usable as of yet due to minor differences in formatting.

## Features

Argon will manage the following elements of Minecraft for you.

* Portable Java versions courtesy of [AdoptOpenJDK](https://api.adoptopenjdk.net/)'s API.
* Different Mojang accounts and their sessions.
* Any versions you would like to play.

## Requirements

* Python 3.6
* Minecraft account

Java will be installed automatically in a portable directory.

## Usage

```py
py -m argon --help
```

```bash
usage: __main__.py [-h] [-v VERSION] [-u USERNAME] [-p PASSWORD]
                   [--list-accounts]

Minecraft client written in Python.

optional arguments:
  -h, --help            show this help message and exit
  -v VERSION, --version VERSION
                        Version of Minecraft to play.
  -u USERNAME, --username USERNAME
                        Username of the account to use.
  -p PASSWORD, --password PASSWORD
                        Password of the account to use.
  --list-accounts       List all of the available accounts.
```

For example, if you wanted to play version **1.8.9** on an account with the email **user@example.com** (password **my_secure_password**) you would do the following.

```bash
py -m argon --username user@example.com --password my_secure_password --version 1.8.9
```

From here, the user session will be saved to the `accounts.json` file, and so you can remove the `--password` argument next time you want to play.

## Structure

The base directory for all files is `%APPDATA%/.argon/` by default. It can be set to another directory by changing the `path` variable when initializing the `Argon()` object.

The following items will be included in your install regardless of whether or not you start Minecraft. However, some folders will only be generated when certain actions are taken, such as downloading Java runtimes or game assets.

### Files

| Path | Description |
| ---- | ----------- |
| `accounts.json` | All authenticated Minecraft sessions. |
| `profiles.json` | Presets for Minecraft versions, including arguments. |

### Directories

| Path | Description |
| ---- | ----------- |
| `/assets` | List of assets for versions. |
| `/java` | Portable Java (AdoptOpenJDK) versions. |
| `/runtime` | All runtime data will go in this directory, e.g. configs generated by mods. |
| `/versions` | Different Minecraft versions. |