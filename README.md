# Owncloud
# 1 
Para llegar a este paso, lo primero que hay que hacer es crearse un nuevo escritorio.

![image](https://github.com/user-attachments/assets/05087909-bcf6-4dcb-a652-d59c6b1bb12f)

Primero ponemos el nombre de nuestro escritorio

![image](https://github.com/user-attachments/assets/af4f89ef-37ec-48d3-8b32-b904ddedb8c7)

Luego seleccionamos nuestra plantilla

![image](https://github.com/user-attachments/assets/92d5d67f-9bc1-4961-b1e7-6c7852ac8ed4)

Despues le damos a crea

![image](https://github.com/user-attachments/assets/d66ac1cc-f6d8-456a-90bd-653768096c8f)

Una vez lo hemos creado, podemos ver que opciones tenemos para abrir nuestro escritorio

![image](https://github.com/user-attachments/assets/957b9100-000a-4c59-a8fe-40e0cbaf2768)

![image](https://github.com/user-attachments/assets/afbbfa89-d579-4fb6-ad42-cd95db73501d)

# 2 
# Instalacion de OwnCloud

1. Instalación de dependencias y repositorio PPA
```console
sudo apt install software-properties-common -y
```
```console
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
```
```console
sudo apt update
```

2. Instalación de PHP 7.4 y extensiones necesarias

```console
sudo apt install php7.4 -y
```
```console
sudo apt install -y php libapache2-mod-php7.4
```
```console
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
```

3. Selección de la versión de PHP
```console
sudo update-alternatives --config php
```

4. Activación de módulos necesarios de Apache2

```console
sudo a2enmod proxy_fcgi setenvif
```
```console
sudo a2enconf php7.4-fpm
```

5. Reinicio del servidor Apache2
```console
sudo service apache2 restart
```

# Instalación y configuración de Apache2, MySQL y librerías PHP


![Captura de pantalla de 2025-05-13 12-55-50](https://github.com/user-attachments/assets/ab5e09f0-25f9-4d6e-b60a-43bdd3fd74ba)

![Captura de pantalla de 2025-05-13 12-56-17](https://github.com/user-attachments/assets/92044c28-a98f-4c27-bf17-22bfb20dcad8)

![Captura de pantalla de 2025-05-13 12-57-03](https://github.com/user-attachments/assets/c8b7b015-da48-4b55-a6ee-67f7f059c1f4)

![Captura de pantalla de 2025-05-13 12-58-19](https://github.com/user-attachments/assets/f1a273e1-dc27-43ef-ab82-73d1c9f4b432)

![Captura de pantalla de 2025-05-13 12-59-12](https://github.com/user-attachments/assets/9ccaaf1c-f118-4bca-93e7-8fb9f4103a8b)

![Captura de pantalla de 2025-05-13 12-59-21](https://github.com/user-attachments/assets/eb27172c-e544-4888-98df-ea33644491b8)

![Captura de pantalla de 2025-05-13 12-59-57](https://github.com/user-attachments/assets/ebe218f3-c94e-436c-9a42-0750d02187b6)

![Captura de pantalla de 2025-05-13 12-45-13](https://github.com/user-attachments/assets/a07e25f8-9765-4889-9f59-bdbd680d5f37)

![Captura de pantalla de 2025-05-13 12-48-01](https://github.com/user-attachments/assets/9156daab-1f18-434a-b631-702c9dac05a9)

![Captura de pantalla de 2025-05-13 12-55-09](https://github.com/user-attachments/assets/757bae6b-17a6-4df1-8287-8eafc256ace9)

![Captura de pantalla de 2025-05-13 12-55-37](https://github.com/user-attachments/assets/1519013a-8593-4b0b-b52a-61d6488e817b)


# 3 Guía Instalación de apache2, mysql y algunas librerías en el contenidor
## 

1. Actualización de la máquina.
```console
sudo apt update
```
```console
sudo apt upgrade
```

2. Instalación del servidor web `apache2`.
```console
sudo apt install -y apache2
```

3. Instalación del servidor de bases de datos `mysql-server`.
```console
sudo apt install -y mysql-server
```

4. Instalación de algunas librerías de `php`, el lenguaje principal que utilizan las aplicaciones.
```console
sudo apt install -y php libapache2-mod-php
```
```console
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
```

5. Reiniciamos el servidor apache2
```console
sudo systemctl restart apache2
```

## Configuración de MySQL
### Accedim a la consola de MySQL
Des d'un terminal on siguem `root` hem d'executar la següent comanda:
```console
sudo mysql
```

### Creación de la base de datos:
Un cop dins la consola de MySQL executem les comandes per a crear la base de dades. En aquest cas estem creant una base de dades amb el nom `bbdd`.

```console
CREATE DATABASE bbdd;
```

### Creación de un usuario
Tingueu en compte que s'haurà d'identificar la IP des de la qual s'accedirà a la base de dades, en aquest cas, `localhost`.

```console
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

### Damos privilegios al usuario:
```console
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
```

### Salimos de la base de datos
```console
exit
```
## Descargamos los archivos de la aplicación web
Vamos al directorio `/var/www/html` y descomprimimos allí los archivos de la aplicación web, debe sustituir `app-web.zip` por el nombre de su archivo que ha descargado con la aplicación web y el nombre de la carpeta `app-web` por la carpeta que le ha creado, si su instalación en linux está en un idioma modifique el pedido para adaptarlo a sus necesidades.

```console
sudo cp ~/Baixades/app-web.zip /var/www/html
```
Vaya al directorio `/var/www/html`
```console
cd /var/www/html
```
Descomprimir el archivo que ha descargado
```console
sudo unzip app-web.zip
```
Copie los archivos en la carpeta `/var/www/html`, modifique `app-web` por el nombre del directorio donde se ha descomprimido su archivo.
```console
sudo cp -R app-web/. /var/www/html
```
Eliminamos la carpeta creada cuando hemos hecho l'`unzip`
```console
sudo rm -rf app-web/
```

## Eliminamos el archivo `index.html` del `apache2`
```console
sudo rm -rf /var/www/html/index.html
```

## Aplicación de permisos en nuestras aplicaciones web
Un cop descomprimits els fitxers de l'aplicació web al directori `/var/www/html`, apliquem els següents permisos al directori `/var/www/html`

```console
cd /var/www/html
```
```console
sudo chmod -R 775 .
```
```console
sudo chown -R usuario:www-data .
```
## Accedemos al navegador para ver que todo funciona
Poseu la direcció http://localhost al navegador web i configureu la cloud.

Si todo ha ido bien y ha seguido el manual le aparecerá el instalador de la aplicación web que ha descargado y le pedirá crear un usuario admin y la información de la base de datos.

La información que debe poner (si no ha modificado la información del manual) es la siguiente:

* **usuari:** usuario
* **contrasenya:** password
* **base de dades:** bbdd
* **domini:** localhost

# 4 Realizar pruebas básicas para verificar el correcto funcionamiento de ownCloud:


![image](https://github.com/user-attachments/assets/0a843c44-e8aa-46e6-9f92-f03f5bdb3540)

![image](https://github.com/user-attachments/assets/99369a70-0fc4-4f29-b90f-cb6fa0070be1)

![image](https://github.com/user-attachments/assets/05dacb7c-da93-4cab-ab7f-ca8c3ddffa73)

![image](https://github.com/user-attachments/assets/48ee5244-56fb-48d5-bbf7-da08f53e68a4)


