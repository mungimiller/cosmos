# CREACIÓN DE COSMOS
La idea de crear un proyecto real ya llevaba tiempo rondandome la cabeza. Al observar la oportunidad de realizar un proyecto de final de ASIX, junté diferentes conceptos
y formé la idea de crear una página web de creación de páginas web ( vaya redundancia).

Siempre quise emprender con un proyecto online, y con los conocimientos adquiridos, crear páginas web me pareció una buena opción.
Observé que habia bastante competencia en el mercado, pero busque unos patrones en los que me pudiera distinguir de el resto de empresas.

En primer lugar, observé que todas las paginas ofrecian el servicio, pero ninguna mostraba el coste directo de la creación de dichas páginas. Por tanto, para focalizar l pàgina web en los clientes, descartamos en cierta medida los proyectos en los que segun lo que te demanden los costes de este varian mucho y valoré la manera de realizar un precio "Standard" con una serie de parametros de configuración y implementanción de dichas paginas web.

En segundo lugar, observé que las paginas no cuentan con un servicio de Soporte o la mayoria no cuentan con el. De aquí, nace la idea de realizar un bot de soporte que 
guie al usuario sobre los servicios de la pàgina web y te describa los diferentes conceptos informaticos que engloban la creación de una pàgina web.

En tercer lugar, al contar con un primer servicio de atención al cliente con el Bot, pensé en crear un mantenimiento mensual de tus pàginas web explicando detalladamente
el tipo de trabajo que se realiza y dejando en claro al cliente que no deberá gestionar ninguna de sus páginas web ya que paga una cuota mensual.

En cuarto lugar y por último, la idea de implementar un pequeño curso de aprendizaje tanto en creación de pàginas web como en gestión de la misma a nivel de servicio de 
Hosting. En un futuro, la idea también es integrar un curso de quota mensual, en la que además de realizar el curso puedas obtener mentoria por parte de un tutor que te 
va guiando en tu proceso de aprendizaje.

Una vez expuestos estos puntos, creo que quedan argumentados los motivos por los que he realizado este proyecto y en que puntos me he fijado para fortalecer las debilidades

## ÍNDICE
- Instalación servicios Cloud
- Configuración 
-
-

## 1. CREACIÓN Y INSTALACIÓN DE LOS SERVICIOS EN EL CLOUD
En primer lugar hemos procedido a contratar el cloud a una empresa externa, en este caso se trata de SW Hosting. Actualmente trabajo allí, ese fue el motivo principal
que me impulsó a tomar servicios con ellos.
El cloud por el que me decidí se trata de un Debian Buster v.10, en el cual he instalado los siguientes servicios que son imprescindibles para el correcto funcionamiento del servicio de Hosting Web.

Los pasos de la instalación de los diferentes servicios son:

▶️ _Previamente siempre debemos realizar_ `sudo apt-get update` y `sudo apt-get upgrade` !

### INSTALACIÓN DNS BIND
En primer lugar instalaremos BIND9, permite a nuestro servidor gestionar los diferentes registros DNS, para que estos resuelvan correctamente y muestren la información de la dirección IP a la que apuntan.

- Instalarlo con la siguiente comanda:
```sh
sudo apt install -y bind9
```
- Una vez instalado el servicio siempre hay que comprobar que este se encuentre activo
```sh
sudo systemctl status bind9
```
- A continuación, crear la carpeta donde se encontrará la configuración DNS del dominio cosmosdesing.es, para ello tenemos que acceder al siguiente path `/etc/bind/` que es donde se encuentra toda la configuración de este servicio. 
```sh
mkdir /etc/bind/dbs
```

