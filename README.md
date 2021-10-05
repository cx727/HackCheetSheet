# ⭐️HackCheetSheet⭐️

Este sera un repositorio en donde ire añadiendo todo el conocimiento que vaya adquiriendo sera una guia para mi ojala le pueda servir a alguien como a mi. 

<h2> 💻 Linux 💻</h2>

Checar todos los paquetes instalados.

```bash
apt list --installed
```

To add OpenSSH to the SysV script to tell the system to run this service after startup, we can link it with the following command:

```bash
systemctl enable ssh
```

The tool journalctl to view the logs. Se puede ver que usuario inicio el servicio.
 
```bash
journalctl -u ssh.service --no-pager
```
El comando find y sus multiples usos!

```bash
find / -name *.conf -type f -size +25k -size -28k 2>/dev/null # archivo de peso mayor a 25k y menor a 28k!
find / -type f -name *.conf -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null # ejecuta con lo que encuentra el comando {} aqui se pone el nombre que se vaya encontrando lo probe con cp intentalo!
```
El comando netstat sustituido por ss
```bash
ss -l -4 | grep -v "127\.0\.0" | grep "LISTEN" | wc -l #Saca todas las conecciones en escucha sin localhost y te dice cuantas hay
```
CURL una especie de spider para ver rutas en una pagina

```bash
curl https://www.inlanefreight.com > htb.txt && cat htb.txt | tr " " "\n" | cut -d"'" -f2 | cut -d'"' -f2 | grep "www.inlanefreight.com" | sort -u | wc -l
```


<h2> 😊 Web Servers😊 </h2>

Linea para crear un servidor web que yo he probado y me han funcionado.

<h4>PHP</h4>

```php
php -S 127.0.0.1:8000
```
<h4>Python</h4>

```python
python -m http.server 8000
```

<h4>NodeJs</h4>

```javascript
npm install -g node-static   # install dependency
static -p 8000
```
<h4>PERL</h4>

```perl
cpan HTTP::Server::Brick   # install dependency
perl -MHTTP::Server::Brick -e '$s=HTTP::Server::Brick->new(port=>8000); $s->mount("/"=>{path=>"."}); $s->start'
```
<h2> Sniffers </h2>

```bash
sudo tcpdump -i eth0 host 10.10.14.2 and 10.129.2.28 # captura en la interfaz eth0
```



