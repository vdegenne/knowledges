## Unix

- check if a program use a port
```bash
# netstat -tulpn | grep <program>
```

- open a specific port to the public
```bash
# firewall-cmd --permanent --zone=public --add-port=80/tcp
# systemctl restart firewalld
```

- Installer un package qui a "fail" pendant l'installation manuelle
```bash
# sudo dpkg -i <package-name>
if it fails
# sudo apt-get install -f
```
