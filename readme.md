# The tinyest httpd server

this tiny httpd server needs systemd to run (available in most linux distros)
it listens for input socket connections and returns html pages

# usage

## compile
```
$ gcc micro_httpd.c -o micro_httpd
```

## place into binary

as root
```
mv micro_httpd /usr/sbin/micro_httpd
```

## enable as a service

as root
```
cp micro_httpd.s{ocket,ervice} /etc/systemd/system/
ln -s /etc/systemd/system/micro_httpd.socket /etc/systemd/system/sockets.target.wants/micro_httpd.socket
systemctl start micro_httpd.socket
systemctl status micro_httpd.socket
```

## test
```
echo "GET / HTTP/1.1" | /usr/sbin/micro_httpd /home/gaspard/www/
```
* http://localhost:8912 will be serving `/home/gaspard/www/`


# uninstall

as root
```
rm /etc/systemd/system/sockets.target.wants/micro_httpd.socket /etc/systemd/system/micro_httpd.s* /usr/sbin/micro_httpd
```

# debug

as root
```
systemctl status micro_httpd.socket
systemctl status micro_httpd.service
```
