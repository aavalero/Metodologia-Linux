## RECURSOS
General
[Hacking Épico](https://hackingepico.com/)

[VeryLazyTech Hacking Guide | VeryLazyTech](https://www.verylazytech.com/)

[GitHub - RoqueNight/Linux-Privilege-Escalation-Basics: Simple and accurate guide for linux privilege escalation tactics](https://github.com/RoqueNight/Linux-Privilege-Escalation-Basics)

https://github.com/gurkylee/Linux-Privilege-Escalation-Basics

Binarios vulnerables
https://gtfobins.org

Capabilities
[Exploiting CAP_SYS_MODULE in Linux | Redfox Security](https://redfoxsec.com/blog/exploiting-linux-capabilities-capsysmodule-exploits/)

Evadir restricciones de bash
[Bypassing Bash Restrictions - Rbash | VeryLazyTech](https://www.verylazytech.com/linux/bypassing-bash-restrictions-rbash)

Cronjobs
[Escalada de Privilegios a través de Cron Jobs en Linux – Deep Hacking](https://blog.deephacking.tech/es/posts/escalada-de-privilegios-a-traves-de-cronjobs-linux/#comandos-crontab)

Metasploit
https://www.offsec.com/metasploit-unleashed/privilege-escalation/

## BUENAS PRACTICAS

Reutilizar contraseñas conocidas
Buscar credenciales en directorios poco comunes como /var/www; /tmp; /opt
Revisar servicios y/o programas que corran como root
Buscar archivos que permitan escritura
Revisar el PATH por si es vulnerable
Revisar las versiones de todo
Revisar tareas programadas
Comprobar binarios que puedan ser explotados

## ENUMERACIÓN AUTOMATIZADA

- LINENUM
```
--- IMPORTANTE ---
chmod +x LinEnum.sh
-------------------
./LinEnum.sh -t (Escaneo profundo)
```
- LINPEAS
```
--- IMPORTANTE ---
chmod +x linpeas.sh
-------------------
./linpeas.sh
```

## ENUMERACIÓN MANUAL

Historial de comandos
```
history
```

Binarios
```
sudo -n -l | grep -E "User|may run|NOPASSWD"
sudo -l (si no queremos filtrar con grep)
```

Claves ssh
```
ls -la "$HOME/.ssh" 2>/dev/null
```

Puertos y servicios
```
netstat -lptun
systemctl list-units --type=service --state=running 2>/dev/null
```

Rutas de interés
```
/etc/passwd
/etc/shadow
```

Grupos e IDs de usuarios
```
id
whoami
groups
getent group | grep -E "sudo|adm|docker|lxd|disk|video"
echo $SHELL
echo $HOME
echo $PATH
```

Logins
```
w 2>/dev/null
last -n 5 2>/dev/null
```

Permisos de usuarios y grupos
```
find / -perm -4000 -type f 2>/dev/null (Se ejecuta como usuario del archivo)
find / -perm -2000 -type f 2>/dev/null (Se ejecuta como el grupo del archivo)
```

Unidades montadas
```
mount
lsblk
cat /etc/fstab
```

Tareas Programadas - Crontab
```
crontab -l
ls -la /etc/cron*
cat /etc/crontab
```

Procesos
```
ps aux | grep root
pstree -p (lista como un tree)
```

Kernel
```
uname -a
```
Exploits de Kernel
https://github.com/ly4k/PwnKit
https://github.com/firefart/dirtycow

