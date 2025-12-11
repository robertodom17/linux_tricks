# linux_tricks
## Borrado y recuperación de /etc/shadow

Supongamos que borramos el fichero `/etc/shadow` en **Ubuntu 24.04** lo que ocurrirá a continuación es que cualquier comando que deseemos ejecutar como superusuario con `sudo` no podrá verificar la clave al no poder verificar la concordancia con el hash de la clave que está en `/etc/shadow`. 
La solución podría ser la siguiente:
1. Reiniciamos Ubuntu y para abrir el menú de arranque de grub pulsamos la tecla **SHIFT** al reiniciar.
2. Elegimos el modo de arranque **RECOVERY** y dentro de el elegimos el modo **ROOT SHELL**, Con ello conseguimos entrar como administrador.
3. Ahora montamos el sistema de ficheros en modo lectura/escritura con el comando `mount -o remount,rw` 
4. Ahora ejecutamos el comando `pwconv`y con ello se vuelve a crear un fichero `/etc/shadow`
5. Como hemos reconstruido el fichero /etc/shadow`ahora es necesario reconstruir las claves de cada usuario
```bash
passwd administrador
passwd usuario
...
```
6. Podemos ver el contenido del fichero shadow con el comando `cat /etc/shadow`y ver el hash de las claves de los usuarios a los que les hemos reconstruido la clave. Ahora podremos volver a loguearnos sin problema en el sistema.
