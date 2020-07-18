The tinyest httpd server

# install

## compile
```
$ gcc micro_httpd.c -o micro_httpd
```

## place into binary
```
$ sudo mv micro_httpd /usr/sbin/micro_httpd
```

## enable as a service
```
$ sudo cp micro_httpd.s{ocket,ervice} /etc/systemd/system/
$ sudo ln -s /etc/systemd/system/micro_httpd.socket /etc/systemd/system/sockets.target.wants/micro_httpd.socket
$ sudo systemctl start micro_httpd.socket
$ sudo systemctl status micro_httpd.socket
```

## test
```
$ echo "GET / HTTP/1.1" | /usr/sbin/micro_httpd /home/gaspard/www/
```
http://localhost:8912 will be serving `/home/gaspard/www/`


# uninstall

```
$ sudo rm /etc/systemd/system/sockets.target.wants/micro_httpd.socket /etc/systemd/system/micro_httpd.s* /usr/sbin/micro_httpd


# debug
`systemctl status micro_httpd.service`
