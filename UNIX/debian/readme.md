# Debian-specific informations

## sudoers

```bash
adduser <username> sudo
```

## find a module containing a specific binary

```bash
apt install apt-file
apt update
apt-file search --regexp '/<binary>$'
```