# InstalarServidorDebian12
Pasos a seguir para instalar servidor debian para API Factronica

´´´´
######################################################
# SCRIPT PARA INSTALACION DE SERVIDOR API FACTRONICA
# SISTEMA OPERATIVO: DEBIAN 12 VERSION 2024
######################################################
#
# ACTUALIZAR EL SISTEMA
apt upgrade
apt update
#
# INSTALAR SERVIDOR HTTP
apt install apache2 -y
apt install apache2-utils -y
#
# INSTALAR PHP
apt install php libapache2-mod-php php-cli php-fpm php-json php-pdo php-mysql php-zip php-gd  php-mbstring php-curl php-xml php-pear php-bcmath
#
# INICIAR EL SERVICIO HTTP
/etc/init.d/apache2 start
#
# INSTALAR SERVIDOR MYSQL
apt install mariadb-server -y
#
# INSTALAR PHPMYADMIN
apt install phpmyadmin -y
#
# APLICAR REGLAS DE SEGURIDAD A LA BASE DE DATOS
# REFERENCIAS: https://linuxgenie.net/how-to-install-mariadb-on-debian-12-bookworm-distribution/
mariadb-secure-installation
#
# ENTRAR A LA BASE DE DATOS POR CONSOLA
mariadb -u root -p
#
# CREAR USUARIO ADMIN
CREATE USER 'admin'@'localhost' IDENTIFIED BY 'Softmadplus2020';
#
# ASIGNAR TODOS LOS PRIVILEGIOS AL ADMIN
GRANT ALL PRIVILEGES ON *.* to 'admin'@'localhost';
#
# ACTUALIZAR PRIVILEGIOS
FLUSH PRIVILEGES;
#
# SALIR DE LA BASE DE DATOS POR CONSOLA
quit;
#
# INSTALAR OPENSSH SERVER
apt install openssh-server -y
#
# INSTALAR CURL Y UTILERIA
apt-get install curl -y
apt-get install libcurl  -y
apt-get install libcurl-dev  -y
apt install libcurl4-openssl-dev -y
apt install libcurl4-nss-dev -y
apt install libcurl4-gnutls-dev -y
#
# INSTALAR FIRMA DE XML
apt install xmlsec1 -y
#
# INSTALAR CLIENTE IMAP
apt install php-imap -y
#
# INSTALAR SERVIDOR FTP
apt install vsftpd -y
#
# EDITAR LA CONF DE SERVIDOR FTP
nano /etc/vsftpd.conf
#
# ESTOS 2 VALORES SE DEBE DESCOMENTAR QUITANDO EL # DEL INICIO
write_enable=YES
local_umask=022
#
# REINICIAR SERVICIO FTP
/etc/init.d/vsftpd restart
#
# CREAR USUARIO
useradd softmad
#
# CAMBIAR LA CLAVE AL USUARIO CREADO
passwd softmad
#
# CREAR CARPETA DEL USUARIO
mkdir /var/www/html/softmad
#
# CREAR CARPETA PUBLICA DEL USUARIO
mkdir /var/www/html/softmad/public_html
#
# ASIGNAR PROPIETARIO DE LA CARPETA NUEVA
chown -R softmad softmad
#
#
´´´´
