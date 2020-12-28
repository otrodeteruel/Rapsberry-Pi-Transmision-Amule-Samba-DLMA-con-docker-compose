# Rapsberry Pi download and server video

Usamar el rapsberry como equipo para tener un amule, un transmitions que es un cliente Torrent, para poder descargar archivos al tratarse de un equipo de bajo consumo y no hay problema en dejarlos encendido continuamente.
Le ponemos tambien el servidio de youtube-dl que nos permite descargar videos de youyube y si lo necesitamos convertirlos a mp3.
le instalamos un servidor samba y un servidor dlna para compartir los archivos por la red

Todo montado sobre docker con lo que ponerlo en marcha es cuestion de 2 minutos.,.


para ver la instalacion inicial de rapsberry y docker en la misma ver :

# Previo

necesitamos montar un disco duro sobre la rapsberry para tener una capacidad de almacenaje

## Montar discos externos en el arranque

https://geekland.eu/montar-particion-ntfs-fat-o-ext4-en-el-arranque-del-sistema/

PASO 1. Conocer la denominación de la partición que queremos montar

    sudo  fdisk -l

PASO 2. Conocer el punto de montaje y tipo de la unidad que vamos a montar

    ls -l /dev/disk/by-uuid

PASO 3. Crear la carpeta donde se montará nuestra partición

    sudo mkdir /media/disco

PASO 4. Configurar que cada que arranquemos el sistema se monte la unidad

Para decirle a nuestro sistema que monte la unidad debemos configurar el archivo /etc/fstab.

    sudo nano /etc/fstab

Montar unidad ext4

    UUID=XXXXXXXXXXXX /media/disco ext4 errors=remount-ro 0 1


## copiar archivos al servidor

## samba

servidor samba, compartir los archivos por la red con otros dispositivos. 

    smb://192.168.1.222

https://github.com/dperson/samba


## rpi-monitor

sistema de monitorizadion de nuestra raspberry, capacidad, temperatura ...

https://github.com/michaelmiklis/docker-rpi-monitor


## minidlna

En mi caso tengo una televison LG que tiene una entrada de red y utiliza un sistema llamado DLNA, con esto puedo ver los archivos descagado en la tele

https://github.com/vladgh/docker_base_images/tree/master/minidlna

##  Docker en transmision

Cliete torrent para descargar archivos

    us: 1234
    ps: 1234

https://gitlab.com/jaymoulin/docker-transmission


##  Docker en amule

Cliente de redes P2P tipo Emule, para descargar archivos

    ps: 1234

