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


# 2 Instalacion de la version 7.4 de Php a UBuntu

# Instal·lació i configuració d'aplicacions web

Per instal·lar una aplicació web hem de baixar el seu codi font i portar-lo al directori arrel del nostre servidor d'aplicacions, en el nostre cas, `apache2`. Quan instal·lem `apache2` es crea una carpeta a `/var/www/html` on, per defecte, el servidor web utilitza com a directori arrel.

Llavors, si portem la nostra aplicació al directori `/var/www/html` tindrem accés a la nostra aplicació mitjaçant l'adreça `http://localhost`.

## Instal·lació d'apache2, mysql i algunes llibreries al contenidor

1. Actualització de la màquina.
```console
sudo apt update
```
```console
sudo apt upgrade
```

2. Instal·lació del servidor web `apache2`.
```console
sudo apt install -y apache2
```

3. Instal·lació del servidor de bases de dades `mysql-server`.
```console
sudo apt install -y mysql-server
```

4. Instal·lació d'algunes llibreries de `php`, el llenguatge principal que utilitzen les aplicacions.
```console
sudo apt install -y php libapache2-mod-php
```
```console
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
```

5. Reiniciem el servidor apache2
```console
sudo systemctl restart apache2
```

## Configuració de MySQL
### Accedim a la consola de MySQL
Des d'un terminal on siguem `root` hem d'executar la següent comanda:
```console
sudo mysql
```

### Creació de la base de dades:
Un cop dins la consola de MySQL executem les comandes per a crear la base de dades. En aquest cas estem creant una base de dades amb el nom `bbdd`.

```console
CREATE DATABASE bbdd;
```

### Creació d'un usuari
Tingueu en compte que s'haurà d'identificar la IP des de la qual s'accedirà a la base de dades, en aquest cas, `localhost`.

```console
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

### Donem privilegis a l'usuari:
```console
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
```

### Sortim de la base de dades
```console
exit
```

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
