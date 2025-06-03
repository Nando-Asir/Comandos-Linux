# 🐧 Guía Completa de Linux para Administradores de Sistemas
## Ubuntu & Debian - Comandos Esenciales y Administración

[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://www.linux.org/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Debian](https://img.shields.io/badge/Debian-D70A53?style=for-the-badge&logo=debian&logoColor=white)](https://www.debian.org/)

---

## 📋 Tabla de Contenidos

1. [Información del Sistema](#️-información-del-sistema)
2. [Gestión de Archivos y Directorios](#-gestión-de-archivos-y-directorios)
3. [Permisos y Propiedades](#-permisos-y-propiedades)
4. [Gestión de Procesos](#️-gestión-de-procesos)
5. [Gestión de Usuarios y Grupos](#-gestión-de-usuarios-y-grupos)
6. [Gestión de Paquetes](#-gestión-de-paquetes)
7. [Gestión de Servicios](#-gestión-de-servicios)
8. [Red y Conectividad](#-red-y-conectividad)
9. [Gestión de Discos y Sistemas de Archivos](#-gestión-de-discos-y-sistemas-de-archivos)
10. [Monitoreo del Sistema](#-monitoreo-del-sistema)
11. [Logs del Sistema](#-logs-del-sistema)
12. [Crontab y Tareas Programadas](#-crontab-y-tareas-programadas)
13. [Compresión y Archivos](#️-compresión-y-archivos)
14. [Búsqueda y Filtrado](#-búsqueda-y-filtrado)
15. [Transferencia de Archivos](#-transferencia-de-archivos)
16. [Seguridad y Firewall](#-seguridad-y-firewall)
17. [Variables de Entorno](#-variables-de-entorno)
18. [Comandos de Texto](#-comandos-de-texto)

---

## 🖥️ Información del Sistema

### `uname` - Información del kernel y sistema
```bash
# Mostrar toda la información del sistema
uname -a

# Mostrar solo el nombre del kernel
uname -s

# Mostrar la versión del kernel
uname -r

# Mostrar la arquitectura del sistema
uname -m
```

### `lsb_release` - Información de la distribución
```bash
# Información completa de la distribución
lsb_release -a

# Solo mostrar la descripción
lsb_release -d

# Mostrar solo la versión
lsb_release -r
```

### `hostnamectl` - Información del hostname y sistema
```bash
# Mostrar información completa del sistema
hostnamectl

# Cambiar el hostname
sudo hostnamectl set-hostname nuevo-nombre
```

### `uptime` - Tiempo de actividad del sistema
```bash
# Tiempo de actividad y carga del sistema
uptime

# Formato más legible
uptime -p
```

---

## 📁 Gestión de Archivos y Directorios

### `ls` - Listar archivos y directorios
```bash
# Listado básico
ls

# Listado detallado con permisos
ls -l

# Mostrar archivos ocultos
ls -la

# Ordenar por fecha de modificación
ls -lt

# Mostrar tamaños en formato legible
ls -lh

# Listado recursivo
ls -R

# Mostrar solo directorios
ls -d */
```

### `cd` - Cambiar directorio
```bash
# Ir al directorio home
cd ~
cd

# Ir al directorio anterior
cd -

# Ir al directorio padre
cd ..

# Ir a un directorio específico
cd /ruta/al/directorio
```

### `pwd` - Mostrar directorio actual
```bash
# Mostrar ruta completa actual
pwd

# Mostrar ruta física (sin enlaces simbólicos)
pwd -P
```

### `mkdir` - Crear directorios
```bash
# Crear un directorio
mkdir nombre_directorio

# Crear directorios anidados
mkdir -p ruta/completa/al/directorio

# Crear múltiples directorios
mkdir dir1 dir2 dir3

# Crear con permisos específicos
mkdir -m 755 directorio
```

### `rmdir` - Eliminar directorios vacíos
```bash
# Eliminar directorio vacío
rmdir directorio_vacio

# Eliminar directorios padre si quedan vacíos
rmdir -p ruta/completa/directorio
```

### `rm` - Eliminar archivos y directorios
```bash
# Eliminar archivo
rm archivo.txt

# Eliminar múltiples archivos
rm archivo1.txt archivo2.txt

# Eliminar directorio y su contenido recursivamente
rm -r directorio/

# Forzar eliminación sin confirmación
rm -f archivo.txt

# Eliminar recursivamente con confirmación
rm -ri directorio/

# Eliminar archivos por patrón
rm *.txt
```

### `cp` - Copiar archivos y directorios
```bash
# Copiar archivo
cp origen.txt destino.txt

# Copiar archivo a directorio
cp archivo.txt /ruta/destino/

# Copiar directorio recursivamente
cp -r directorio_origen/ directorio_destino/

# Copiar preservando atributos
cp -p archivo.txt copia.txt

# Copiar con confirmación antes de sobrescribir
cp -i archivo.txt destino.txt

# Copiar mostrando progreso
cp -v archivo.txt destino.txt
```

### `mv` - Mover/renombrar archivos y directorios
```bash
# Renombrar archivo
mv nombre_viejo.txt nombre_nuevo.txt

# Mover archivo a directorio
mv archivo.txt /ruta/destino/

# Mover múltiples archivos
mv archivo1.txt archivo2.txt /destino/

# Mover con confirmación
mv -i archivo.txt destino.txt
```

### `ln` - Crear enlaces
```bash
# Crear enlace duro
ln archivo.txt enlace_duro.txt

# Crear enlace simbólico
ln -s /ruta/completa/archivo.txt enlace_simbolico.txt

# Crear enlace simbólico a directorio
ln -s /ruta/directorio/ enlace_dir
```

---

## 🔐 Permisos y Propiedades

### `chmod` - Cambiar permisos
```bash
# Usando notación octal
chmod 755 archivo.txt    # rwxr-xr-x
chmod 644 archivo.txt    # rw-r--r--
chmod 600 archivo.txt    # rw-------

# Usando notación simbólica
chmod u+x archivo.txt    # Dar ejecutar al propietario
chmod g+w archivo.txt    # Dar escribir al grupo
chmod o-r archivo.txt    # Quitar leer a otros
chmod a+r archivo.txt    # Dar leer a todos

# Recursivo para directorios
chmod -R 755 directorio/

# Ejemplos comunes
chmod +x script.sh       # Hacer ejecutable
chmod 777 archivo.txt    # Todos los permisos para todos
```

### `chown` - Cambiar propietario
```bash
# Cambiar propietario
sudo chown usuario archivo.txt

# Cambiar propietario y grupo
sudo chown usuario:grupo archivo.txt

# Solo cambiar grupo
sudo chown :grupo archivo.txt

# Recursivo para directorios
sudo chown -R usuario:grupo directorio/

# Cambiar como el archivo de referencia
sudo chown --reference=archivo_ref archivo_destino
```

### `chgrp` - Cambiar grupo
```bash
# Cambiar grupo de un archivo
sudo chgrp grupo archivo.txt

# Recursivo para directorios
sudo chgrp -R grupo directorio/
```

### `umask` - Máscara de permisos por defecto
```bash
# Ver umask actual
umask

# Establecer umask
umask 022    # Archivos: 644, Directorios: 755
umask 002    # Archivos: 664, Directorios: 775
```

---

## ⚙️ Gestión de Procesos

### `ps` - Mostrar procesos
```bash
# Procesos del usuario actual
ps

# Todos los procesos con detalles
ps aux

# Procesos en forma de árbol
ps auxf

# Procesos de un usuario específico
ps -u usuario

# Procesos por PID
ps -p 1234

# Formato personalizado
ps -eo pid,ppid,cmd,%mem,%cpu
```

### `top` - Monitor de procesos en tiempo real
```bash
# Monitor básico
top

# Ordenar por uso de memoria
top (luego presionar 'M')

# Ordenar por uso de CPU
top (luego presionar 'P')

# Mostrar solo procesos de un usuario
top -u usuario

# Actualizar cada 2 segundos
top -d 2
```

### `htop` - Monitor mejorado (requiere instalación)
```bash
# Instalar htop
sudo apt update && sudo apt install htop

# Ejecutar htop
htop
```

### `kill` - Terminar procesos
```bash
# Terminar proceso por PID
kill 1234

# Forzar terminación
kill -9 1234
kill -KILL 1234

# Terminar graciosamente
kill -15 1234
kill -TERM 1234

# Listar señales disponibles
kill -l
```

### `killall` - Terminar procesos por nombre
```bash
# Terminar todos los procesos con ese nombre
killall firefox

# Forzar terminación
killall -9 firefox

# Terminar procesos de un usuario
sudo killall -u usuario
```

### `pkill` - Terminar procesos con patrones
```bash
# Terminar por nombre parcial
pkill fire

# Terminar procesos de un usuario
pkill -u usuario

# Terminar por comando completo
pkill -f "comando completo"
```

### `nohup` - Ejecutar comandos sin colgar
```bash
# Ejecutar comando que continúe tras cerrar terminal
nohup comando &

# Redirigir salida
nohup comando > salida.log 2>&1 &
```

### `jobs` - Gestión de trabajos en segundo plano
```bash
# Listar trabajos activos
jobs

# Traer trabajo a primer plano
fg %1

# Enviar trabajo a segundo plano
bg %1

# Enviar proceso actual a segundo plano
Ctrl+Z (luego bg)
```

---

## 👥 Gestión de Usuarios y Grupos

### `useradd` - Agregar usuarios
```bash
# Crear usuario básico
sudo useradd nombre_usuario

# Crear usuario con directorio home
sudo useradd -m nombre_usuario

# Crear usuario con shell específico
sudo useradd -s /bin/bash nombre_usuario

# Crear usuario con grupo específico
sudo useradd -g grupo nombre_usuario

# Crear usuario completo
sudo useradd -m -s /bin/bash -c "Nombre Completo" nombre_usuario
```

### `usermod` - Modificar usuarios
```bash
# Cambiar grupo principal
sudo usermod -g nuevo_grupo usuario

# Agregar a grupos adicionales
sudo usermod -aG grupo1,grupo2 usuario

# Cambiar shell
sudo usermod -s /bin/zsh usuario

# Cambiar directorio home
sudo usermod -d /nuevo/home usuario

# Bloquear usuario
sudo usermod -L usuario

# Desbloquear usuario
sudo usermod -U usuario
```

### `userdel` - Eliminar usuarios
```bash
# Eliminar usuario
sudo userdel usuario

# Eliminar usuario y su directorio home
sudo userdel -r usuario
```

### `passwd` - Cambiar contraseñas
```bash
# Cambiar propia contraseña
passwd

# Cambiar contraseña de otro usuario (como root)
sudo passwd usuario

# Forzar cambio de contraseña en próximo login
sudo passwd -e usuario

# Bloquear cuenta
sudo passwd -l usuario

# Desbloquear cuenta
sudo passwd -u usuario
```

### `su` - Cambiar usuario
```bash
# Cambiar a root
su -

# Cambiar a otro usuario
su - usuario

# Ejecutar comando como otro usuario
su - usuario -c "comando"
```

### `sudo` - Ejecutar comandos como otro usuario
```bash
# Ejecutar comando como root
sudo comando

# Ejecutar comando como otro usuario
sudo -u usuario comando

# Cambiar a root temporalmente
sudo -i

# Editar archivo con permisos elevados
sudo nano /etc/archivo

# Listar permisos sudo del usuario
sudo -l
```

### Gestión de grupos
```bash
# Crear grupo
sudo groupadd nombre_grupo

# Eliminar grupo
sudo groupdel nombre_grupo

# Agregar usuario a grupo
sudo gpasswd -a usuario grupo

# Eliminar usuario de grupo
sudo gpasswd -d usuario grupo

# Listar grupos del usuario
groups usuario

# Ver información de grupo
getent group nombre_grupo
```

---

## 📦 Gestión de Paquetes

### APT (Ubuntu/Debian)
```bash
# Actualizar lista de paquetes
sudo apt update

# Actualizar todos los paquetes
sudo apt upgrade

# Actualización completa del sistema
sudo apt full-upgrade

# Instalar paquete
sudo apt install nombre_paquete

# Instalar múltiples paquetes
sudo apt install paquete1 paquete2 paquete3

# Reinstalar paquete
sudo apt reinstall nombre_paquete

# Eliminar paquete
sudo apt remove nombre_paquete

# Eliminar paquete y configuraciones
sudo apt purge nombre_paquete

# Buscar paquetes
apt search término_búsqueda

# Mostrar información del paquete
apt show nombre_paquete

# Listar paquetes instalados
apt list --installed

# Limpiar caché de paquetes
sudo apt autoclean
sudo apt clean

# Eliminar dependencias no necesarias
sudo apt autoremove
```

### DPKG (Gestión de paquetes .deb)
```bash
# Instalar paquete .deb
sudo dpkg -i paquete.deb

# Eliminar paquete
sudo dpkg -r nombre_paquete

# Listar paquetes instalados
dpkg -l

# Buscar paquete instalado
dpkg -l | grep nombre

# Ver archivos de un paquete
dpkg -L nombre_paquete

# Ver información de paquete
dpkg -s nombre_paquete

# Reparar dependencias rotas
sudo apt --fix-broken install
```

### Snap (Paquetes universales)
```bash
# Instalar snap
sudo snap install nombre_paquete

# Listar snaps instalados
snap list

# Actualizar snaps
sudo snap refresh

# Eliminar snap
sudo snap remove nombre_paquete

# Buscar snaps
snap find término
```

---

## 🔧 Gestión de Servicios

### Systemctl (SystemD)
```bash
# Ver estado de servicio
sudo systemctl status nombre_servicio

# Iniciar servicio
sudo systemctl start nombre_servicio

# Detener servicio
sudo systemctl stop nombre_servicio

# Reiniciar servicio
sudo systemctl restart nombre_servicio

# Recargar configuración sin reiniciar
sudo systemctl reload nombre_servicio

# Habilitar servicio (inicio automático)
sudo systemctl enable nombre_servicio

# Deshabilitar servicio
sudo systemctl disable nombre_servicio

# Listar todos los servicios
systemctl list-units --type=service

# Listar servicios activos
systemctl list-units --type=service --state=active

# Listar servicios fallidos
systemctl list-units --type=service --state=failed

# Ver logs de servicio
sudo journalctl -u nombre_servicio

# Ver logs en tiempo real
sudo journalctl -u nombre_servicio -f
```

### Servicios comunes
```bash
# Apache/Nginx
sudo systemctl status apache2
sudo systemctl status nginx

# SSH
sudo systemctl status ssh
sudo systemctl restart ssh

# MySQL/PostgreSQL
sudo systemctl status mysql
sudo systemctl status postgresql

# Firewall
sudo systemctl status ufw
sudo systemctl status iptables
```

---

## 🌐 Red y Conectividad

### `ip` - Configuración de red moderna
```bash
# Mostrar interfaces de red
ip addr show
ip a

# Mostrar solo IPv4
ip -4 addr show

# Mostrar tabla de rutas
ip route show
ip r

# Agregar IP a interfaz
sudo ip addr add 192.168.1.100/24 dev eth0

# Eliminar IP de interfaz
sudo ip addr del 192.168.1.100/24 dev eth0

# Activar/desactivar interfaz
sudo ip link set eth0 up
sudo ip link set eth0 down
```

### `netstat` - Estadísticas de red
```bash
# Mostrar conexiones activas
netstat -tuln

# Mostrar procesos escuchando
netstat -tlnp

# Mostrar estadísticas de interfaces
netstat -i

# Mostrar tabla de rutas
netstat -r
```

### `ss` - Alternativa moderna a netstat
```bash
# Mostrar todas las conexiones
ss -tuln

# Mostrar procesos
ss -tulnp

# Mostrar solo TCP
ss -tln

# Mostrar solo UDP
ss -uln
```

### `ping` - Probar conectividad
```bash
# Ping básico
ping google.com

# Limitar número de pings
ping -c 4 google.com

# Ping con IPv6
ping6 google.com

# Ping con tamaño de paquete específico
ping -s 1024 google.com
```

### `wget` y `curl` - Descargar archivos
```bash
# Descargar archivo con wget
wget https://ejemplo.com/archivo.zip

# Descargar en directorio específico
wget -P /ruta/destino https://ejemplo.com/archivo.zip

# Descargar con curl
curl -O https://ejemplo.com/archivo.zip

# Descargar y guardar con nombre específico
curl -o nuevo_nombre.zip https://ejemplo.com/archivo.zip

# Seguir redirecciones
curl -L https://ejemplo.com/archivo.zip
```

### `iptraf` y `nethogs` - Monitoreo de red
```bash
# Instalar herramientas
sudo apt install iptraf-ng nethogs

# Monitor de tráfico por interfaz
sudo iptraf-ng

# Ver uso de ancho de banda por proceso
sudo nethogs
```

---

## 💾 Gestión de Discos y Sistemas de Archivos

### `df` - Espacio en disco
```bash
# Mostrar uso de disco
df

# Formato legible para humanos
df -h

# Mostrar tipo de sistema de archivos
df -T

# Mostrar solo sistemas de archivos locales
df -l
```

### `du` - Uso de espacio por directorio
```bash
# Tamaño de directorio actual
du -sh .

# Tamaño de todos los subdirectorios
du -h

# Tamaño de directorio específico
du -sh /ruta/directorio

# Los 10 directorios más grandes
du -h | sort -hr | head -10

# Excluir ciertos directorios
du -h --exclude="*.log" /var
```

### `lsblk` - Listar dispositivos de bloque
```bash
# Mostrar todos los dispositivos
lsblk

# Mostrar con sistema de archivos
lsblk -f

# Mostrar tamaños en formato legible
lsblk -h
```

### `fdisk` - Particionado de discos
```bash
# Listar particiones
sudo fdisk -l

# Particionar disco (CUIDADO!)
sudo fdisk /dev/sda

# Mostrar particiones de un disco específico
sudo fdisk -l /dev/sda
```

### `mount` y `umount` - Montar sistemas de archivos
```bash
# Montar dispositivo
sudo mount /dev/sdb1 /mnt/punto_montaje

# Montar con opciones específicas
sudo mount -o rw,user /dev/sdb1 /mnt/usb

# Desmontar
sudo umount /mnt/punto_montaje

# Desmontar forzadamente
sudo umount -f /mnt/punto_montaje

# Ver sistemas montados
mount | column -t
```

### `fsck` - Verificar y reparar sistemas de archivos
```bash
# Verificar sistema de archivos
sudo fsck /dev/sda1

# Reparación automática
sudo fsck -y /dev/sda1

# Verificar sin montar
sudo fsck -n /dev/sda1
```

---

## 📊 Monitoreo del Sistema

### `free` - Memoria RAM y swap
```bash
# Información básica de memoria
free

# Formato legible
free -h

# Mostrar en MB
free -m

# Actualizar cada 2 segundos
free -s 2
```

### `vmstat` - Estadísticas del sistema
```bash
# Estadísticas básicas
vmstat

# Actualizar cada 2 segundos, 5 veces
vmstat 2 5

# Mostrar estadísticas de disco
vmstat -d
```

### `iostat` - Estadísticas de E/S
```bash
# Instalar si no está disponible
sudo apt install sysstat

# Estadísticas básicas
iostat

# Actualizar cada 2 segundos
iostat 2

# Mostrar estadísticas extendidas
iostat -x
```

### `sar` - Recopilar estadísticas del sistema
```bash
# CPU usage cada 2 segundos, 5 veces
sar -u 2 5

# Uso de memoria
sar -r 2 5

# Actividad de red
sar -n DEV 2 5

# Carga promedio
sar -q 2 5
```

### `lscpu` - Información de CPU
```bash
# Información completa de CPU
lscpu

# Información básica
cat /proc/cpuinfo
```

### `lspci` y `lsusb` - Hardware
```bash
# Listar dispositivos PCI
lspci

# Información detallada
lspci -v

# Listar dispositivos USB
lsusb

# Información detallada de USB
lsusb -v
```

---

## 📝 Logs del Sistema

### `journalctl` - Logs de SystemD
```bash
# Ver todos los logs
sudo journalctl

# Logs desde el último boot
sudo journalctl -b

# Logs de un servicio específico
sudo journalctl -u nombre_servicio

# Seguir logs en tiempo real
sudo journalctl -f

# Logs de las últimas 24 horas
sudo journalctl --since "24 hours ago"

# Logs entre fechas
sudo journalctl --since "2024-01-01" --until "2024-01-02"

# Logs por prioridad
sudo journalctl -p err

# Limpiar logs antiguos
sudo journalctl --vacuum-time=7d
sudo journalctl --vacuum-size=100M
```

### Archivos de log tradicionales
```bash
# Log del sistema
sudo tail -f /var/log/syslog

# Logs de autenticación
sudo tail -f /var/log/auth.log

# Logs del kernel
sudo tail -f /var/log/kern.log

# Logs de Apache
sudo tail -f /var/log/apache2/access.log
sudo tail -f /var/log/apache2/error.log

# Logs de Nginx
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log
```

### `dmesg` - Mensajes del kernel
```bash
# Mensajes del kernel
dmesg

# Seguir mensajes en tiempo real
dmesg -w

# Limpiar buffer de mensajes
sudo dmesg -c

# Mostrar timestamps legibles
dmesg -T
```

---

## ⏰ Crontab y Tareas Programadas

### `crontab` - Tareas programadas del usuario
```bash
# Editar crontab del usuario actual
crontab -e

# Listar tareas programadas
crontab -l

# Eliminar todas las tareas
crontab -r

# Editar crontab de otro usuario (como root)
sudo crontab -e -u usuario
```

### Formato de crontab
```bash
# Formato: minuto hora día_mes mes día_semana comando
# * * * * * comando_a_ejecutar
# | | | | |
# | | | | +-- Día de la semana (0-7, donde 0 y 7 son domingo)
# | | | +---- Mes (1-12)
# | | +------ Día del mes (1-31)
# | +-------- Hora (0-23)
# +---------- Minuto (0-59)

# Ejemplos:
# Ejecutar cada minuto
* * * * * /ruta/al/script.sh

# Ejecutar a las 2:30 AM todos los días
30 2 * * * /ruta/al/script.sh

# Ejecutar cada lunes a las 9:00 AM
0 9 * * 1 /ruta/al/script.sh

# Ejecutar cada 5 minutos
*/5 * * * * /ruta/al/script.sh

# Ejecutar el primer día de cada mes
0 0 1 * * /ruta/al/script.sh
```

### Tareas del sistema
```bash
# Tareas del sistema en /etc/crontab
sudo nano /etc/crontab

# Directorio para scripts diarios
ls /etc/cron.daily/

# Directorio para scripts semanales
ls /etc/cron.weekly/

# Directorio para scripts mensuales
ls /etc/cron.monthly/
```

### `at` - Ejecutar comandos una sola vez
```bash
# Instalar at si no está disponible
sudo apt install at

# Programar comando para las 3:00 PM
echo "comando" | at 15:00

# Programar para mañana a las 9:00 AM
echo "comando" | at 9:00 tomorrow

# Ver trabajos programados
atq

# Eliminar trabajo programado
atrm numero_trabajo
```

---

## 🗜️ Compresión y Archivos

### `tar` - Archivador
```bash
# Crear archivo tar
tar -cvf archivo.tar directorio/

# Crear archivo tar comprimido con gzip
tar -czf archivo.tar.gz directorio/

# Crear archivo tar comprimido con bzip2
tar -cjf archivo.tar.bz2 directorio/

# Extraer archivo tar
tar -xvf archivo.tar

# Extraer archivo tar.gz
tar -xzf archivo.tar.gz

# Extraer archivo tar.bz2
tar -xjf archivo.tar.bz2

# Listar contenido sin extraer
tar -tzf archivo.tar.gz

# Extraer en directorio específico
tar -xzf archivo.tar.gz -C /ruta/destino/

# Agregar archivos a tar existente
tar -rvf archivo.tar nuevo_archivo.txt
```

### `gzip` y `gunzip` - Compresión gzip
```bash
# Comprimir archivo
gzip archivo.txt

# Descomprimir archivo
gunzip archivo.txt.gz

# Comprimir manteniendo original
gzip -c archivo.txt > archivo.txt.gz

# Ver información sin descomprimir
gzip -l archivo.txt.gz
```

### `zip` y `unzip` - Archivos ZIP
```bash
# Crear archivo ZIP
zip archivo.zip archivo1.txt archivo2.txt

# Crear ZIP de directorio
zip -r directorio.zip directorio/

# Extraer archivo ZIP
unzip archivo.zip

# Extraer en directorio específico
unzip archivo.zip -d /ruta/destino/

# Listar contenido sin extraer
unzip -l archivo.zip

# Probar integridad
unzip -t archivo.zip
```

---

## 🔍 Búsqueda y Filtrado

### `find` - Buscar archivos y directorios
```bash
# Buscar por nombre
find /ruta -name "archivo.txt"

# Buscar ignorando mayúsculas/minúsculas
find /ruta -iname "*.txt"

# Buscar por tipo (f=archivo, d=directorio)
find /ruta -type f -name "*.log"

# Buscar por tamaño
find /ruta -size +100M    # Mayor a 100MB
find /ruta -size -1G      # Menor a 1GB

# Buscar por fecha de modificación
find /ruta -mtime -7      # Modificado en últimos 7 días
find /ruta -mtime +30     # Modificado hace más de 30 días

# Buscar por permisos
find /ruta -perm 644

# Ejecutar comando en archivos encontrados
find /ruta -name "*.tmp" -delete
find /ruta -name "*.txt" -exec chmod 644 {} \;

# Buscar archivos vacíos
find /ruta -empty
```

### `locate` - Buscar archivos por base de datos
```bash
# Actualizar base de datos
sudo updatedb

# Buscar archivo
locate archivo.txt

# Buscar ignorando mayúsculas
locate -i archivo.txt

# Limitar número de resultados
locate -n 10 archivo.txt
```

### `grep` - Buscar texto en archivos
```bash
# Buscar patrón en archivo
grep "patrón" archivo.txt

# Buscar ignorando mayúsculas/minúsculas
grep -i "patrón" archivo.txt

# Buscar en múltiples archivos
grep "patrón" *.txt

# Buscar recursivamente en directorios
grep -r "patrón" /ruta/

# Mostrar número de línea
grep -n "patrón" archivo.txt

# Mostrar líneas antes y después del patrón
grep -A 3 -B 3 "patrón" archivo.txt

# Invertir búsqueda (líneas que NO contienen patrón)
grep -v "patrón" archivo.txt

# Usar expresiones regulares
grep -E "patrón1|patrón2" archivo.txt

# Contar ocurrencias
grep -c "patrón" archivo.txt
```

### `which` y `whereis` - Localizar comandos
```bash
# Encontrar ubicación de comando
which comando

# Información completa del comando
whereis comando

# Ver todos los paths de un comando
which -a comando
```

---

## 📤 Transferencia de Archivos

### `scp` - Copia segura por SSH
```bash
# Copiar archivo local a servidor remoto
scp archivo.txt usuario@servidor:/ruta/destino/

# Copiar desde servidor remoto a local
scp usuario@servidor:/ruta/archivo.txt /local/destino/

# Copiar directorio recursivamente
scp -r directorio/ usuario@servidor:/ruta/destino/

# Especificar puerto SSH
scp -P 2222 archivo.txt usuario@servidor:/destino/

# Preservar permisos y timestamps
scp -p archivo.txt usuario@servidor:/destino/
```

### `rsync` - Sincronización avanzada
```bash
# Sincronización básica
rsync -av origen/ destino/

# Sincronizar con servidor remoto
rsync -av directorio/ usuario@servidor:/ruta/destino/

# Mostrar progreso
rsync -av --progress origen/ destino/

# Eliminar archivos en destino que no existen en origen
rsync -av --delete origen/ destino/

# Excluir archivos/directorios
rsync -av --exclude="*.log" origen/ destino/

# Dry run (simular sin ejecutar)
rsync -av --dry-run origen/ destino/
```

### `sftp` - FTP seguro
```bash
# Conectar a servidor SFTP
sftp usuario@servidor

# Comandos dentro de SFTP:
# ls - listar archivos remotos
# lls - listar archivos locales
# cd - cambiar directorio remoto
# lcd - cambiar directorio local
# get archivo - descargar archivo
# put archivo - subir archivo
# quit - salir
```

---

## 🔒 Seguridad y Firewall

### `ufw` - Firewall simplificado (Ubuntu)
```bash
# Ver estado del firewall
sudo ufw status

# Habilitar firewall
sudo ufw enable

# Deshabilitar firewall
sudo ufw disable

# Permitir puerto específico
sudo ufw allow 22
sudo ufw allow ssh

# Permitir puerto con protocolo específico
sudo ufw allow 80/tcp
sudo ufw allow 53/udp

# Permitir rango de puertos
sudo ufw allow 3000:3010/tcp

# Denegar puerto
sudo ufw deny 23

# Permitir desde IP específica
sudo ufw allow from 192.168.1.100

# Eliminar regla
sudo ufw delete allow 80

# Resetear todas las reglas
sudo ufw --force reset

# Ver reglas numeradas
sudo ufw status numbered
```

### `iptables` - Firewall avanzado
```bash
# Ver reglas actuales
sudo iptables -L

# Ver reglas con números de línea
sudo iptables -L --line-numbers

# Permitir tráfico SSH
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Permitir tráfico HTTP y HTTPS
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Bloquear IP específica
sudo iptables -A INPUT -s 192.168.1.100 -j DROP

# Guardar reglas (Ubuntu/Debian)
sudo iptables-save > /etc/iptables/rules.v4

# Restaurar reglas
sudo iptables-restore < /etc/iptables/rules.v4
```

### `fail2ban` - Protección contra ataques de fuerza bruta
```bash
# Instalar fail2ban
sudo apt install fail2ban

# Ver estado
sudo fail2ban-client status

# Ver servicios protegidos
sudo fail2ban-client status sshd

# Desbanear IP
sudo fail2ban-client set sshd unbanip 192.168.1.100

# Ver IPs baneadas
sudo fail2ban-client get sshd banip
```

### Comandos de seguridad
```bash
# Ver últimos logins
last

# Ver intentos de login fallidos
lastb

# Ver usuarios actualmente conectados
who
w

# Ver información de login del usuario
finger usuario

# Cambiar a modo de emergencia
sudo systemctl rescue

# Ver puertos abiertos
sudo netstat -tulnp
sudo ss -tulnp
```

---

## 🌍 Variables de Entorno

### Gestión de variables de entorno
```bash
# Ver todas las variables de entorno
env
printenv

# Ver variable específica
echo $PATH
echo $HOME
echo $USER

# Establecer variable temporal
export MI_VARIABLE="valor"

# Establecer variable permanente (usuario)
echo 'export MI_VARIABLE="valor"' >> ~/.bashrc
source ~/.bashrc

# Establecer variable del sistema
sudo echo 'MI_VARIABLE="valor"' >> /etc/environment

# Eliminar variable
unset MI_VARIABLE
```

### Variables importantes
```bash
# PATH - Directorios de ejecutables
echo $PATH
export PATH=$PATH:/nuevo/directorio

# HOME - Directorio del usuario
echo $HOME

# USER - Nombre del usuario actual
echo $USER

# SHELL - Shell actual
echo $SHELL

# LANG - Configuración de idioma
echo $LANG

# EDITOR - Editor por defecto
export EDITOR=nano
```

---

## 📝 Comandos de Texto

### `cat` - Mostrar contenido de archivos
```bash
# Mostrar archivo completo
cat archivo.txt

# Mostrar múltiples archivos
cat archivo1.txt archivo2.txt

# Numerar líneas
cat -n archivo.txt

# Mostrar caracteres no imprimibles
cat -A archivo.txt

# Crear archivo simple
cat > nuevo_archivo.txt
# (escribir contenido y Ctrl+D para terminar)
```

### `less` y `more` - Ver archivos página por página
```bash
# Ver archivo con less (recomendado)
less archivo.txt

# Ver archivo con more
more archivo.txt

# Navegación en less:
# Espacio - página siguiente
# b - página anterior
# / - buscar
# n - siguiente coincidencia
# q - salir
```

### `head` y `tail` - Ver inicio y final de archivos
```bash
# Primeras 10 líneas
head archivo.txt

# Primeras N líneas
head -n 20 archivo.txt

# Últimas 10 líneas
tail archivo.txt

# Últimas N líneas
tail -n 20 archivo.txt

# Seguir archivo en tiempo real
tail -f archivo.log

# Seguir múltiples archivos
tail -f archivo1.log archivo2.log
```

### `wc` - Contar líneas, palabras, caracteres
```bash
# Contar líneas, palabras y caracteres
wc archivo.txt

# Solo contar líneas
wc -l archivo.txt

# Solo contar palabras
wc -w archivo.txt

# Solo contar caracteres
wc -c archivo.txt
```

### `sort` - Ordenar contenido
```bash
# Ordenar líneas alfabéticamente
sort archivo.txt

# Ordenar numéricamente
sort -n numeros.txt

# Ordenar en reversa
sort -r archivo.txt

# Ordenar por campo específico
sort -k 2 archivo.txt

# Eliminar duplicados
sort -u archivo.txt
```

### `uniq` - Eliminar líneas duplicadas
```bash
# Eliminar duplicados consecutivos
uniq archivo.txt

# Contar duplicados
uniq -c archivo.txt

# Mostrar solo duplicados
uniq -d archivo.txt

# Mostrar solo líneas únicas
uniq -u archivo.txt
```

### `cut` - Extraer columnas/campos
```bash
# Extraer caracteres 1-5 de cada línea
cut -c 1-5 archivo.txt

# Extraer campo delimitado por espacios
cut -d ' ' -f 2 archivo.txt

# Extraer múltiples campos
cut -d ',' -f 1,3 archivo.csv

# Usar tabulador como delimitador
cut -f 1-3 archivo.tsv
```

### `awk` - Procesamiento de texto avanzado
```bash
# Imprimir segunda columna
awk '{print $2}' archivo.txt

# Imprimir líneas que contienen patrón
awk '/patrón/ {print}' archivo.txt

# Usar delimitador específico
awk -F ',' '{print $1}' archivo.csv

# Operaciones matemáticas
awk '{sum += $1} END {print sum}' numeros.txt

# Condicionales
awk '$3 > 100 {print $1, $3}' archivo.txt
```

### `sed` - Editor de flujo
```bash
# Reemplazar primera ocurrencia por línea
sed 's/viejo/nuevo/' archivo.txt

# Reemplazar todas las ocurrencias
sed 's/viejo/nuevo/g' archivo.txt

# Eliminar líneas que contienen patrón
sed '/patrón/d' archivo.txt

# Mostrar solo líneas específicas
sed -n '5,10p' archivo.txt

# Editar archivo in-place
sed -i 's/viejo/nuevo/g' archivo.txt

# Insertar línea después de patrón
sed '/patrón/a\Nueva línea' archivo.txt
```

---

## 🚀 Scripts y Automatización

### Crear scripts básicos
```bash
#!/bin/bash
# Mi primer script

echo "Hola, mundo!"
echo "Usuario actual: $USER"
echo "Directorio actual: $(pwd)"
echo "Fecha: $(date)"

# Hacer ejecutable
chmod +x mi_script.sh

# Ejecutar
./mi_script.sh
```

### Variables en scripts
```bash
#!/bin/bash

# Variables
NOMBRE="Juan"
EDAD=25

echo "Nombre: $NOMBRE"
echo "Edad: $EDAD"

# Variables de argumentos
echo "Primer argumento: $1"
echo "Segundo argumento: $2"
echo "Todos los argumentos: $@"
echo "Número de argumentos: $#"
```

### Estructuras de control
```bash
#!/bin/bash

# If-else
if [ "$1" = "hola" ]; then
    echo "¡Hola!"
elif [ "$1" = "adios" ]; then
    echo "¡Adiós!"
else
    echo "No entiendo"
fi

# For loop
for i in {1..5}; do
    echo "Número: $i"
done

# While loop
contador=1
while [ $contador -le 5 ]; do
    echo "Contador: $contador"
    ((contador++))
done
```

---

## 📚 Recursos Adicionales

### Documentación y ayuda
```bash
# Manual de comandos
man comando

# Ayuda corta
comando --help

# Información del comando
info comando

# Buscar en manuales
apropos palabra_clave

# Ubicación del manual
whereis -m comando
```

### Atajos de teclado útiles
```bash
# Ctrl+C - Interrumpir proceso actual
# Ctrl+Z - Suspender proceso actual
# Ctrl+D - Cerrar terminal/logout
# Ctrl+L - Limpiar pantalla
# Ctrl+A - Ir al inicio de línea
# Ctrl+E - Ir al final de línea
# Ctrl+U - Borrar desde cursor al inicio
# Ctrl+K - Borrar desde cursor al final
# Ctrl+R - Buscar en historial
# Tab - Autocompletar
# !! - Repetir último comando
# !n - Ejecutar comando número n del historial
```

### Configuración de shell
```bash
# Ver historial de comandos
history

# Limpiar historial
history -c

# Configurar tamaño del historial
echo 'HISTSIZE=1000' >> ~/.bashrc
echo 'HISTFILESIZE=2000' >> ~/.bashrc

# Alias útiles
echo 'alias ll="ls -la"' >> ~/.bashrc
echo 'alias la="ls -A"' >> ~/.bashrc
echo 'alias l="ls -CF"' >> ~/.bashrc

# Recargar configuración
source ~/.bashrc
```

---

## ⚠️ Comandos Peligrosos (Usar con Precaución)

```bash
# ¡CUIDADO! Estos comandos pueden dañar el sistema

# Eliminar todo (NO EJECUTAR)
# rm -rf /

# Sobrescribir disco con ceros
# dd if=/dev/zero of=/dev/sda

# Eliminar archivo de swap mientras está en uso
# swapoff -a && rm /swapfile

# Cambiar permisos de sistema críticos
# chmod 777 /etc/passwd
```

---

## 🔧 Troubleshooting Común

### Problemas de permisos
```bash
# Recuperar permisos estándar
sudo chmod 755 /usr/bin/*
sudo chmod 644 /etc/passwd
sudo chmod 600 /etc/shadow

# Cambiar propietario recursivamente
sudo chown -R usuario:grupo /home/usuario/
```

### Espacio en disco
```bash
# Encontrar archivos grandes
find / -size +100M -type f 2>/dev/null

# Limpiar caché de paquetes
sudo apt clean

# Eliminar paquetes huérfanos
sudo apt autoremove

# Limpiar logs
sudo journalctl --vacuum-time=7d
```

### Problemas de red
```bash
# Reiniciar interfaz de red
sudo ip link set eth0 down
sudo ip link set eth0 up

# Reiniciar NetworkManager
sudo systemctl restart NetworkManager

# Flush DNS
sudo systemd-resolve --flush-caches
```

---

## 📖 Conclusión

Esta guía cubre los comandos y conceptos esenciales para la administración de sistemas Linux en Ubuntu y Debian. Recuerda:

- **Siempre hacer backup** antes de cambios importantes
- **Usar `man comando`** para documentación detallada
- **Practicar en entorno de pruebas** antes de producción
- **Mantener el sistema actualizado**: `sudo apt update && sudo apt upgrade`
- **Monitorear logs** regularmente para detectar problemas

### Para contribuir a este repositorio:
1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -am 'Añadir nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

---

**¡Happy Linux Administration!** 🐧✨
