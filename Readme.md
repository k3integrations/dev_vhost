Easily keep your nginx virtual hosts and `/etc/hosts` file up to date with this tool.

It is primarily intended for developers who work on multiple projects.

It allows you to have a single shared [nginx](http://nginx.org/) service running on your system
which directs traffic to each of your projects/apps based on host name.

Each of your projects should have a `config/dev` directory containing:
- `config.json` containing the project name and a list of host names
- `nginx` directory containing at a minimum:
  - `index.conf` containing (or `include`ing) a `server` block for each virtual host used by this project

When you run `vhost install`, this tool will automatically add or update your `nginx` config and
`/etc/hosts` file based on your project's configuration.

## Usage

From the root of your project, run `vhost`, which will show you the usage instructions: 

```
Usage:
  vhost <command> [<options>]
  vhost new <vhost_name> [<options>]
  vhost intsall [<options>]

Commands:
  new      Generate config for a new vhost and copy it into your current project's 'config/dev'
  install  Installs the contents of your project's 'config/dev' into your system nginx config
```

## Requirements

### Nginx

You must have nginx running locally on your system.

On Mac:
```
brew-install nginx
```

On Linux:
```
apt-install nginx
```

`vhost` will automatically detect your nginx "sites" directory, if it is one of
- `/usr/local/etc/nginx/servers`
- `/etc/nginx/sites-enabled`

Otherwise, you must provide it with the `--sites-dir` option.

### jq

```
brew install jq
```

```
apt-install jq
```

### envsubst (gettext)

```
brew install gettext; brew link --force gettext
```

```
apt install gettext-base
```

## Installation

Add the `bin` directory from this project to your `$PATH`.