- Hemos creado la carpeta ya que puede que en un futuro existan mas hostings en el servidor y por tanto diversas configuraciones. Debemos entrar a la carpeta y  vamos a crear un archivo con el nombre del dominio en cuestión y configurar los registros DNS que deben resolver para ese dominio.
![image](https://user-images.githubusercontent.com/73543470/166708050-8d4ded14-6bcd-42ca-ac76-449326423476.png)

A continuación voy a explicar los parametros que aparecen en la siguiente imagen para poder entender mejor la configuración realizada


### INSTALACIÓN APACHE2
La función principal de apache es brindar a los usuarios todos los ficheros necesarios para la correcta visualización de la página web.
- Instalamos realizando la comanda
```sh
sudo apt install apache2
```
- Comprobamos que este se encuentre activo
```sh
systemctl status apache2
```
- Una vez instalado debemos proceder a configurar el VirtualHost del servicio web. En debian ya se encuentra un directorio previamente definido para realizar la creación de directorios relacionado con las webs. Por tanto procederemos a crear el directorio  `/var/www/cosmosdesign.es` con el nombre de nuestro dominio.
```sh
mkdir -p /var/wwww/cosmosdesign.es/datos/web/
```

### PHP
Debemos instalar el lenguaje PHP en nuestro Cloud ya que es esencial para crear sitios web y configurar el backend.
#### INSTALACIÓN PHP
 - Debemos descargar los repositorios PPA de SURY
 ```ls
sudo apt -y install lsb-release apt-transport-https ca-certificates 
sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
 ```
 - Seguidamente tenemos que agregar los repositorios descargados anteriormente al archivo `source.list`
 ```sh
 echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/php.list
 ```
 - Procedemos a actualizar la lista de paquetes para que detecte el nuevo introducido
 ```sh
 sudo apt-get update
 ```
 - Efectuamos la comanda de instalación
 ```
 sudo apt -y install php7.4
 ```
 - Como vamos a utilizar php como módulo de Apache activamos la versión con la que vamos a trabajar en nuestro Hosting y desactivamos la predefinida
 ```sh
sudo a2dismod php7.3
sudo a2enmod php7.4
 ```
 

 
### INSTALACIÓN MARIA DB



### INSTALACIÓN NGINX
Cuando alguien hace una solicitud para abrir una página web, el navegador se comunica con el servidor de ese sitio web. Luego, el servidor busca los archivos solicitados para la página y se los envía al navegador.
Funcina como servidor proxy de correo electrónico SMPT, POP3, IMAP.

### INSTALACIÓN POSTFIX


## 2. CREACIÓN Y CONFIGURACIÓN DEL SERVICIO DE HOSTING
Una vez configurado el Cloud al completo podemos proceder a la creación del servicio de Hosting.
Antes de proceder a realizar la instalación del servicio, he comprado el dominio de la página web cosmodesigns.es, mediante la opción que proporciona el SW Panel.
Una vez este dominio es comprado los registros DNS no apuntan a ningún servicio de Hosting. Por tanto, procederemos a asignar los DNS que le pertocan al dominio 
utilzando la herramienta del SWPanel. Los DNS deben ser el nombre del cloud y uno de los servidores con los que SWHosting trabaja. 
En este caso `ce202224546545.dnssw.net` y `dns4.swhosting.com`

Modificar estos DNS hará que nuestro dominio apunte al servicio de Hosting creado anteriormente, y así pueda cargar el contenido de la pàgina web. La propagación de 
los DNS a través de la red lleva un tiempo hasta que se registra alrededor del mundo.
En este caso al tratarse de un dominio .es la propagación és más lenta ya que la aprobación y propagación del domino la lleva a cabo el Gobierno Español.

Cuando los DNS del dominio ya coinciden con los del Hosting y además estos se encuentran propagados a través de internet. Procederemos a la creación y instalación 
de un certificado SSL. Utilizaremos un certificado llamado Lets Encryps, este es gratuito y lo que nos proporciona es que no salte ese aviso de que la página no es segura al entrar en ella, además del candado en el lado superior izquierdo del navegador. Estos mensajes no se muestran porque la web se encuentra encryptada y por tanto es más segura.



## 3. CONFIGURACIÓN DE WORDPRESS
Como los DNS todavia no se encuentran propagados he modificado mi archivo de host en Winodws para que mi PC apunte al dominio en cuestión con la IP asignada. Para así poder iniciar sesión en Wordpress y poder comenzar a adminstrarlo.
- Para modificar el archivo de host de nuestro Windows debemos abrir un **Bloc de Notas ejecutado como administrador**.

- Debemos a acceder a archivos e ir al siguiente path `C:\Windows\System32\drivers\etc\hosts`
![image](https://user-images.githubusercontent.com/73543470/166690231-7ee73ff2-cfd1-44e2-a867-576e8508df43.png)

- Seguidamente tenemos que modificar el archivo añadiendo en la parte final de este el nombre del dominio i la IP asignada.
![image](https://user-images.githubusercontent.com/73543470/166690357-da34c6d3-c106-4735-a6c2-567d0d198303.png)

- Para acceder a wordpress tenemos que introducir la siguiente URL `http://cosmosdesign.es/wp-admin/` donde nos llevará a iniciar sesión que dará a la siguiente ventana
![image](https://user-images.githubusercontent.com/73543470/166509748-f8182557-7336-4fbb-b21e-98d8467e90e0.png)

- Una vez llegados a este punto procederemos a utilizar uno de los Temas predefinidos de los que consta Wordpress. Para ello debemos acceder Apariencias > Temas. En este punto tras una larga busqueda, me decidí por el siguiente:
![image](https://user-images.githubusercontent.com/73543470/166525726-202a64c7-8ebc-4232-a60e-1a01050b5f42.png)

En este apartado mostraré mediante un breve resumen todas las modificaciones que he realizado en el tema elegido. Dividiendolo por las diferentes páginas realizadas en el Wordpress.

- **Homepage** --> En este apartado, me interesaba que se viera con claridad los 3 conceptos básicos que engloban mi proyecto. A primera vista queria que supeiras que la pagina web trata de creación de pàginas web, también me interesaba que se vieran los 3 precios de los 3 formatos de páginas web a realizar y finalmente que entiendan que es un servicio que ofrece soporte y que este sea visible para que lo utilicen.

- **Descripciones de productos** --> Un total de 3 páginas individuales donde se explica las características del producto, porque tiene ese precio, que servicios se ofrecen en el y el estilo de página web que se puede llegar a realizar con el plan seleccionado.

- **Formulario de propuesta** --> Formulario donde debes especificar exactamente lo que deseas realizar en tu página web, el concepto de la empresa, los colores que pueden llegar a definir la entidad, cantidad de hojas aproximadas(como lo que estoy realizando yo en este apartado), aportar una cantidad de seleccionables que sean extras que tengan un coste extra en el proyecto. Además de dejar en claro al cliente que puede mantener-se en contacto con nosotros para hacer una evaluación continua de la página.

- **Muro de mejoras** --> Muro donde el cliente puede ir dejando notas referente a los cambios que estan sucediendo en su página web junto con posibles mejoras.


## 4. INSTALACIÓN DE PLUGINS

Una vez creado el Wordpress, voy a realizar una lista con los plugins que tengo instalados y la funcinonalidad de cada uno.

- **YOAST SEO -->** Básicamente es una ayuda extra al crear la página para que esta quede más optimizada y tu web obtenga más entradas para los motores de búsquedas.
- **LITTLE SPEED CACHÉ -->** Configuración de la caché, servicios CDN, optimización de imagenes y páginas.


**Información extra:** _Un CDN a grandes rasgos es un servidor donde se almacenan las imágenes, videos, etc. de tu página web. Basicamente almacena todos los archivos de gran peso, excepto el codigo de la página. Esta información se replican en diferentes nodos de manera que cuando algun usuario accede a la web, detectan que nodo de CDN se encuentra más cerca del punto de carga(PC USUARIO) y procede a cargar las imagenes de dicho nodo, mientras que el codigo lo carga desde el servidor donde se encuentra el hosting._

## 5. INSTALACIÓN WOOCOMMERCE

Es necesaria la instalación de dicha aplicación para poder realizar pagos online

## 6. CREACIÓN DE BOT DE SOPORTE

## 7. ANALSIS EMPRESARIAL DEL PROYECTO.




