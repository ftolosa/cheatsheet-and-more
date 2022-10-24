## Linux Cheatsheet

Listar usuarios
`cat /etc/passwd`

Listar grupos y usuarios asignados a grupos
``cat /etc/group``

Listar usuarios por grupo
``groups nombregrupo``

Agregar usuario
``
useradd [OPTIONS] USERNAME
-m -- Crear el directorio de home
https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/
``

Agregar usuario a grupo
``sudo usermod -aG grupo usuario``

Crear carpeta .ssh y archivo authorized_keys
``
sudo mkdir /home/usuario/.ssh
sudo touch /home/usuario/.ssh/authorized_keys
``

Para ver consumo de discos
``
df -h
``

Detalle de almacenamiento de la carpeta en la cual estamos parados. Se puede ver el detalle de archivos
``
du -h
sudo du /var/dehonline/contracts | sort -rn | head -n 10
``

Encontrar archivos mayor a 14 dias y eliminar
``sudo find  /home/ec2-user/lexbox/data/test4-app/src/storage/logs -atime +14 -delete``

Conocer limites actuales de ficheros
``ulimit -n``

Aumentar limite temporal de ficheros
``ulimit -n XXXX``

Archivo limites
``/etc/security/limits.conf``

Listar servicios
``
systemctl list-units --type=service
systemctl --type=service
``

Listar servicios estado activo
``systemctl --type=service --state=active``

Listar los puertos que estan escuchando en el servidor
``sudo netstat -tulpn | grep LISTEN``

Cambiar contraseña de usuario
``chage -l <username>``

Ver ejecuciones de Crontab
``
grep CRON /var/log/syslog
o
cat /var/log/syslog
``
Archivo donde se encuentra informacion de los volumenes https://keepcoding.io/blog/que-es-el-fichero-fstab-en-linux/
`/etc/fstab`
Opciones
Esta campo del archivo FSTAB hace referencia a las opciones de montaje. Deben ir separadas por comas. Algunas de opciones son:

* auto: para que la partición se monte al arrancar «mount -a».
* noauto: opción que impide que la partición se monte automáticamente durante el arranque.
* user: los usuarios tienen permitido montar la partición.
* nouser: solo el usuario root tiene permitido realizar el montaje de la partición.
* ro: partición que solo permite la lectura.
* rw: opción que permite la lectura escritura.
* exec: es posible ejecutar los binarios pertenecientes a esa partición.
* async: esta opción permite que el sistema continúe trabajando luego de una petición de escritura del equipo, aunque no haya recibido la confirmación.
* suid: esta opción permite las operaciones con los bits suid y sgid. Es utilizado para permitir a los usuarios diferentes del root, ejecutar binarios con ciertos privilegios otorgados temporalmente para que realicen una labor determinada.
* nosui: se encarga de impedir el funcionamiento de los bits suid y sgid.
* noatime: esta opción no actualiza el nodo-i de los ficheros con el tiempo de acceso. Además, permite aumentar las prestaciones del sistema, debido a que accede menos al disco.
* diratime: sirve para actualizar el tiempo de acceso a un nodo en el sistema de archivos que se ha montado.
* nodiratime: se impide la actualización del nodo-i de los directorios con el tiempo de acceso. Al igual que la opción noatime, también puede aumentar las prestaciones del sistema.
* defaults: establece que las opciones sean asignadas por defecto gracias al sistema operativo. Estas opciones predeterminadas son  rw, suid, dev, exec, auto, nouser y async.


Nginx con certbot
``
docker run --name nginx-prometheus -v /var/nginx/conf:/etc/nginx/conf.d -v /var/www/certbot:/var/www/certbot -v /etc/letsecrypt:/etc/letsecrypt -p 80:80 -p 443:443 -d nginx
``