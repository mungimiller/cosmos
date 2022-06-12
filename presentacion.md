# CREACIÓN DE COSMOS
La idea de crear un proyecto real ya llevaba tiempo rondándome la cabeza. Al observar la oportunidad de realizar un proyecto de final de ASIX, junté diferentes conceptos y formé la idea de crear una página web de creación de páginas web ( vaya redundancia).

Siempre quise emprender con un proyecto online, y con los conocimientos adquiridos, crear páginas web me pareció una buena opción. Observé que había bastante competencia en el mercado, pero busque unos patrones en los que me pudiera distinguir del resto de empresas.

En primer lugar, observé que todas las páginas ofrecían el servicio, pero ninguna mostraba el coste directo de la creación de dichas páginas. Por tanto, para focalizar la página web en los clientes, descartamos en cierta medida los proyectos en los que según lo que te demanden, los costes de este varían mucho y valoré la manera de realizar un precio "Standard" con una serie de parámetros de configuración e implementación de dichas páginas web.

En segundo lugar, observé que las páginas no cuentan con un servicio de Soporte o la mayoría no cuentan con el. De aquí, nace la idea de realizar un bot de soporte que guie al usuario sobre los servicios de la página web y te describa los diferentes conceptos informáticos que engloban la creación de una página web.

En tercer lugar, al contar con un primer servicio de atención al cliente con el Bot, pensé en crear un mantenimiento mensual de tus páginas web, explicando detalladamente el tipo de trabajo que se realiza y dejando en claro al cliente que no deberá gestionar ninguna de sus páginas web, ya que paga una cuota mensual.

En cuarto lugar, y por último, la idea de implementar un pequeño curso de aprendizaje tanto en creación de páginas web como en gestión de la misma a nivel de servicio de Hosting. En un futuro, la idea también es integrar un curso de cuota mensual, en la que además de realizar el curso puedas obtener mentoría por parte de un tutor que te va guiando en tu proceso de aprendizaje.

Una vez expuestos estos puntos, creo que quedan argumentados los motivos por los que he realizado este proyecto y en que puntos me he fijado para fortalecer las debilidades

## ÍNDICE
- Compra del dominio/cloud 
- Configuración BIND9 - DNS
- Configuración LAMP
- Instalación Certificado SSL
- Configuración NGINX
- Configuración POSTFIX + DOVECOT
- Instalación de WORDRPRESS
- Configuración SPAMASSASIN
- Configuración FAIL2BAN
- SCRIPTS
- COMO SER AUTÓNOMO
- BALANCE EMPRESARIAL
- CONCLUSIÓN

## QUE ES HELPDESK
En este caso he realizado la compra del dominio y del hosting/cloud con la empresa de SW Hosting, ya que trabajo allí y es más cómodo para mí monitorizar/configurar mi servidor, porque funciona bajo la infraestructura de SW

El hecho de que conozca en cierta medida la infraestructura informática de la empresa se debe a que ocupo la categoría **Help Desk**. Esta posición es en la que probablemente empezarás en el caso de trabajar en el área de Hosting+Cloud ( con la finalidad de ser Administrador de Sistemas, en este caso lo más probable que sean de SO Linux en su gran mayoría ).

Al trabajar en el área **Help Desk**, perteneces al departamento de Soporte de la empresa. Por tanto, aprendes como funciona la infraestructura de dicha empresa, los diferentes programas que utilizan para dar mantenimiento a los servidores que funcionan 24hs al día. Además, estas empresas suelen tener un cliente visual con el que el cliente puede administrarse el servidor de una manera más gráfica, en este caso seria SWPanel, pero encontrarías otras muchas posibilidades como cPanel, Plesk entre otros.

Por tanto, tu función es responder a las dudas de los clientes, ya sea referente a la configuración del servidor mediante algún cliente de los anteriormente mencionados o errores o incidencias que estén teniendo los clientes con su propio servidor. Cabe recordar, que cuando tú contratas un servidor, a no ser que contrates un servicio de monitorización activo mensual, este es privado, y la empresa en cuestión no puede acceder a tu servidor para observar los logs por ejemplo. Normalmente, este apartado se suele llamar **"Muro de soporte"**, serían las incidencias de menor nivel.

Después encontraríamos los **Tickets Técnicos**, donde entrarían las consultas/acciones/problemas sobre el servidor de un cliente que, por ejemplo, paga la mensualidad de monitorización. En este caso, según la dificultad de la propuesta, tu función como HelpDesk es seguir el protocolo de la empresa, revisar el estado del cloud, observar si puedes realizar una acción en el servidor o solucionar un error de este. En el caso de no saber, siempre puedes preguntar a tus compañeros, ellos siempre saben más que tú cuando acabas de empezar. En el caso de ser una acción difícil o un error que no podéis solucionar, lo reportas con acciones que ya hayas realizado para que el Administrador de Sistemas que lea tu reporte no tenga que realizar la tarea dos veces. En el caso de poder solucionar el ticket llevarás a cabo las acciones que creas necesarias. Normalmente suelen pedirte Deploys, cambios de cabeceras, cambiar parámetros PHP de Apache, cambiar permisos de directorios y ficheros...

Otra de las funciones que realizaras es supervisar el estado de los servidores con un programa de monitorización de equipos y servicios de la red. En mi caso es **NAGIOS**. En este, te irán apareciendo diferentes alertas como _Warning y Critical_ definiendo el problema, ya sea a nivel de Hardware por ejemplo por sobreúso de los vCores, como por ejemplo un problema MAILQ o un RevisarHack por exceso de conexiones al servidor por segundo.

## COMPRA DEL DOMINIO

Antes de proceder a realizar la instalación del servicio, he comprado el dominio de la página web cosmodesigns.es, mediante la opción que proporciona el SW Panel de la siguiente manera:
- Accedemos a Dashboard de SWPanel > Dominios i SSL > Cartera de Dominios

