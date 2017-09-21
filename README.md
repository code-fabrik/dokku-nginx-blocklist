# Dokku Nginx Blocklist

Block clients accessing your Dokku instance by blacklisting user agents, IP addresses and IP subnets.

## Installation

```shell
# on 0.4.x+
sudo dokku plugin:install https://github.com/code-fabrik/dokku-nginx-blocklist.git
```

## Usage

Upload a file named `DOKKU_NGINX_BLOCKLIST` to the root of your application where the block rules are defined in the format expected by NGINX.

Note: rules are checked in the order of their appearance to the first match.

You can either block by IP or subnet:

```nginx
deny 1.2.3.4;
deny 91.212.45.0/24;
deny 91.212.65.0/24;
```

You can block by user agent match:

```nginx
deny = wget"                     # exact match
deny ~ (Catall Spider|AcoiRobot) # case sensitive match
deny ~* (foo|bar)                # case insensitive match
```