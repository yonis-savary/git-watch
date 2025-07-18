# git-watch

Bash script to automatically pull changes and (re)build your app every X seconds

## Requirements

- git
- bash (present on most popular linux distros)

# Installation

```sh
mkdir /opt
cd /opt
git clone git@github.com:yonis-savary/git-watch.git # OR https://github.com/yonis-savary/git-watch.git

sudo ln -s /opt/git-watch/git-watch /usr/local/bin/git-watch
# Or add /opt/git-watch in your $PATH
```

## How does it work

The script initialy start a "runner" version of itself, which contains the actual code

When the runner works:
- Fetch for changes on `--branch`
- If any :
    - Execute `--command`
- Sleep `--sleep` seconds (10 minutes by default)

Here is two simple examples
```sh
git-watch --output ./watch.logs --command "npm ci"

git-watch --main feature-branch --sleep 600 --command "npm ci"
```

Additionnally, you can specify a log file with `--output`, 
a repository path with `--path` (current directory by default),
and a runner process name with `--name` (It is advised that you let git-watch decide itself)

If you want to stop your runner instance, simply use 
```sh
git-watch --uninstall
```