![image](https://user-images.githubusercontent.com/73543470/167443139-16b352ae-dca6-48bd-8c3d-0f3bcb9696fc.png)

- Verificamos si este se encuentra disponible. Siempre podemos utilizar herramientas como www.who.is para verificar el estado del dominio que nos interese.

![image](https://user-images.githubusercontent.com/73543470/167444036-c95f308f-6dc3-4d58-81fd-1131c1dcf1da.png)

- Este se nos añadirá al carrito superior, donde si accedemos debemos declarar que somos el propietario del dominio vinculando nuestro DNI, para confirmar que somos una persona real.

![image](https://user-images.githubusercontent.com/73543470/167445056-5d0c5b84-158b-4f62-9522-e31533d2fc1f.png)

- Después ya tendríamos nuestro dominio comprado y guardado en nuestra billetera de dominios.

![image](https://user-images.githubusercontent.com/73543470/167445176-bf809858-4cac-47dc-b1a5-5b1ba2df9c20.png)

Una vez este dominio es comprado, los registros DNS no apuntan a ningún servicio de Hosting. Por tanto, procederemos a asignar los DNS que le pertenecen al dominio utilizando la herramienta del SWPanel. Los DNS deben ser el nombre del cloud y uno de los servidores con los que SWHosting trabaja.

## COMPRA DEL CLOUD
Ahora que ya tenemos en nuestra posesión el dominio, observaremos que estamos en el servidor whois de dominios declarados en internet, resolviendo con el día de contratación y la empresa que registró el dominio que en este caso fue SWHosting.

Ahora tenemos que crear nuestro cloud, para ello iremos a la parte superior derecha del Panel y seleccionaremos Crear nuevo servicio.
- Seleccionaremos Cloud
- Cloud One
- Debian v.10

Una vez aceptemos la compra se nos enviará al correo electrónico las credenciales de usuario y contraseña de acceso SSH al Cloud. Y listo ya podríamos acceder a él.

## CREACIÓN Y INSTALACIÓN DE LOS SERVICIOS EN EL CLOUD
He instalado los siguientes servicios que son imprescindibles para el correcto funcionamiento del servicio de Hosting Web.

Los pasos de la instalación de los diferentes servicios son:

▶️ _Previamente siempre debemos realizar_ `sudo apt-get update` y `sudo apt-get upgrade` !

## 1. INSTALACIÓN/CONFIGURACIÓN DNS BIND
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
- Hemos creado la carpeta, ya que puede que en un futuro existan más hostings en el servidor y, por tanto, diversas configuraciones DNS. Debemos entrar a la carpeta y vamos a crear un archivo con el nombre del dominio en cuestión y configurar los registros DNS que deben resolver para ese dominio.

![image](https://user-images.githubusercontent.com/73543470/166709151-e4f824f7-eda7-43ed-8651-08c934f4a5e4.png)


### CONFIGURACIÓN DNS DEL CLOUD
A continuación voy a explicar los parámetros que aparecen en la siguiente imagen para poder entender mejor la configuración realizada

  ![image](https://user-images.githubusercontent.com/73543470/166709653-f70ba7aa-477b-4b2f-91f2-bd14b8535b50.png)

En este apartado debemos indicar le nombre del servidor, en mi caso tiene este nombre, ya que al generar el cloud con SW Hosting, le asigna un nombre con la fecha de creación del cloud.

####  REGISTRO MX

  ![image](https://user-images.githubusercontent.com/73543470/166711011-7b944677-b39a-4873-981a-be6b448c5073.png)

Con la siguiente línea indicamos que el servidor de correo es el mismo en el que nos encontramos ahora mismo.

####  REGISTRO DNS

![image](https://user-images.githubusercontent.com/73543470/166711274-b4d0ae55-80b9-4836-8247-f0f3e79aacc2.png)

En la siguiente línea encontramos los registros DNS que utiliza nuestro Cloud para resolver en internet, en este caso tenemos dos, el principal que vendría a ser el nombre del cloud nuevamente y el secundario que es un servidor DNS con el que trabaja SWHosting.

####  REGISTRO A

![image](https://user-images.githubusercontent.com/73543470/166712006-6f4ff46e-f30a-4d64-ba8c-d72f9ea4e31e.png)

Aquí nos encontramos el registro A, el cual hace referencia a la página web. Cuando escribimos cosmosdesign.es, realmente estamos haciendo referencia a la IP descrita en este apartado.

#### REGISTRO CNAME

![image](https://user-images.githubusercontent.com/73543470/166711970-6c14c516-534e-430f-911d-e03a3904b3b1.png)

Observamos que estos dos parámetros hacen referencia a los registros CNAME que son alias del dominio, su función son parecidas a la de un subdominio. En este caso hemos indicado que si escriben el dominio con www también resuelva y muestre nuestra página. También hemos indicado que si escriben mail.nombredelcloud.es este resuelva con el nombre del servidor, el cual te redireccionará al webmail.

#### REGISTRO TXT - SPF1

![image](https://user-images.githubusercontent.com/73543470/166950612-5bd81bd9-5e39-41e0-a8b9-55e09c9335f6.png)

La función de SPF es determinar que servidores de correo y dominios tiene permitido enviar correo en nombre de tu dominio. También indica a los servidores que reciben tu correo que hacer con los mensajes una vez comprobados, confirman que los mensajes parecen proceder de tu servidor autorizado.

En este caso hemos declarado mediante 'MX' autorice a un servidor de correo mediante el registro MX del dominio. ( En este caso es el nombre del cloud y al no indicar el MX, automáticamente tomará el registro MX creado en este mismo archivo)

Mediante `a` autorizamos al servidor de correo por la IP del servidor de correo.

Finalmente, con `~all` los servidores que reciben correo suelen aceptar los mensajes de remitentes que no figuran en el registro SPF, pero los marca como sospechosos.
#### REGISTRO TXT - DMARC1

![image](https://user-images.githubusercontent.com/73543470/166985751-da33ba48-b209-4e73-8b40-3b8e33cbad47.png)

En este caso configuraremos el servicio dmarc1, ayuda a los destinatarios a determinar si un mensaje coincide con lo que sabe sobre un remitente. Por tanto, si el mensaje no coincide, el servidor receptor puede verificar el registro DMARC para orientarte sobre como manejar el mensaje no alineado.
  
En este caso, la `-p` indica que no se lleve a cabo ninguna acción contra el correo no autenticado, pero que envíe en su lugar informes de correo electrónico a la dirección mailto inscrita en el registro DMARC
  
 ####  REGISTRO SRV
 
![image](https://user-images.githubusercontent.com/73543470/166985839-0d7df034-44e8-487f-972e-1d46a50559ad.png)
  
  El registro SRV permite que los servicios se ejecuten fácilmente en puertos no standard y reducir la carga.
  
  El parametro `autodiscover`, como bien dice, descubre automáticamente el nombre simbólico del servicio. Con `_tcp` indicamos el protocolo de transporte del servicio. 
  
  El valor `SRV` indica la clase de registro DNS que és. `443` indica el puerto en el que se encuentra el servicio. Finalmente `ce202205..dnssw.net` indica el nombre del host que  proporciona el servicio.

#### REGISTRO TXT - DKIM1

![image](https://user-images.githubusercontent.com/73543470/166952004-258b38fd-9343-4e68-9d4f-8f68f574fb4b.png)

En este apartado hemos configurado registro DKIM, que es un método de autentificación de correo electrónico que evita que spammers entre otros elementos maliciosos, se hagan pasar por un dominio.

Este se divide en dos partes, la que se almacena en los registros del DNS para el dominio y en las cabeceras que se adjunta a todos los correos electrónicos de un dominio.
Al enviar un mensaje, DKIM utiliza la clave privada para firmar el correo electrónico mientras que la clave pública se publica en el DNS de tu dominio mediante registro TXT.

### COMO GENERAR CLAVES DKIM

💥Para realizar este apartado debes tener instalado **PostFix**

Para generar las claves privadas-públicas e optado por **OpenDKIM**
- Como siempre, previamente a una instalación realizamos
```sh
sudo apt-get update
sudo apt-get dist-upgrade
```
- Instalamos los **OpenDKIM** y sus dependéncias las cuales se instalan al escribir `YES`.
```sh
sudo apt-get install opendkim opendkim-tools
```
Debes tener algo así al finalizar la instalación:

![image](https://user-images.githubusercontent.com/73543470/166957697-a762f788-3f5e-43f1-ab48-7dd53098b093.png)

- A continuación debemos acceder al archivo `nano /etc/opendkim.conf` y debemos modificar los siguientes parámetros para permitir la firma de mensajes para uno o más dominios.

![image](https://user-images.githubusercontent.com/73543470/166958726-643542c7-4a96-4f4f-867d-087386640d50.png)

- Luego tenemos que ir al siguiente archivo `nano /etc/default/opendkim` y añadir al final del archivo la siguiente línea en la que especificamos el número del puerto que utilizará.

![image](https://user-images.githubusercontent.com/73543470/166959725-ea571a18-a9fc-4b17-9be1-c0e33d3f6a47.png)

- Después debemos configurar postfix para utilizar el milter `nano /etc/postfix/main.cf`

 ![image](https://user-images.githubusercontent.com/73543470/166961443-44653682-85f8-4e7c-a7a0-00adcbfac3d2.png)
 
🚦 _**Milter**, es una extensión utilizada para el procesamiento de correos. Permite a los administradores agregar filtros de correo_

#### ESTRUCTURA DE DIRECTORIOS/ARCHIVOS
- Una vez configurados estos parámetros debemos crear una estructura de directorios que contendrá los hosts de confianza, las tablas de las claves, las tablas de las firmas y las claves criptográficas.
```sh
mkdir /etc/dkim
```
- Dentro del siguiente directorio procederemos a crear las diferentes partes que conforman nuestro DKIM.
 **1.** En primer lugar crearemos el fichero `hosts.txt` en el que indicaremos el parámetro local host y nuestra IP.
 ```sh
 touch hosts.txt
 ```
  ![image](https://user-images.githubusercontent.com/73543470/166975862-96d47448-d57f-473f-a987-2d33cc6aa89f.png)
  
  **2.** A continuación crearemos archivo `dkimTable` que contenga una tabla de claves con el dominio y la ruta a su clave privada.
 
  ![image](https://user-images.githubusercontent.com/73543470/166976612-0c8c3573-7ba2-4586-892e-64f43b06b179.png)

  **3.** Crearemos el archivo `dkimSigningTable` que tiene la función de declarar los dominios/direcciones de correo y sus selectores
  
  ![image](https://user-images.githubusercontent.com/73543470/166978332-58dac3bb-620c-438f-9d7c-8e7e41a76e64.png)

#### GENERAR CLAVE PÚBLICA/PRIVADA
  **4.** Una vez realizadas estas configuraciones tenemos que generar las claves públicas y privadas. Para generar nuestras claves efectuaremos la siguiente comanda:
 ```sh
 opendkim-genkey -s mail -d cosmosdesign.es
 ```
 
   **5.** Esta comanda creará dos archivos ya que `-s` especifica el selector que debe utilizará y la `-d` el dominio en cuestión. Los dos archivos creados son `cosmosdesign.es.private` y `cosmosdesign.es.txt`
   
 ![image](https://user-images.githubusercontent.com/73543470/166979958-c490b643-d4e3-47f5-9a07-eccf8b45d233.png)
 
  **6.** Una vez realizados estos cambios debemos agregar la clave pública a nuestro registro DNS generado `/etc/dkim/cosmosdesign.es.txt` y añadirla en el `/etc/bind/dbs/cosmosdesign.es`
  
 ![image](https://user-images.githubusercontent.com/73543470/166981051-e75d5090-6f66-40c9-b672-56634904696e.png)

  **7.** Finalmente debemos reiniciar Postfix y OpenDKIM
```sh
service postfix restart
service opendkim restart
```

### CONFIGURAR ZONAS DNS DEL CLOUD
Una vez hemos configurado los registros DNS de nuestro Cloud debemos modificar 3 archivos que se encuentran en el directorio `cd /etc/bind`.

- En primer lugar, nos encontraríamos con `named.conf`, en este archivo incluiremos nuestra nueva zona cosmosdesign.es, ya que estamos declarando la resolución directa de nuestro dominio.
![image](https://user-images.githubusercontent.com/73543470/173199193-b9ee5b5f-7f38-41e1-a240-1dfb9a21d9d4.png)

- En tercer lugar nos encontrariamos con 'named.conf.default-zones', en esta debemos introducir estos parametros ya que SW Hosting trabaja con ellos. La resolución DNS a nivel de hosting se lleva a nivel de servidor, pero las zonas DNS pasan por otro servidor DNS privado de SWHosting, por tanto, no tengo manera de mostrar la configuración. 

Por tanto, una vez llegados ha este punto ya tendriamos configurado completamente nuestro servicio DNS en el cloud para trabajar con SWHosting.

## 2. INSTALACIÓN LAMP
### APACHE2
_____________
La función principal de apache es brindar a los usuarios todos los ficheros necesarios para la correcta visualización de la página web.
- Instalamos realizando la comanda
```sh
sudo apt install apache2
```
- Comprobamos que este se encuentre activo
```sh
systemctl status apache2
``` 
-  Posteriormente instalaremos `curl`, y efectuaremos la comanda para descargar icanhazip 
```sh
apt install curl
curl -4 icanhazip.com
```

#### ESTRUCTURA DE DIRECTORIOS/PERMISOS
Una vez instalado debemos proceder a configurar el VirtualHost del servicio web. En debian ya se encuentra un directorio previamente definido para realizar la creación de directorios relacionado con las webs. Por tanto, crearemos el directorio '/var/www/cosmosdesign.es' con el nombre de nuestro dominio.

Crearemos una estructura de directorios que sea compatible con el SW Panel, ya que, aunque no lo estemos utilizando, nos interesa tenerlo configurado para poder visualizar, en el apartado de gestión de ficheros, los ficheros principales de la web de un modo más gráfico.

- Para ello crearemos la siguiente estructura dentro de cosmosdesign.es. Esta primera carpeta tendrá /cache, /datos/data, /datos/web, /logs mediante los siguientes comandos

```sh
mkdir - p /var/www/cosmosdesign.es/cache
mkdir - p /var/www/cosmosdesign.es/datos
mkdir - p /var/www/cosmosdesign.es/datos/data
mkdir  -p /var/www/cosmosdesign.es/datos/web
mkdir  -p /var/www/cosmosdesign.es/logs
```

- Una vez creados todos los directorios toca dar permisos a estos, en este caso daremos permisos al usuario creado en el SW Panel al contratar el servicio. Este usuario puede conectarse al Panel de control de SW Hosting y configurar de una manera más grafica el directorio `/var/www/datos//web` y restringiremos los permisos de
`RWX` 

```sh
chown -R  AL...78:AL...78 /var/www/cosmosdesign.es/datos
chmod -R 755 /var/www/cosmosdesign.es/datos
```
_Mediante `-R` especificamos que se realice de manera recursiva. De esta manera este usuario no puede acceder al resto del servidor solo a dichas carpetas, posteriormente configuraremos el servicio FTP._

- Crearemos  el archivo `index.html` en el directorio `/var/www/cosmosdesign.es/datos/web` con el siguiente código para que Apache pueda servir el contenido.

```sh
nano /var/www/cosmosdesign.es/datos/web/index.html
<html>
    <head>
        <title>Bienvenidos</title>
    </head>
    <body>
        <h1>COSMOS SE ENCUENTRA EN MANTENIMIENTO</h1>
    </body>
</html>
```

- En terminos generales la configuración de permisos debe quedar tal que así:

  ![image](https://user-images.githubusercontent.com/73543470/167138100-a0723d4b-a957-4226-a4c8-c6f4f9c3e277.png)
  
_Al iniciar el Apache, este inicia una serie de procesos que se ejecutan con el usuario www-data y el grupo www-data. En el caso de `/logs` hemos indicado que el usuario es www-data que forma parte del grupo root y el único que puede RWX és el usuario www-data_

- Lo siguiente es modificar el archivo de configuración de apache para nuestro uso. En primer lugar crearemos el directorio `swhosting/vhosts/` para que el SWPanel sepa encontrar el archivo de vhosts. Dentro de este directorio crearemos el archivo `cosmosdesign.es.conf`

```sh
mkdir /etc/apache2/swhosting/vhost
nano /etc/apache2/swhosting/vhost/cosmosdesign.es.conf
```
#### CONFIGURACIÓN VIRTUAL HOST
-Debemos configurar nuestro Virtual Host para que quede de la siguiente manera definiendo cada uno de los parámetros
 
![image](https://user-images.githubusercontent.com/73543470/167114188-f0e9cdfb-cd7f-4526-a078-fb589a70066a.png)

En primer lugar, definimos mediante `<VirtualHost*:8080>`que ese será el puerto por el que operará. Tanto `ServerName` como `ServerAlias` establecen que el dominio base que debe coincidir con esta definición de host virtual. Con `DocumentRoot` indicamos el path donde se encuentran los archivos que dan contenido a la página web.

Con el parámetros `Custom Logs` configuraremos el directorio y el nombre del archivo donde se guardaran nuestros registros Logs de Apache. En este caso, le aplicamos la plantilla common donde incluirá los principales parámetros de los logs. Crearemos dos archivos, uno en el que el servidor almacena en el registro de acceso información sobre todas las peticiones que procesa.

Con el parametro `Error Log` Apache enviará cualquier información de diagnóstico y registrará cualquier error que encuentre al procesar peticiones al archivo de registro seleccionado. Los 3 archivos los asignamos a la carpeta `logs` de nuestra web.

- A continuación tenemos que habilitar el archivo con la herramienta `a2ensite`

```sh
a2ensite /etc/apache2/swhosting/vhosts/cosmosdesign.es.conf
```
- Después debemos deshabilitar el sitio que viene predeterminado con deafult.

```sh
a2dissite 000-default.conf
```

- Finalmente comprobamos que todo este correctamente con el siguiente comando

![image](https://user-images.githubusercontent.com/73543470/167132191-fdcd0f44-2a0e-483f-bdcc-d6854e64853e.png)

También podemos visualizar nuestra pagina web accediendo a nuestro navegador

### JERARQUIA DE ARCHIVOS APACHE
Llegados a este punto podemos mencionar que la configuración de Apache no se lleva a cabo en un solo archivo, sino que ocurre a través de un diseño donde se pueden agregar y modificar nuevos archivos.

Los archivos que permiten la modificación de Apache son los siguientes:

```sh
ls -f /etc/apache2
```

![image](https://user-images.githubusercontent.com/73543470/167168084-f5d280a1-f744-469f-af44-ca4be55e47af.png)

En este apartado profundizaremos en la configuración hablando de las utilidades de cada uno de los comandos.

#### APACHE2.CONF
Los detalles principales de la configuración vienen en este archivo, que se divide en tres partes.
- Configuración para processos globales de Apache
- Configuración del servidor
- Configuración vHost
  #### INCLUDE
  La configuración del servidor y los vHosts se manejan mediante la directiva `INCLUDE`, que permite que Apache lea otros archivos de configuración en el archivo `apache2.conf`.

  En nuestro caso tenemos los siguientes `IncludeOptional`, que cargan los módulos de configuración `*.conf` de los directorios indicados. Nosotros al crear un directorio personalizado para el vhost lo tenemos que incluir de esta manera:

    ![image](https://user-images.githubusercontent.com/73543470/167170043-dc062011-d1f8-4ba5-a2a1-05ade42c0a1f.png)

  Además del resto de includes genericos de Apache:

  ![image](https://user-images.githubusercontent.com/73543470/167170253-35404bc4-3dd0-4c11-99df-d71e633207e5.png)

  ![image](https://user-images.githubusercontent.com/73543470/167170323-29a3e3d6-6833-4f85-8339-a3e82a54265b.png)

  #### <DIRECTORY>
  Estas definiciones manejan diferentes directorios con sus respectivos archivos. Apache aplica todas las direcciones en orden, de la mas corta a la más larga, donde existe la posibilidad de anular las opciones anteriores.
  ```sh
  nano /etc/apache2/apache2.conf
  ```
  Las definiciones del directorio aplican reglas para  `/`,`/usr/share`, `/var/www`
  
  ![image](https://user-images.githubusercontent.com/73543470/167173240-1eb0ed23-d770-4508-b42f-dc28f5eb7c6a.png)
  ![image](https://user-images.githubusercontent.com/73543470/167173344-8c057c07-303d-4fc7-a743-0705efdf7c75.png)
  
  Las diferentes reglas establecidas en los diferentes directorios son:
  - `Require`--> restringir o abrir el acceso a diferentes recursos de su servidor.
  - `AllowOverride`--> Se usa para decidir si el archivo `.htacces` puede anular la configuración si se coloca en el directorio del contenido.
  - `FollowSymLinks` --> Afirmamos y permitimos que Apache siga los enlaces simbólicos del directorio.
  - `-Index` --> Denegamos que un diretorio se pueda mostrar como una lista si no hay una página índex.
  - `+MultiViews` --> Permite que si existe un archivo llamado configuration.php en la raíz siempre sea elegido aunque modifiques el archivo .htacces para que realice la búsqueda en otro directorio.

### PHP
_____________
Es el componente que procesará el código permitiéndonos así ejecutar scripts, conectarnos a las bases de datos MariaDB para obtener información y entregar el contenido al servidor web.
  
```sh
apt install php libapache2-mod-php phpmysql
```
 
### MARIA DB
_____________
Para realizar la instalación de este paquete debemos efectuar la siguiente comanda:
```sh
apt install mariadb-server
```
  
-  Nos aseguramos de que se encuentra iniciado mariadb-server con la siguiente comanda:
  ```
  systemctl start mariadb.service
  ```
  
- Una vez este se encuentre activo, procederemos a utilizar un script de mariaDB para restringir el acceso al servidor y eliminar cuentas no utilizadas. Así que en primer lugar debemos ejecutar la siguiente comanda: 
 ```
  sudo mysql_secure_installation
 ```
  
- En este se iniciará y nos pedirá que ingreses la contraseña a la raíz de la base de datos actual. Como no tenemos ninguno creado, lo dejaremos en blanco.
  
  ![image](https://user-images.githubusercontent.com/73543470/173236497-86bbd605-c8ca-4bf9-a737-20a795948f07.png)
  
- En la siguiente opción que nos muestra es si desea configurar una contraseña de reaiz de la base de datos y seleccionaremos NO
  
  ![image](https://user-images.githubusercontent.com/73543470/173236539-9a5ac8fe-9ffc-449c-ae8b-1c193e5bedaf.png)

- Al aceptar este script aceptamos los valores predeterminados para todas las preguntas posteriores, también eliminará usuarios anónimos, la BD de prueba y los inicios de sesión raíz remotos y cargará nuevas reglas para que MariaDB sea más seguro.
  
-A continuación, no vamos a modificar la cuenta raiz ya que por tareas de rotación de logs y el inicio y la detención de el servidor de BD es mejor no cambiar los detalles de autentificación de la cuenta raiz. Por tanto, procederemos a crear una nueva cuenta con las mismas capacidades que la cuenta RAIZ, de la siguiente manera
  ```
  GRANT ALL ON *.* TO 'admin'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
  ```
  
- Seguidamente, vaciamos los privilegios para asegurarnos que estos nuevos se guardan:
  ```
  FLUSH PRIVILEGES;
  ```

- Comprobamos que maria DB se encuentra funcional y podemos acceder a dicha cuenta:
![image](https://user-images.githubusercontent.com/73543470/173236848-99e4a8de-1fe5-4cf2-8579-90c282107375.png)

  
## 3. INSTALACIÓN CERTIFICADO SSL
El certificado SSL que he instalado en esta ocasión es Lets Encrypt. Ya que este es gratuito, además de autorenovable, por tanto, "infinito".
La función de este certificado es generar una clave pública para el dominio cosmosdesign.es que te identifique como administrador de tu dominio. Estas claves se generan a través de la instalación y activación del certificado, y nos permitirán hacer conexiones cifradas entre usuarios y nuestro servidor.

#### SNAP, CORE Y CERTBOT
- El método de instalación que utilizaremos es **cerbot**, pero antes debemos tener instalado el complemento **snapd** que es un daemon necesario para administrar snaps(instantáneas). Recuerda presionar 'YES'+ 'ENTER' para instalar todas sus dependencias también.
  
```sh
apt install snapd
```
  
- Una vez instalado utilizaremos el comando snap para instalar el complemento `core`y actualizarlo.
```sh
sudo snap install core
sudo snap refresh core
```
- Ahora podemos instalar el complemento cerbot, pero utilizaremos el comando snap y determinaremos con la opcion `--classic` que Certbot tiene permiso para editar ciertos archivos de configuración para configurar correctamente el certificado.
```sh
snap install --classic certbot
```
### CONFIGURACIÓN DEL CERTIFICADO SSL
Cuando ya haya finalizado la instalación tenemos que comprobar la configuración de apache, ya que Certbot necesita poder encontrar el Virtual Host en su configuración de apache para configurar automáticamente el SSL así que previamente debemos tener hecho estos pasos "INSTALAR APACHE"

De todas maneras comprobaremos que tenemos 'ServerName'configurado con el nombre del dominio en `/etc/apache2/sites-available/cosmosdesign.es.conf`
![image](https://user-images.githubusercontent.com/73543470/167049886-df606684-64c5-44d2-a955-482bf30764f6.png)

Con el siguiente comando nos fijaremos que no haya ningún error de sintaxis
```sh
apache2ctl configtest
```
Y recibirás un mensaje como este en caso de que todo sea correcto:
  
![image](https://user-images.githubusercontent.com/73543470/167050097-ae1360e0-0368-4d01-9bb8-4d23c05512c1.png)

### OBTENER CERTIFICADO SSL

Realizando la siguiente comanda instalaremos el certificado SSL, mediante '--apache' permitimos que certbot reconfigure apache y recargue la configuración cuando sea necesario.
Indicamos mediante las dos '-d' que queremos que el certificado sea válido para ambos DNS.
```sh
sudo certbot --apache -d cosmosdesign.es -d www.cosmosdeisng.es
```

En el caso de ser la primera vez que inicia cerbot en el servidor, este le pedirá que ingreses una dirección de correo electrónico y acepte los términos del servicio.
A continuación certbot se comunicará con el servidor Lets encrypt y ejecutará el desafío para verificar que eres tú el que controla el dominio por el cual se está solicitando el certificado.

Una vez terminado el desafío y observado el mensaje final podemos acceder a nuestro navegador, introducir nuestra URL y observaremos que esta tendrá un candado y en más información veremos el nombre del Lets Encrypt

![image](https://user-images.githubusercontent.com/73543470/167051490-5499d805-7c65-4ffb-b230-bd5a3200e868.png)

#### RENOVACIÓN AUTOMÁTICA
Para olvidarnos del certificado por completo podemos realizar ela siguiente comanda para que Certbot renueve el SSL cuando este vaya a caducar
```sh
certbot renew --dry-run
```

## 4. INSTALACIÓN NGINX
Cuando alguien hace una solicitud para abrir una página web, el navegador se comunica con el servidor de ese sitio web. Luego, el servidor busca los archivos solicitados para la página y se los envía al navegador.
Funciona como servidor proxy de correo electrónico SMPT, POP3, IMAP.

En primer lugar, hemos de instalar los siguientes paquetes:
```
 apt-get install nginx php5-fpm php5-mysql mysql-server 
```
  
El archivo de configuración del host se encuentra en `/etc/nginx/nginx.conf`, en este observaremos las configuración es default con las que trabaja nginx. En este apartado lo único que haremos será añadir las siguientes líneas. La función de estas es indicar a nginx donde se encuentran las configuraciones de nuestros Hosts Virtuales.
  
Además, debemos añadir:

![image](https://user-images.githubusercontent.com/73543470/173195437-71037c80-c17a-4d35-9083-3af4b5b1bc1b.png)
  
Ahora podemos comprobar que la página por defecto de Nginx se encuentra accediendo por la IP del navegador. El archivo de esta configuración se encuentra en el directorio `/etc/nginx/config.d/default.conf`, en el cual indicaremos lo siguiente 
  
La jerarquía de directorios del servicio de hosting ya la tenemos creada en el directorio `cd /var/www/cosmosdesign.es`. Para que Nginx pueda servir el contenido de dicha página web debemos crear un archivo de configuración, y como hemos especificado anteriormente  en `nginx.conf` hemos incluido nuestro path personalizado llamado:
  ```
  /etc/nginx/swhosting/vhosts/cosmosdesign.es
  ```

La configuración de este archivo contiene la información de como tiene que efectuarse nginx en nuestro dominio. Nosotros hemos realizado las siguientes configuraciones que detallaremos en breves. Lo primero que podemos observar es que abrimos el parámetro server con tal de especificar las variables que actúan en dicho servidor.

- En este caso podemos ver que nginx se comunica con a través del puerto 80
![image](https://user-images.githubusercontent.com/73543470/173237275-3d35abf7-1a1c-418f-97bb-246ab78d0d5a.png)
  
  Significado de las diferentes variables que hay que introducir/modificar:
  
  - Indicamos que el path en el que se encuentran los diferentes archivos que se proporcionan al cargar la página web
  
  ![image](https://user-images.githubusercontent.com/73543470/173237516-9f6353a9-7473-44f6-8712-ff7f7f8868e0.png)
  
  - Indicamos que priorice la busqueda de estos archivos con este orden, ya que si hay un .html se cargará antes que un php
  
  ![image](https://user-images.githubusercontent.com/73543470/173237604-01d57af7-a367-4601-9473-1300595e46d8.png)
  
  - En este apartado debemos indicar la resolución DNS de nuestro dominio, con y sin www.
  
  ![image](https://user-images.githubusercontent.com/73543470/173237630-11d1f5d8-9a1c-41d5-ae54-d182e1439de9.png)
  
  - En la siguiente línea indicamos que muestre error 503 cuando no es capaz de cargar contenido con ngninx en la misma página.
  
  ![image](https://user-images.githubusercontent.com/73543470/173237665-20bb26e1-7f5c-48a3-aa02-97ec523b3c9a.png)

  - En esta imagen observamos el path en el que guardaremos los logs de error y de acceso de nuestro nginx
  
  ![image](https://user-images.githubusercontent.com/73543470/173237688-f15917a1-3c7b-4126-899c-b52879d88949.png)

- Por último realizamos un include diciéndole a nginx que en el siguiente path '/etc/nginx/swhosting/all-vhosts.conf' se encuentran archivos de configuración. Este último paso no es necesario a no ser que trabajes con swhosting, ya que en dicho archivo de configuración se encuentran configuraciones predeterminadas del servicio, cuando los contratas con ellos.
  
  ![image](https://user-images.githubusercontent.com/73543470/173237722-b3575329-2478-48a3-9546-55db1064aba7.png)


- En este caso observamos que nginx está a la escucha por el puerto 443 y esperando contenido HTTP2 o conexiones SSL. Hemos implementado estas dos escuchas para dividir el tráfico que se realiza en la web en dos puertos diferentes, según las consultas que se realizan a nuestra página web. Por ejemplo, en caso de cargar la página con certificado SSL utilizará este apartado de Nginx
  
 ![image](https://user-images.githubusercontent.com/73543470/173237321-f89f2480-5b12-4844-a142-8e20d34ffc5f.png)
  
  La configuración es la misma que en el puerto 80 solo que en esta activamos el certificado SSL y revisamos su PEM y su KEY
  
  ![image](https://user-images.githubusercontent.com/73543470/173238251-3c71adf3-c1c1-44dc-9e63-71c20c42d36e.png)
  
A continuación podemos comprobar si las configuraciones realizadas son correctas:
  
![image](https://user-images.githubusercontent.com/73543470/173238017-cc50d507-b946-47a5-ba75-46d9cb9e5194.png)
  
En el caso de ser así, procederemos a reiniciar nuestro servicio nginx.
```
systemctl restart nginx  
```
  
### Crear un Proxy Pass en NGINX
 
 En primer lugar, comentar que un servidor proxy es una interfaz de la comunicación de la red que se encarga de las peticiones y las transmite en forma de representante antes de que esta llegue a internet y viceversa. En este caso, su función principal es entregar el contenido de la imagen, incluyendo informaciones sobre el servidor principal.
  
  ![image](https://user-images.githubusercontent.com/73543470/173238402-3ff68902-4bf1-4a79-a96f-6c84448d95f1.png)

Para configurar dicho proxypass debemos acceder a nuestro archivo de configuración que se encuentra en `/etc/nginx/swhosting/vhost/cosmosdesign.es` y debemos añadir los siguientes parámetros.

![image](https://user-images.githubusercontent.com/73543470/173238326-b76f414c-4a1d-4a2f-b99d-8521ffdca7fa.png)
  
 - Establecemos los encabezados de las solicitudes, en primer lugar nos encontramos con proxy_pass donde especificaremos que se realiza de manera local y en que  puertos.
  En las siguientes variables se especifican el host, la IP real del sv y la IP forwarded que es de donde proviene la consulta.
  
  ![image](https://user-images.githubusercontent.com/73543470/173239046-dc361ca7-9395-4f95-9de8-09ac06877173.png)
  
  Reiniciamos nginx y ya tendríaamos configurado nuestro proxy pass:
  ```
  /etc/init.d/nginx reload
```

## 5. INSTALACIÓN POSTFIX + DOVECOT
En este apartado configuraremos el servidor para que también opere como un servidor de correo utilizando las tecnologías Postfix, Dovecot, MariaDB y SpamAssasin.

Previamente, debemos tener configurados el dominio, mysql, root y SLL. Además, necesitamos tener configurado FQDN.

Debemos realizar la instalación en la raíz, por tanto, realizamos la siguiente comanda:
```
sudo -i
```

### Instalación de paquetes:
```
apt-get install postfix postfix-mysql dovecot-core dovecot-imapd dovecot-lmtpd dovecot-mysql
```

Una vez comenzada la instalación nos saltará la siguiente pantalla, donde debes seleccionar Internet Site:
  
 ![image](https://user-images.githubusercontent.com/73543470/173190837-1c82b5f6-987e-4582-82c5-e3524d1d548e.png)

 Posteriormente tendremos que introducir nuestro dominio o FQDN:
  
 ![image](https://user-images.githubusercontent.com/73543470/173190890-323a44f3-3879-4b9a-89ba-e761b1390bca.png)

 Una vez instaladas las tecnologías, debemos dirigirnos a nuestro Gestor de BD, en nuestro caso, MariaDB. En este, vamos a configurar 3 tablas, una para el dominio, una para los usuarios y la última para el alias.
  
Para ello iniciaremos sesion en mysql sfsdf
  
## Configurar Postfix
Este lo tenemos que configurar para poder manejar las conexiones SMTP y enviar los mensajes para cada usuario introducido en la base de datos.
  
### main.cf
  En primer lugar debemos hacer una copia del archivo original en `cd /etc/postfix`
  
  ```
  cp /etc/postfix/main.cf /etc/postfix/main.cf
  ```
Procederemos a abrir dicho archivo 'nano main.cf' y lo primero que debemos configurar son los parámetros TLS donde utilizaremos el certificado SSL instalado con anterioridad.
Este archivo básicamente contiene la configuración de los servicios que trabajan con  postfix.
Los parámetros a configurar son los siguientes:
  
![image](https://user-images.githubusercontent.com/73543470/173192048-3e709eee-00db-4e73-a711-125dd440c2fe.png)

Para entender un poco mejor que significan todas estas líneas de comandos, partiremos el código:
- Especifican la ruta donde se encuentra el certificado, estas claves siempre deben tener la extensión, .PEM y .KEY
  
  ![image](https://user-images.githubusercontent.com/73543470/173192101-51469f57-9584-4a54-b058-ace541cf45b8.png)

- Los siguientes indican que se pueden establecer conexiones con TLS o no, dejando al cliente la opción de activarlo o no. El mismo trabajo lo realizan para el servicio smptd, que es el encargado de que el cliente envíe correos al servidor.
  
  ![image](https://user-images.githubusercontent.com/73543470/173192212-3868728e-e4da-4a83-95f4-d26bd75fafdc.png)

- Otro parámetro importante es el siguiente, donde se configura el directorio para descargar la caché de la CPU en las negociaciones TLS
  
  ![image](https://user-images.githubusercontent.com/73543470/173192336-b493ee94-20fc-44d7-897b-9e29ae463e7b.png)

- Por último observamos el soporte SNI, este contiene la tabla con el nombre del dominio y la ruta para PEM y KEY.
  
  ![image](https://user-images.githubusercontent.com/73543470/173192389-fb18cd4f-b743-4efb-8b5d-11c72a208a6c.png)
  
Para finalizar todos los parámetros que debes añadir/modificar de `main.cf` son los siguientes:
  
```
smtpd_tls_cert_file = /etc/ssl/swhosting/certs/MV2016070510001.dnssw.net.pem
smtpd_tls_key_file = /etc/ssl/swhosting/private/MV2016070510001.dnssw.net.key
smtp_tls_security_level = may 
smtp_tls_note_starttls_offer = yes 
smtpd_tls_security_level = may 
smtpd_tls_loglevel = 1 
smtpd_tls_received_header = yes 
smtpd_tls_session_cache_timeout = 3600s 
tls_random_source = dev:/dev/urandom 
tls_random_exchange_name = /var/lib/postfix/prng_exch 
tls_server_sni_maps = hash:/etc/postfix/sni
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
```

### master.cf  
El archivo `master.cf` contiene la configuración específica de cada instancia de postfix. En este aparecen los bloques de submisiones y submisiones de estos.
  
![image](https://user-images.githubusercontent.com/73543470/173192534-ca391be3-9eac-4974-9537-121300ac2305.png)

- El siguiente bloque debemos añadirlo al final del archivo, ya que mediante estos parametros hacemos referéncia a:
  
  Submision ( Puerto 587 ) Ofrece la posibilidad de usar TLS (STARTTLS) ya que así lo establecimos en main.cf con `smtpd_tls_security=may`
  
  Submissions ( Puerto 465 ) Permite y obliga a conectarte vía TLS segun los parámetros que establecimos anteriormente `smptd_tls_auth_only=yes` y `smtpd_tls_wrappermdoe=yes`
  
  ![image](https://user-images.githubusercontent.com/73543470/173192666-16879334-76f8-4bf0-8ce4-404c6201f90c.png)

 Te estarás preguntando y porque submission? Són alias de nombres de puertos, la manera de añadirlos es la siguiente:
 Debemos acceder a `nano /etc/services`, buscar el nombre que haya para el puerto 465, duplicarlo y cambiarle el nombre a submission.
  
  ![image](https://user-images.githubusercontent.com/73543470/173193068-24b208ba-f0fd-403c-9e51-366cdbaf91f8.png)

## SNI
  Este se establece en la configuración del main.cf que hemos mostrado anteriormente, `tls_server_sni_maps = hash:/etc/postfix/sni`
  - hash: indica que buscará el arxiu /etc/postfix/sni.db
  - Este sni.db se genera automáticamente con la ejecución de `postmap -F /etc/postfix/sni`
  
  Por tanto, para la configuración de este debemos acceder al fichero `nano /etc/postfix/sni` e introducir el nombre del cloud con el path de las claves KEY y PEM del certificado SSL. Seguidamente debes introducir el nombre del alias que hace referencia a la IP del correo configurada en los DNS del Cloud, junto con sus respectivas claves.
  
  ![image](https://user-images.githubusercontent.com/73543470/173193378-a6929b88-8382-4995-a319-186674b201da.png)
  
Llegados a este punto debemos reiniciar el servicio Postfix para que los cambios efectuados se lleven a cabo:
  
  ```
  /etc/init.d/postfix relaod
  ```
 ## DOVECOT
 Se trata de un MDA que tiene por función almacenar el correo y servirlo mediante POP3 o IMAP al programa cliente (MUA).
 Para proceder a la configuración de este debemos acceder a los archivos `/etc/dovecot/conf.d/10-ssl.conf` y `10-sni.conf`
  
 - En primer lugar, accederemos a `10-ssl.conf`, donde indicaremos que queremos el servicio ssl activo, e indicaremos donde se encuentra el path a las claves PEM y KEY del ceritficado SSL
  
  ![image](https://user-images.githubusercontent.com/73543470/173194336-c52f37ab-7065-420d-9c2b-7211d90714f2.png)

   Aquí indicaremos el directorio raiz de donde se encuentran nuestros certificados
  
  ![image](https://user-images.githubusercontent.com/73543470/173194407-8acd3ad3-e0d8-48bc-8705-73a9caca99eb.png)
  
- Una vez terminado procederemos a modificar el archivo `10-sni.conf`, en el que deberemos añadir el nombre de nuestro alias de dominio que ahce referencia al DNS del mail, con la localización de los certificados de SLL.
  
  ![image](https://user-images.githubusercontent.com/73543470/173194637-5def9534-f94b-4342-b85d-bd451ec47243.png)
  
 Para finalziar debemos reiniciar el servicio dovecot:
 ```
/etc/init.d/dovecot reload  
```
 
## 4. INSTALACIÓN/CONFIGURACIÓN DE WORDPRESS
Previamente debemos tener instalado la pila LAMP y que nuestro dominio se encuentre bajo un certificado SSL. También necesitamos un dominio adquirido y un
usuario no root con privilegios

### Crear BD y usuario en MARIADB
El primer paso es instalar la Base de Datos para poder almacenar y administrar la información del sitio y del usuario.

#### CREAR USUARIO CON PERMISOS
- Tenemos que ejecutar MariaDB como cuenta RAIZ, o con cualquier usuario que tenga permisos administrativos. En este caso crearemos un usuario, al que le otorgaremos permisos administrativos. El usuario será CQ893_WP, pero antes tenemos que iniciar sesión como usuario raíz.

```sh
sudo mariadb
```
- Posteriormente crearemos el usuario con permisos administrativos utilizando la siguiente comanda:
  ```sh
  GRANT ALL ON *.* TO '	CQ893_WP'@'localhost' IDENTIFIED BY 'passowrd' WITH GRANT OPTION;
```
 - Eliminamos los privilegios para asegurar que los actuales se actualicen y cerrar MariaDB.
 ```sh
  FLUSH SERVICES;
  exit;
  ```
#### CREAR BASE DE DATOS
- Comenzaremos Creando una BD para WordPress realizando la siguiente comanda, el nombre de la base de datos sera la misma que la del usuario
```mariadb
CREATE DATABASE CQ893_WP DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
```
  
- Crearemos un usuario de MYSQL que utilizaremos exculsivamente para operar en nuestra nueva BD con la siguiente comanda:
 ```sql
 GRANT ALL ON CQ893_WP.* TO 'CQ893_WP'@'localhost' IDENTIFIED BY 'password';
 ```
 - Eliminamos los privilegios para asegurar que los actuales se actualicen y cerrar MariaDB.
 ```sh
  FLUSH SERVICES;
  exit;
  ```

 Llegados a este punto ya tendiéramos el usuario y la BD que utilizará Wordpress. Para continuar debemos verificar si tenemos la siguiente extensiones PHP instaladas empleadas por el CMS de Wordpress.

#### EXTENSIONES PHP ADICIONALES
AL configurar LAMP solo necesitamos una cantidad de extensiones mínima para que PHP pueda comunicarse con MariaDB y Wordpress. Pero estos complementos necesitan a su vez más complementos de los cuales se aprovechan para realizar funciones PHP extras.
Por tanto, instalaremos las siguientes:
```sh
sudo apt update
sudo apt install php-curl php-gd php-mbstring php-xml php-xmlrpc php-soap php-intl php-zip
```
  
- Después de instalar los paquetes debemos reiniciar apache2 para que este pueda cargar las nuevas extensiones instaladas.
```sh
sudo systemctl restart apache2
```
  
En este punto, lo único que queda por hacer antes de proceder a la instalación de Wordpress es realizar algunos cambios en la configuración de Apache para permitir que el CMS funcione correctamente.

### INSTALACIÓN DEL ENTORNO
Para instalar WordPress lo primero que debemos hacer es verificar si tenemos el comando 'apt install curl' instalado.
  
 Antes de proceder con la descarga e instalación tenemos que determinar donde va a estar instalado wordpress. En este caso como queremos instalarlo en el dominio cosmosdesign.es, por tanto, procederemos a instalar Wordpress en el directorio ` cd /var/www/cosmosdesign.es/datos/` que tenemos configurado hace rato.
  
 -  Una vez nos encontremos en el directorio anteriormente mencionado debemos descargar Wordpress en su verisón comprimida.
 ```sh
    curl -O https://wordpress.org/latest.tar.gz
``` 
  
- Después tenemos que descomprimir:
 ```sh
 tar xzvf latest.tar.gz
 ```
  
 - Observaremos que se han descargado todos los archivos siguientes:
  ![image](https://user-images.githubusercontent.com/73543470/167429681-c74e120a-43c7-4cc0-b1bf-8f0d60f2e5bc.png)

- Una vez estemos en este punto modificaremos el nombre de la carpeta WordPress que hemos descargado por web. Y seguidamente le cambiaremos los permisos de propiedad y le otorgaremos el usuario proporcionado por SWHosting. También podéis utilizar el usuario www-data, ya que este permite que Apache pueda leer y escribir archivos de WordPress.
 ```sh
sudo chown -R Al..78:AL..78 /var/www/cosmosdesign.es/datos
sudo chown -R www-data:www-data /var/www/cosmosdesign.es/datos
 ```

 - A continuación efectuaremos las siguientes comandas para que los directorios tengan los permisos correctos en los directorios de Wordpress.
```sh
sudo find /var/www/wordpress/ -type d -exec chmod 750 {} \;
sudo find /var/www/wordpress/ -type f -exec chmod 640 {} \; 
```
  
#### INSTALACIÓN DE CLAVES
Posteriormente tenemos que configurar algunos archivos de la configuración principal de Wordpress. El primer objetivo sera ajustar algunas claves secretas para brindar seguridad en la instalación.
  
Para obtener los valores del generador de claves secretas tenemos que efectuar la siguiente comanda:
```sh
curl -s https://api.wordpress.org/secret-key/1.1/salt/
```
El cual mostrará el siguiente mensaje x ejemplo:
![image](https://user-images.githubusercontent.com/73543470/167436074-89580424-ce2d-4d71-a12a-2c888bad3ccb.png)
  
- Una vez realizada esta comanda obtendremos valores unicos, que deberemos copiar directamente en nuestro archivo de configuración, wp-config.php para establecer las claves seguras. Para ello abrimos el archivo `nano /var/www/cosmosdesign.es/datos/web/wp-config.php`
 ![image](https://user-images.githubusercontent.com/73543470/167437504-dd005376-d97c-4b10-a78d-6b9f6262af79.png)
  
 _Recuerda que debes substituir todos los valores mostrados por la comanda que genera las secret keys en el apartado indicado en esta última imagen._
  
-  Ahora que ya se encuentran segurizadas las variables de Wordpress, debemos ajustar el nombre de la base de datos, el usuario y la contraseña que hemos configurado previamente en MariaDB, en el mismo archivo de wp-config.php.
 ![image](https://user-images.githubusercontent.com/73543470/167438662-dcbf4ec8-9056-476d-8dc1-f084c0ae7636.png)

- También añadiremos las siguientes definiciones que permitirán la conexión FTP a un usuario en concreto, y mediante el FS_METHOD direct, evitamos que nuestro WordPress solicite credenciales de FTP cuando se realicen ciertas acciones.
  
En este punto ya tendremos configurados WordPress y, por tanto, ya podríamos acceder a nuestro dominio utilizando nuestro dominio cosmosdesign.es para poder finalizar la configuración de WordPress a través de interfaz web
  
### CONFIGURAR INTERFICIE WORDPRESS
Como los DNS todavía no se encuentran propagados, he modificado mi archivo de host en Windows para que mi PC apunte al dominio en cuestión con la IP asignada. Para así poder iniciar sesión en WordPress y poder comenzar a administrarlo.

_Si quieres saber en qué punto de propagación se encuentran tus DNS de tu dominio puedes utilizar www.whatsmydns.net ._

- Para modificar el archivo de host de nuestro Windows debemos abrir un **Bloc de Notas ejecutado como administrador**.

- Debemos a acceder a archivos e ir al siguiente path `C:\Windows\System32\drivers\etc\hosts`
![image](https://user-images.githubusercontent.com/73543470/166690231-7ee73ff2-cfd1-44e2-a867-576e8508df43.png)

- Seguidamente tenemos que modificar el archivo añadiendo en la parte final de este el nombre del dominio i la IP asignada.
![image](https://user-images.githubusercontent.com/73543470/166690357-da34c6d3-c106-4735-a6c2-567d0d198303.png)
  
- Para acceder a wordpress tenemos que introducir la siguiente URL `http://cosmosdesign.es/wp-admin/` el cual nos redigira a la siguiente pagina donde hemos de especificar el nombre de usuario de conexión a wordpress y la contraseña además de un email. Finalizaremos haciendo click en instalar Wordpress.
  
- Para acceder a wordpress tenemos que introducir la siguiente URL `http://cosmosdesign.es/wp-admin/` donde nos llevará a iniciar sesión que dará a la siguiente ventana
![image](https://user-images.githubusercontent.com/73543470/166509748-f8182557-7336-4fbb-b21e-98d8467e90e0.png)

- Una vez llegados a este punto procederemos a utilizar uno de los Temas predefinidos de los que consta Wordpress. Para ello debemos acceder Apariencias > Temas. En este punto tras una larga búsqueda, me decidí por el siguiente:
![image](https://user-images.githubusercontent.com/73543470/166525726-202a64c7-8ebc-4232-a60e-1a01050b5f42.png)

En este apartado mostraré mediante un breve resumen todas las modificaciones que he realizado en el tema elegido. Dividiéndolo por las diferentes páginas realizadas en el WordPress.

- **Homepage** --> En este apartado, me interesaba que se viera con claridad los 3 conceptos básicos que engloban mi proyecto. A primera vista quería que supieras que la página web trata de creación de páginas web, también me interesaba que se vieran los 3 precios de los 3 formatos de páginas web a hacer y finalmente que entiendan que es un servicio que ofrece soporte y que este sea visible para que lo utilicen.

- **Descripciones de productos** --> Un total de 3 páginas individuales donde se explica las características del producto, porque tiene ese precio, que servicios se ofrecen en el y el estilo de página web que se puede llegar a realizar con el plan seleccionado.

- **Formulario de propuesta** --> Formulario donde debes especificar exactamente lo que deseas realizar en tu página web, el concepto de la empresa, los colores que pueden llegar a definir la entidad, cantidad de hojas aproximadas(como lo que estoy realizando yo en este apartado), aportar una cantidad de seleccionables que sean extras que tengan un coste extra en el proyecto. Además de dejar en claro al cliente que puede mantener-se en contacto con nosotros para hacer una evaluación continua de la página.

- **Muro de mejoras** --> Muro donde el cliente puede ir dejando notas referentes a los cambios que están sucediendo en su página web junto con posibles mejoras.


## 4. INSTALACIÓN DE PLUGINS

Una vez creado el Wordpress, voy a realizar una lista con los plugins que tengo instalados y la funcinonalidad de cada uno.

- **YOAST SEO -->** Básicamente es una ayuda extra al crear la página para que esta quede más optimizada y tu web obtenga más entradas para los motores de búsquedas.
- **LITTLE SPEED CACHÉ -->** Configuración de la caché, servicios CDN, optimización de imagenes y páginas.
- **ELEMENTOR -->** Modificar los elementos visuales de una página web como textos, botones, etc.

**Información extra:** _Un CDN a grandes rasgos es un servidor donde se almacenan las imágenes, videos, etc. de tu página web. Básicamente almacena todos los archivos de gran peso, excepto el código de la página. Esta información se replican en diferentes nodos, de manera que cuando algún usuario accede a la web, detectan que nodo de CDN se encuentra más cerca del punto de carga(PC USUARIO) y procede a cargar las imágenes de dicho nodo, mientras que el código lo carga desde el servidor donde se encuentra el hosting._
  
## 5. INSTALACIÓN EXTRAS
  ## INSTALAR Y CONFIGURAR SPAM ASSASSIN
  En primer lugar debemos instalar el paquete:
  
  ```
  apt-get install spamassasin spamc 
   ```
  
   Seguidamente debemos crear un usuario para Spam Assasin
  ```
  adduser spamd --disabled-login
  ```
  
  Ahora debemos dirigirnos al archivo ` nano /etc/defaul/assassin` y editarlo. Lo primero que debemos hacer es activarlo añadiendo esta línea:
  
  ![image](https://user-images.githubusercontent.com/73543470/173200027-aaeacd50-28e9-4d2f-9b3f-5a14c7e55700.png)
  
  Después necesitamos configurar los parámetros de inicio y las opiones indicando el directorio de creación junto con el usuario
  
  ![image](https://user-images.githubusercontent.com/73543470/173200110-b999f3fc-7046-4461-af0e-6c912fd7a492.png)
  
  En la siguiente línea debemos especificar que el PID del archivo también se guardará en el directorio `/home/spamd`
  
  ![image](https://user-images.githubusercontent.com/73543470/173200186-949e7585-6959-4e87-9c9f-5b726c1ff1bc.png)
  
  Finalmente mediante el `CRON=1` especificamos que las reglas de Spam Asssasins se actualizarán automáticamente.
  
  ![image](https://user-images.githubusercontent.com/73543470/173200228-1eeb2d83-7e5a-42b0-8e68-2e6a450c8450.png)
  
  Una vez llegados a este punto tenemos que configurar las reglas antispam que tendrá nuestro servicio. Para ello debes dirigirte al archivp `nano /etc/spamassassin/local.cf`.
  
SpamAssassin califica el correo, y detecta que el que tiene más de 5 en su verificación es correo no deseado. Para que realice esta función debemos modificar y descomentar estos parámetros en dicho archivo:
  ```
  rewrite_header Subject ***** SPAM _SCORE_ *****
report_safe             0
required_score          5.0
use_bayes               1
use_bayes_rules         1
bayes_auto_learn        1
skip_rbl_checks         0
use_razor2              0
use_dcc                 0
use_pyzor               0
  ```
  
  Posteriormente, necesitamos modificar el archivo `/etc/postfix/master.cf` para decirle que cada correo será revisado por SpamAssassin. Debemos encontrar la linea creada anteriormente con submission y agregar que utilizará el filtro de Spam Assassin
  
  ![image](https://user-images.githubusercontent.com/73543470/173200580-0a75e371-4191-439f-be93-67579b046b33.png)
  
  Finalmente debemos añadir el siguiente parámetro para que spam assassin pueda trabajar.
  
  ![image](https://user-images.githubusercontent.com/73543470/173200663-884af2e6-6909-40a3-a971-ff97966e781b.png)
  
  Por último debes iniciar el servicio SpamAssassin y reiniciar Postfix ya que hemos realizado modificaciones en su configuración.
  ```
  /etc/init.d/postfix reload
  /etc/init.d/assasssin reload
  ```

  ## Instalación Fail2Ban
  
 En este caso instalaremos diferentes extras a nuestro servidor, que nos vendrán bien a la hora de administrarlo o mantenerlo seguro. Comenzaremos por instalar Fail2Ban, es una aplicación escrita en Python, protegiendo a tu sistema bloqueando los intentos de acceso de fuerza bruta.

En primer lugar, como siempre, debemos instalar el aplicativo.
  ```
  apt-get update
  apt-get install fail2ban
  ```
  
  Seguidamente hemos de acceder a `cd /etc/fail2ban` y tenemos que copiar el contenido de `jail.conf` a jail.local
  ```
  cp -pr jail.conf jail.local
  ```
  Una vez copiado nos dirigimos a `jail.local` y analizaremos el contenido de este y realizaremos algunas modificaciones:
  
  En la siguiente imagen observamos el rango de IPs que no se deben banear ya que forman parte de la infraestructura de SW Hosting, también observamos que el tiempo de baneo es 10 horas. A continuación se indica que se procede a banear cuando hay 10 conexiones en un máximo de 60 segundos y en la última es por donde se notifica el baneo.
  
  ![image](https://user-images.githubusercontent.com/73543470/173201973-c505f312-824b-4119-b100-58c673450b56.png)
  
  Debemos configurar Fail2Ban para los diferentes servicios que funcionan en nuestro servidor, comenzaremos por configurar el servicio:
  
  ### Configuración SSH
  Tenemos que configurar que escucha por el puerto 2200 ya que es con el puerto que trabaja SW Hosting.
  
  ![image](https://user-images.githubusercontent.com/73543470/173202223-9dbdb3c6-1c0e-4b4e-816d-4d7777e255ee.png)

  ### Configuración PROTFTPD
  Indicamos los puertos por los alias que hay definidos en el servidor
  
  ![image](https://user-images.githubusercontent.com/73543470/173202301-0c7c505d-ebee-4b36-8df5-d44035b6020d.png)
  
  ### Configuración POSTFIX
  Indicamos los puertos por los alias que hay definidos en el servidor.
  
  ![image](https://user-images.githubusercontent.com/73543470/173240042-30d1c216-d2e2-47b7-8e6a-f8888769fb61.png)

  ### Configuración SASL

  ![image](https://user-images.githubusercontent.com/73543470/173240089-90f55efc-bce7-4779-aeed-69d2ba4e6770.png)
  
  ### Configuración Dovecot y Coruierauth

  ![image](https://user-images.githubusercontent.com/73543470/173240152-cb55bded-13c7-4621-bcf2-b43fd87da4bf.png)
  
  ### Configuración MYSQL
  
  ![image](https://user-images.githubusercontent.com/73543470/173242246-38f6aae0-304c-435d-ba65-e74eeff6d963.png)

  ### Configuración WP
  
  ![image](https://user-images.githubusercontent.com/73543470/173242260-a8588cd1-dfb6-42c6-bc5b-9dbaac7cb713.png)

  
  ### Creación JAIL 
  __
Una vez tenemos configurado todos los parámetros de los diferentes servicios que actúan en el servidor, para poder crear la JAIL y así bloquear los intentos de conexión masivos se deben seguir los siguientes pasos. Estos pasos los mostraré una única vez,, pero este procedimiento se debe llevar a cabo con todas las configuraciones de servicios mencionadas anteriormente:

- Antes de crear las JAILS debemos crear los filtros personalizados donde mediante expresiones regulares le tenemos que especificar que debe buscar en el fichero de logs especificado en el 'jail.local'. Por tanto debemos dirigirnos al directorio '/etc/fail2ban/filter.d' y comenzar a crear ficheros con el nombre del servicio al que realizan la filtración, como por ejemplo realizaremos el de conexión FTP.
  ```
  touch /etc/fail2ban/filter.d/vsftpd.conf
  ```
  ![image](https://user-images.githubusercontent.com/73543470/173241762-fb6d0203-3def-4d44-b29a-6ec669fb9f67.png)
  
   Posteriormente debemos introducir la siguiente contenido para que filtre por FAIL LOGIN CLIENT en el archivo de log especificado:
  
  ![image](https://user-images.githubusercontent.com/73543470/173241814-f0e6b121-9a3b-4aa4-b7f5-51523c1d83a5.png)

  
- En primer lugar, crearemos la JAIL e indicaremos cuáles son las funciones de las diferentes variables que se encuentran en dicha JAIL:
  
    https://user-images.githubusercontent.com/73543470/173202223-9dbdb3c6-1c0e-4b4e-816d-4d7777e255ee.png
  
    `enabled` --> Indica que se encuentra activo
    `port` -->  Los puertos implicados con el servicio, deben ir separados por comas
    `filter` --> Es el nombre del filtro que definiremos en el siguiente `/etc/fail2ban/filter.d/nombre_delfiltro.conf`
    `logpath` --> Se trata de la ruta absoluta del fichero de logs. Fail2Ban tendra en cuenta los logs que hagan "match" con dicha IP
    `maxretry` --> Numero de intentos con los que te quedarás baneado al intentar acceder al servicio en cuestión.
  
Una vez realizadas estas modificaciones debemos realizar la siguiente comanda para comprobar que este se encuentra correctamente configurado:
  ```
  fail2ban-regex /path/al/fichero/de/log.log /etc/fail2ban/filter.d/filtro_fail2ban.conf
  ```
  
## 6. SCRIPTS DESARROLLADOS
  
En este apartado voy a mostrar los scripts que he realizado en el cloud para que se efectúen de una manera automática. Son 3 scripts que ayudan mucho y evitan gastos de 3eros ya que en uno contamos con un backup completo de nuestra página web y en los otros dos mantenemos informado al cliente de las diferentes sobre cargas de recursos que más pueden afectar a su página web.

  ### BACKUPS WORDPRESS

- En primer lugar, nos encontraríamos con el indispensable script de copias de seguridad de nuestra base de datos, en este caso será de WordPress. El método que vamos a utilizar és un mysqldump que esta considerado como una copia en caliente, ya que no hay que parar ningún servicio. Antes de realizar ningún tipo script debemos crear la infraestructura de directorios que contendrá dicha información, en mi caso es la siguiente:
  ```
  mkdir /cosmos-admin
  mkdir /cosmos-admin/backups_wordpress
  mkdir /cosmos-admin/backups_wordpress/BasesdeDatos
  mkdir /cosmos-admin/backups_wordpress/WebContent
  mkdir /cosmos-admin/scripts
  mkdir /cosmos-admin/backups_wordpress/Logs
  ```
 - En segundo lugar crearemos el script con el nombre `nano /cosmos-design/scripts/cosmos_wp.sh` y realizaremos los pasos mencionados en la imagen inferior, antes de continuar debemos dar permisos de ejecución a nuestro script:
  ```
  chmod 777 cosmos_wp.sh
  ```
  ![image](https://user-images.githubusercontent.com/73543470/173249020-ae76084e-c77d-43c5-be12-2d1b73028a0f.png)

- En tercer lugar he creado otro pequeño script que hace una copia pero del contenido web de Wordpress:
  
  ![image](https://user-images.githubusercontent.com/73543470/173249084-8ac9e1ca-000b-4043-b0e5-c854025acafa.png)

  Finalmente he realizado un CRON que ejecuta cada dia a las 12 de la noche el script realizado anteriormente. Para crearlo e introducido la siguiente comanda `crontab -e` y se me ha abierto la siguiente ventana donde e añadido las últimas dos lineas
  
  ![image](https://user-images.githubusercontent.com/73543470/173249220-aa9c5b6b-3f5d-45df-9f84-634318eb1816.png)

  ### SOBREUSO DE RAM
  
  - En este caso se trata de un script que te envia por email un correo indicando que tu RAM esta haciendo un uso excesivo de recursos.
  
  ![image](https://user-images.githubusercontent.com/73543470/173249498-ead216be-6d0b-4d3b-9edc-821e99f6df7a.png)

  ### SOBREUSO DE DISCO
  
  - En este caso trataremos un script con el que automáticamente se debe enviar un correo alertando al cliente que se esta quedando sin espacio disponible en su disco. Concretamente cuando este llegue a un 90% de ocupación.
  
  ![image](https://user-images.githubusercontent.com/73543470/173250106-cb676b8f-6aa9-4a5f-99b4-7d35217fbd2d.png)

  
  
## 7. COMO SER AUTÓNOMO
 Como hemos decidido tomar esta iniciativa, para poder facturar y declarar el dinero ganado con esta nueva entidad, debemos convertirnos en autónomos. Supongo que te estarás preguntando que requisitos se necesitan para ser autónomo, que documentos o donde hay que dirigirse.

El motivo por el cual nos tenemos que hacer autónomos es por el hecho de emprender un negocio, aunque este sea online. Por tanto, como nosotros vamos a vender nuestro servicio de creación de páginas web, deberemos facturar los costes y los beneficios a nombre de la entidad empresarial y no bajo nuestro nombre.

Antes que nada debes conocer las dos instituciones con la que debes tratar para realizar dichos trámites que son: *la Agencia Tributaria* (Hacienda) y la Seguridad Social (INSS)

### Requisitos Previos para ser Autónomo
____
Estos requisitos son establecidos spor el Estatuto de Trabajadores Autónomo de España y son los siguientes:

- Contar con actividad económica por cuenta propia, es decir, tener algún tipo de ingreso o ahorro.
- Ser mayor de edad con libre disposición de bienes.
- Ser menor de edad, pero emancipado y cumpliendo el artículo 232 del Código Civil.
- Estar registrado en Hacienda, demostrando actividad económica.
- Desarrollar esta actividad sin depender de la dirección de otros
- Estar dado de alta en el Régimen Especial de Trabajadores Autónomos.(https://www.seg-social.es/wps/portal/wss/internet/Trabajadores/Afiliacion/10548/32825#625)
- La actividad debe realizarse de manera habitual como fuente de ingreso principal o secundaria y emitir una factura por ello.

### Requisitos y solicitudes para ser autónomo en Hacienda
____
Para estar registrado en Hacienda como un autónomo debes realizar los siguientes pasos en orden:

**1.** Solicitar una cita en la Agencia Tributaria más cercana de tu localidad.

**2.** Rellenar y presentar el modelo 036 o 037, básicamente son documentos donde informarlos a la agencia tributaria datos costos/beneficios que generamos con nuestra actividad.

**3.** Estar al corriente de que porcentaje de Impuestos de Actividades Económicas (IAE) te corresponde dependiendo de tu servicio profesional. En la siguiente URL puedes comprobar el porcentaje. https://www2.agenciatributaria.gob.es/ADUA/internet/es/aeat/dit/adu/adws/certificados/Tabla_de_epigrafes_IAE.pdf

**4.** Debes estar atento, ya que puede que necesites registrarte en el Régimen de Operadores Intracomunitario (ROI), es decir, si tu empresa ejecutará operaciones dirigidas a algún otro país de la Unión Europea.

**5.** Conocer en que régimen fiscal te incluirán de acuerdo con tu actividad profesional.

**6.** Estar al tanto del impuesto que te corresponderá pagar.

**7.** Conocer los modelos de autoliquidación que tendrás que presentar cada trimestre y las declaraciones informativas anuales cuando finaliza el año. Estos se presentan mediante el modelo 111 (IRPF) y el modelo 115 (alquiler de inmuebles urbanos).

- Te proporciono más información sobre el modelo: https://www.infoautonomos.com/fiscalidad/rellenar-modelo-111-irpf/

**8.** Finalmente debes darte de alta voluntariamente en el servicio de notificaciones electrónicas de hacienda

_Revisar modelos 037, 111 ya que son con los que realizas la solicitud_

### Requisitos y solicitudes para ser autónomo en Seguridad Social
____
En un plazo de 60 días antes del inicio de la actividad marcada por Hacienda, debes de darte de alta en RETA. Los pasos a seguir son los siguientes.

1. Alta presencial como Autónomo de SS tendrás que entregar el modelo TA0521 de solicitud junto con el DNI y la fotocopia del alta en hacienda.

2. Debes presentar tu CNAE, el codigo con el que se representa tu actividad económica.

3. Definiremos nuestra base de cotización entre una cuantía máxima y mínima, anual. La base de cotización mínima y máxima son **960,60€€ y 4139.40** establecida por el Gobierno Español. Por tanto, la cuota de autónomos mínimas del 30.6% de 966.6, por lo que tendremos que pagar 294 mensuales.

- URL con más información sobre las bases de cotización: https://www.infoautonomos.com/seguridad-social/bonificaciones-autonomos-reta/

4. Para conocer las bonificaciones de la Seguridad Social y que concuerde con su caso:

- También proporciono este artículo sobre las bonificaciones en la cuota de autónomos para que este no sea tan costoso: https://www.infoautonomos.com/seguridad-social/bonificaciones-autonomos-reta/

Una vez llegados a este punto ya tendríamos toda la documentación preparada y lista para estar dados de alta de autónomos. ¿Vale y ahora que? Ya que te has dado de alta de autónomo para poder realizar facturas de manera legal.

Observamos 3 modelos diferentes de facturación según el tipo de negocio que llevemos a cabo:

- **Factura de tipo simplificada** --&gt; es un tipo de factura que se emite para clientes particulares que no entran en la categoría de empresas ni se encuentran dados de alta en el sistema de autónomos

- **Factura de tipo venta** --&gt; es un tipo de factura que sigue el modelo de relación comercial autónomo-empresa. Es la más conocida y la más completa.

- **Factura de tipo rectificativa** --&gt; es una clase de factura que únicamente se emite en el caso de que hayas llegado a efectuar una factura con algún error.

Según el cliente, deberemos de hacer uso de un modelo o de otro. Siempre podemos contar con algún programa para gestionar las facturas y emitirlas como Mgest, Factusol, SeniorFactu, Contasol...

Ya llegaríamos al final del apartado de como darte de alta en la Seguridad Social y Hacienda y finalmente ser autónomo. ¿Pero en España esto lo único que te hace pensar es, vale ya estoy dado de alta, ahora cuanto voy a tener que pagar y cada cuanto?

### Que debemos pagar a Hacienda?
____

- **Declaración IRPF**
Es un impuesto que se paga a nivel progresivo, cuanto más ingresos se generan mayor será el porcentaje de este impuesto

- **IVA**
Es un impuesto sobre el valor producido por las empresas. En España esta se posiciona en un 21% que debes incluir en el coste de tus productos

- **Tramitar modelo 347 (en caso de operar para terceros dentro de la UE)**
Si emites facturas y desarrollas servicios a terceros en la UE debes presentar este modelo para tramitar el excento del IVA

### Hecha la ley hecha la trampa
____
En nuestro caso, no hemos decidido dar el paso darnos de alta como autónomo, ya que, como mi actividad genera ingresos superiores a los 950 € brutos mensuales y la actividad económica no es habitual, podemos realizar facturas sin ser autónomos.

Propongo la siguiente URL donde encontrarás más información sobre si puedes realizar facturaciones sin estar dado de alta:

- https://www.infoautonomos.com/facturas/facturar-sin-ser-autonomo/

- https://www.infoautonomos.com/ser-autonomo-o-no/ser-autonomo-o-no-con-ingresos-bajos/

## 7. BALANCE EMPRESARIAL DEL PROYECTO

Finalmente, una vez desarrollado el proyecto debemos valorar los costes que este va a tener, plantear los beneficios mínimos que necesitamos para no obtener perdidas(Punto Muerto) y definir los posibles Costes Variables o Costes Fijos que este va a tener.

Es importante siempre que se decida empezar un proyecto evaluarlo financieramente, ya que, puede ser una muy buena idea, pero que requiera de un capital más grande para comenzar y esto conlleve a un riesgo mayor, porque la posibilidad de perder dinero aumenta exponencialmente.

A priori, un emprendimiento online es el menos costoso de todos, porque, para empezar, no cuentas con ninguna tienda física, la cual es bastante costosa. Básicamente con una empresa online solo debemos hacernos cargo de los gastos de Hosting + Cloud + Cuota Autonomo + Hacienda.
En el caso de no tener conocimiento de gestión de Hosting + Cloud tus costos aumentarían, igual que si la gestión de darse de alta como autónomo te la realiza una gestoría.

En el caso de cosmos design hemos procedido a evaluar los Costes que conllevaría el proyecto, y los hemos dividido en Fijos y Variables:

___

- Coste Fijo:

Cuota Seguridad Social = 60€/mes --&gt; En el caso de no contar con el bono son 220

Coste del Dominio = 7.50€/anual --&gt; Pasamos el coste a mensual y el resultado es: 0.625€

Coste del Hosting V.1 = 7.50€/mensual

Coste del Cloud/Hosting V.2 = 12€/mensual

Coste del Cloud/Hosting V.3 = 37€/mensual

TOTAL= |68€| |80€| |112|

_La cuota de la seguridad social consta de un descuento del 80% el primer año, por tanto, pagaremos 60€ en vez de 294_

___

- Costes Variables

Uso de recursos del Cloud = No se pueden calcular, porque dependen del proyecto del cliente.

Tempo de dedicación al proyecto = Variable según la cantidad de horas que debo dedicarle al proyecto

___

- Beneficios:

Pack Simple = desde 150€

Pack Completo = desde 300€

Pack E-Commerce = desde 500€

___

### PUNTO MUERTO CONOCE TU BENEFICIO
Partiendo de la fórmula de Punto Muerto obtendremos la cantidad de servicios que tenemos que vender para obtener beneficio, aunque a simple vista, observamos que únicamente con 1 sola venta ya obtenemos la cantidad suficiente de dinero como para no obtener perdidas. Por este motivo, es factible hacer este tipo de emprendimientos, ya que las perdidas son mínimas.

La fórmula es la siguiente:

'''
Q*= CostesFijos / PrecioProducto - Coste Variable de Cada Producto
'''

Sí la ejecutamos, el resultado del Pack Simple es:

'''
Q*= 68 / 150 - 10 = 0.5
'''
Esto significa que con tan solo una venta ya nos encontraríamos por encima del punto muerto y, por tanto, los beneficios son mayores

![image](https://user-images.githubusercontent.com/73543470/173235818-789e25ee-b1aa-4b9c-9760-afcadefe51d2.png)

En el caso de encontrarnos sin bonos de la seguridad social como autónomo al punto muerto varía un poco, quedando de esta manera:

'''
Q* = 302 / 150 -10 = 2
'''
En este caso tenemos que vender mínimo 2 para que sea rentable, ya que si no estaríamos obteniendo perdidas.

_En estas sumas ya se encuentra el precio con el IVA añadido_

En el caso de las otras opciones, los resultados son similares, ya que el coste es mucho menor que el precio de venta,por lo tanto, únicamente con vender uno este ya es rentable aunque no excesivamente.

Los cálculos efectuados se han efectuados para calcular el beneficio mensual no anual. Por tanto, para no obtener perdidas cada mes mínimo debemos vender 1 página web Simple y pasados los años de bono de autónomo, deberemos vender 4 cada mes para poder obtener beneficio.

### 8. CONCLUSIÓN

Una vez llegados a este punto deberíamos tener nuestro Cloud configurado y operativo para el hosting de una página web. En donde hemos aplicado todos los conocimientos aprendidos en el ciclo superior de ASIX y unos cuantos conceptos donde nos hemos adentrado con más profundidad. Los cuales los he aprendido en el trabajo, donde empece a hacer las prácticas.

No es un proyecto supercomplicado, ni superoriginal, pero la intención de este proyecto, es que sea real y palpable. Quería emprender y no supe como hasta que di con esta idea. Día tras día, en mi trabajo observaba a clientes que no tenían ni idea de ejecutar este tipo de tareas y nos pedían ayuda a nosotros, pero claro, el soporte que realizamos en SW Hosting es a nivel de servidor y no a nivel de diseño de páginas web. Al observar la demanda, me decanté por realizar una página web donde la gente pudiera ponerse en contacto con nosotros y poder desarrollar nuestro potencial.

Además de crear páginas web, vi la oportunidad de desarrollar mis capacidades como Administrador de Sistemas, ya que en un principio estamos trabajando bajo otra empresa de Hosting, pero en un futuro y en el caso de que la empresa fuera productiva, la idea es tener nuestros propios servidores con AWS donde nosotros los administramos y gestionamos por completo. Donde también me gustaría implementar scripts de autolanzado.

Estoy satisfecho con el trabajo realizado, ya que gracias a este proyecto he entendido en más profundidad el comportamiento de un Cloud junto con todos sus servicios. Además de tomar la iniciativa de montar una pequeña empresa que conlleve pocos gastos y aunque puede que no rentable, me sirva como experiencia y como un dinero extra que puede entrar cada mes. Quería agradecer al equipo docente de ASIX2, ya que gracias a ellos muchos de nosotros hemos dado un giro 180º a nuestra vida simplemente dándonos conocimientos sobre este sector. Agradecer a todos los compañeros que he tenido este curso, con los que nos hemos apoyado y ayudado mutuamente y hemos logrado llegar hasta el final de este camino.

Espero que el proyecto este a la altura y no haya sido demasiado aburrido de corregir para vosotros. Un gusto cerrar esta etapa con vosotros y os deseo lo mejor.



