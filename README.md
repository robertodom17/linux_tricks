# linux_tricks
Trucos de Linux interesantes

Supongamos que borramos el fichero /etc/shadow en Ubuntu 24.04 lo que ocurrirá a continuación es que cualquier comando que deseemos ejecutar como superusuario con sudo no podrá verificar la clave al no poder verificar la concordancia con el hash de la clave que está en /etc/shadow. 
La solución podría ser la siguiente:
1.- Reiniciamos Ubuntu y para sacar el menú de arranque de grub pulsamos la tecla SHIFT al reiniciar.
2.- Elegimos el modo de arranque RECOVERY y dentro de el elegimos el modo ROOT SHELL, Con ello conseguimos entrar como administrador.
3.- Ahora montamos el sistema de ficheros con 'mount -o remount,rw'
