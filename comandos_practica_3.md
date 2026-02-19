##### **#Configuración de grub2**



\#modificación del menu grub 

Sudo namo /etc/default/grub



\#Guardar cambios 

sudo grub2-mkconfig -o /boot/grub2/grbcfg



\#Revisar cambio del tiempo de espera

grep GRUB\_TIMEOUT /etc/default/grub



\#Cambio de contraseña root 



\#Reinicio del sistema

reboot



\#Estando en el menu 

una vez en el menu presionamos la e

después nos dirigimos al comando que dice Linux root y vamos al final del código y escribimos init=/bin/bash luego le damos a Control + x 



\#Después de estar en el apartado de recuperación 

una vez en el menu donde vamos a recuperar la cuenta usamos el comando: mount -o remount,rw /



\#Comando para cambiar la contraseña 

passwd root 

colocamos la nueva contraseña



\#Guardamos con el comando:

touch /.autorelabel



\#Salimos con:

exec /sbin/init o reboot 





##### \#Creación de scripts en bash



\#Creación del archivo

nano backup.sh



\#Código que nos permitirá ejecutar la tarea 



\#!/bin/bash



FOLDER="/home/carlos"

TIMESTAMP=(date +"%d-%m-%Y\_%H-%M")

BACKUP\_NAME="backup-$TIMESTAMP.tar.gz"

DESTINATION="/home/carlos"

tar -czf "$DESTINARTION/$BACKUP\_NAME" "$FOLDER"

echo "Back creado exitosamente en /home/carlos"



\#Otorgación de permisos de ejecución

chmod +x backup.sh



\#Ejecución del script

./backup.sh



\#Creación del archivo

nano ifconfig.sh



\#Código que nos permitirá ejecutar la tarea

\#!/bin/bash



read -p "Ingrese el nombre del archivo: " nombre

ifconfig > ~/${nombre}.txt

echo "Archivo creado exitosamente con el nombre: ${nombre}.txt"



\#Otorgación de permisos de ejecución

chmod +x ifconfig.sh



\#Ejecución del script

./ifconfig.sh



\#Colocacion del nombre del archivo TXT

red\_local



\#Lectura del archivo

cat red\_local.txt





##### \#Configuración de SSH

 

\#Actualizacion de los repositorios del sistema

sudo dnf update



\#Comando de descarga del servidor ssh 

sudo dnf install opensshd-server



\#Permite verificar el estado del servidor ssh

sudo systemctl status sshd



\#Permite iniciar desde cero el servidor 

sudo systemctl start sshd



\#Permite parar el servidor completamente 

sudo systemctl stop sshd



\#Habilita el servicio ssh

sudo systemctl enable sshd



\#Lo deshabilita 

sudo systemctl disable sshd



\#Reinicia el servidor en caso de falla o de que lo necesite 

sudo systemctl restart sshd



\#Permite ver la ip de la maquina 

ip a



\#Prueba de conexión desde la otra maquina 

ping ip de la maquina



\#Comando de acceso al servidor ssh

ssh usario@ y la ip del servidor



\#Creacion de llaves publicas y privadas

ssh-keygen -t rsa -b 4096



\#Ubicacion para guardar las llaves 

/home/usuario/.ssh/winssh



\#Creación del directorio ssh

mkdir -p ~/.ssh



\#Otorgación de los permisos a ese directorio 

chmod 770 ~/.ssh



\#Colocar la llave en el archivo de autorizacion 

echo  #la llave /.ssh/authorized\_keys



\#Permisos al archivo de autorización 

cmod 600 ~/.ssh/authorized\_keys



\#Acceder al archivo ssh 

cd ~/.ssh



\#Editar el archivo de autorización 

sudo nano authorized\_keys



\#Otra manera de crear el archivo ssh darle permisos y la creación del archivo de autorización 

ssh carlos@192.168.174.129 "mkdir -p ~/.ssh \&\& cat >> ~/.ssh/authorized\_keys \&\& chmod 700 ~/.ssh \&\& chmod 600 ~/.ssh/authorized\_keys"

