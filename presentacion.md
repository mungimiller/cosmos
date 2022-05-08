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

## QUE ES HELPDESK
En este caso he realizado la compra del domino y del hosting/cloud con la empresa de SW Hosting, ya que trabajo allí y es más comodo para mi monitorizar/configurar mi servidor ya que funciona bajo la infraestructura de SW

El hecho de que conozca en cierta medida la infraestructura informatica de la empresa se debe a que ocupo la categoria **Help Desk**. Esta posición, es en la que problablemente empezarás en el caso de trabajar en el area de Hosting+Cloud ( con la finalidad de ser Administrador de Sistemas, en este caso lo más probable que sean de SO Linux en su gran mayoria ).

Al trabajar en el area **Help Desk**, perteneces al departamento de Soporte de la empresa. Por tanto, aprendes como funciona la infraestructura de de dicha empresa, los diferentes programas que utilizan para dar mantenimiento a los servidores que funcionan 24Hs al dia. Además estas empresas suelen tener un cliente visual con el que el cliente puede administrarse el servidor de una manera más gràfica, en este caso seria SWPanel, pero encontrarias otras muchas posiblidades como cPanel, Plesk entre otros.

Por tanto tu funcion és responder a las dudas de los clientes ya sea referente a la configuración del servidor mediante algún cliente de los anteriormente menciondos o errores o incidencias que esten teniendo los clientes con su propio servidor. Cabe recordar, que cuando tu contratas un servidor, a no ser que contrates un servicio de monitorización activo mensual, este es privado, y la empresa en cuestión no puede acceder a tu servidor para observar los logs por ejemplo. Normalmente, este apartado se suele llamar **"Muro de soporte"**, serían las incidencias de menor nivel. 

Después encontrariamos los **Tickets Técnicos**, donde entrarian las consultas/acciones/problemas sobre el servidor de un cliente que por ejemplo, paga la mensualidad de monitorización. En este caso, segun la dificultad de la propuesta tu función como HelpDesk es seguir el protocolo de la empresa, revisar el estado del cloud, observar si puedes realizar una acción en el servidor o solucionar un error de este. En el caso de no saber, siempre puedes preguntar a tus compañeros, ellos siempre saben más que tu cuando acabas de empezar. En el caso de ser una accion dificil o un error que no podeis solucionar, lo reportas con acciones que ya hayas realizado para que el Administrador de Sistemas que lea tu reporte no tenga que realizar la tarea dos veces. En el caso de poder solucionar el ticket llevarás a cabo las acciones que creas necesarias. Normalmente suelen peditte coDeploys, cambios de cabezeras, cambiar parametros PHP de Apache, cambiar permisos de directorios y ficheros...

Otra de las funciones que realizaras es supervisar el estado de los servidores con un programa de monitorización de equipos y servicios de la red. En mi caso es **NAGIOS**. En este, te iran apareciendo diferentes alertas como _Warning y Critical_ definiendo el problema ya sea a nivel de Hardware por ejemplo por sobreuso de los vCores, como por ejemplo un problema MAILQ o un RevisarHack por exceso de conexiones al servidor por segundo.

## COMPRA DEL DOMINIO

Antes de proceder a realizar la instalación del servicio, he comprado el dominio de la página web cosmodesigns.es, mediante la opción que proporciona el SW Panel de la siguiente manera:
- Accedemos a Dashboard de SWPanel
- Dominios i SSL
- Cartera de Dominios
- Añadir Dominio
- Verificamos si este se encuentra disponible. Siempre podemos utilizar herramientas como www.who.is para verificar el estado del dominio que nos interese.
- Una vez comprado nos pedira que demos un monton de datos declarando que somos una persona que existe, mediante DNI, etc.
- Después ya tendríamos nuestro dominio comprado y guardado en nuestra billetera de dominios.
Una vez este dominio es comprado los registros DNS no apuntan a ningún servicio de Hosting. Por tanto, procederemos a asignar los DNS que le pertocan al dominio 
utilzando la herramienta del SWPanel. Los DNS deben ser el nombre del cloud y uno de los servidores con los que SWHosting trabaja.

## COMPRA DEL CLOUD
Ahora que ya tenemos en nuestra posesión el dominio, observaremos que estamos en el servidor whois de dominios delcarados en internet, resolviendo con el dia de contratación y la empresa que registró el dominio que en este caso fue SWHosting.

Ahora tenemos que crear nuestro cloud, para ello iremos a la parte superior derecha del Panel y seleccionaremos Crear nuevo servicio.
- Seleccionaremos Cloud
- Cloud One
- Debian v.10

Una vez aceptemos la compra se nos enviará al correo electronico las credenciales de usuario y contraseña de acceso SSH al Cloud. Y listo ya podriamos acceder a el.

Para no tener que estar introduciendo la tediosa contraseña que debemos tener por la seguridad de nuestro cloud, yo he realizado una autorización para que mi Putty se pueda conectar directamente al cloud al cargar la configuración de este.

Como nosotros ya tenemos el usuario SSH creado con unas credenciales uqe ya nos ha proporcionado la empresa de servicio de hosting. Lo unico que haremos sera decirle a windows que cada vez que ejecute el acceso directoq que crearemos de Putty, ejecute una comanda 
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
- Hemos creado la carpeta ya que puede que en un futuro existan mas hostings en el servidor y por tanto diversas configuraciones DNS. Debemos entrar a la carpeta y  vamos a crear un archivo con el nombre del dominio en cuestión y configurar los registros DNS que deben resolver para ese dominio.
![image](https://user-images.githubusercontent.com/73543470/166709151-e4f824f7-eda7-43ed-8651-08c934f4a5e4.png)


### CONFIGURACIÓN DNS DEL CLOUD
A continuación voy a explicar los parametros que aparecen en la siguiente imagen para poder entender mejor la configuración realizada

  ![image](https://user-images.githubusercontent.com/73543470/166709653-f70ba7aa-477b-4b2f-91f2-bd14b8535b50.png)

  En este apartado debemos indicar le nombre del servidor, en mi caso tiene este nombre ya que al generar   el cloud con con SW Hosting, le assigna un nombre con la fecha de creación del cloud.

####  REGISTRO MX
  ![image](https://user-images.githubusercontent.com/73543470/166711011-7b944677-b39a-4873-981a-be6b448c5073.png)

  Con la siguiente linea indicamos que el servidor de correo és el mismo en el que nos encontramos ahora  mismo.

####  REGISTRO DNS
![image](https://user-images.githubusercontent.com/73543470/166711274-b4d0ae55-80b9-4836-8247-f0f3e79aacc2.png)

  En la siguiente liena encontramos los registros DNS que utiliza nuestro Cloud para resolver a nivel de internet, en este caso tenemos dos, el principal que vendria a ser el nombre del cloud nuevamente y el secundario que es un servidor dns con el que trabaja SWHosting.

####  REGISTRO A
![image](https://user-images.githubusercontent.com/73543470/166712006-6f4ff46e-f30a-4d64-ba8c-d72f9ea4e31e.png)

  Aquí nos encontramos el registro A, el cual hace referencia a la página web. Cuando escribimos cosmosdesign.es, realmente estamos haciando referencia a la IP descrita en este apartado.

#### REGISTRO CNAME
![image](https://user-images.githubusercontent.com/73543470/166711970-6c14c516-534e-430f-911d-e03a3904b3b1.png)

  Observamos que estos dos parametros hacen referéncia a los registros CNAME que son alias del dominio, su funcion son parecida a la de un subdominio. EN este caso hemos indicado que si escriben el dominio con www tambien resuelva y muestre nuestra pàgina. También hemos indicado que si escriben mail.nombredelcloud.es este resuelva con el nombre del servidor, el cual te redireccionará al webmail.

#### REGISTRO TXT - SPF1
![image](https://user-images.githubusercontent.com/73543470/166950612-5bd81bd9-5e39-41e0-a8b9-55e09c9335f6.png)

  La función de SPF és determinar que servidores de correo y dominios tiene permitido enviar correo en nombre de tu dominio. También indica a los servidores que reciben tu correo que hacer con los mensajes una vez comprobados, confirman que los mensajes parecen proceder de tu servidor autorizado.

  En este caso hemos declarado mediante `MX` autorize a un servidor de correo mediante el registro MX del dominio. ( En este caso es el nombre del cloud y al no indicar el MX, automáticamente tomara el registro MX creado en este mismo archivo)

  Mediante `a` autorizamos al servidor de correo por la IP del servidor de correo.

  Finalmente con `~all` los servidores que reciben correo suelen aceptar los mensajes de remitentes que no figuran en el registro SPF, pero los marca como sospechosos.

#### REGISTRO TXT - DMARC1
![image](https://user-images.githubusercontent.com/73543470/166985751-da33ba48-b209-4e73-8b40-3b8e33cbad47.png)

  En este caso configuraremos el servicio dmarc1, ayuda a los destinatarios a determinar si un mensaje coincide con lo que sabe sobre un remitente. Por tanto, si el mensaje no coincide el servidor receptor puede verificar el registro DMARC para orientarte sobre como manejar el mensaje no alieneado.
  
  En este caso, la `-p` indica que que no se lleve a cabo ninguna acción contra el correo no autenticado, pero que envie en su lugar informes de correo electronico a la dirección mailto inscrita en el registro DMARC
  
 ####  REGISTRO SRV
![image](https://user-images.githubusercontent.com/73543470/166985839-0d7df034-44e8-487f-972e-1d46a50559ad.png)
  
  El registro SRV permite que los servicios se ejecuten facilmente en puertos no standard y reducir la carga.
  
  El parametro `autodiscover`, como bien dice descubre automaticamente el nombre simbolico del servicio. Con `_tcp` indicamos el protocolo de transporte del servicio. 
  
  El valor `SRV` indica la clase de registro DNS que és. `443` indica el puerto en el que se encuentra el servicio. Finalmente `ce202205..dnssw.net` indica el nombre del host que  proporciona el servicio.

#### REGISTRO TXT - DKIM1
![image](https://user-images.githubusercontent.com/73543470/166952004-258b38fd-9343-4e68-9d4f-8f68f574fb4b.png)

En este apartado hemos configurado registro DKIM, que és un metodo de autentificación de correo electronico que evita que spammers entre otros elementos maliciosos, se hagan pasar por un dominio.

Este se divide en dos partes, la que se almacena en los registro del DNS para el dominio y en las cabezeras que se adjunta a todos los correos electrònicos de un dominio.
Al enviar un mensaje DKIM utiliza la clave privada para firmar el correo electronico mientras que la clave publica se publica en el DNS de tu dominio mediante registro TXT.

### COMO GENERAR CLAVES DKIM

💥Para realizar este apartado debes tener instalado **PostFix**

Para generar las claves privadas-publicas e optado por **OpenDKIM**
- Como siempre, previamente a una instalación realizamos
```sh
sudo apt-get update
sudo apt-get dist-upgrade
```
- Instalamos los **OpenDKIM** y sus dependencias las cuales se instalan al escribir `YES`.
```sh
sudo apt-get install opendkim opendkim-tools
```
Debes tener algo así al finalizar la instalación:

![image](https://user-images.githubusercontent.com/73543470/166957697-a762f788-3f5e-43f1-ab48-7dd53098b093.png)

- A continuación debemos acceder al archivo `nano /etc/opendkim.conf` y debemos modificar los siguientes parametros para permitir la firma de mensajes para uno o más dominios.

![image](https://user-images.githubusercontent.com/73543470/166958726-643542c7-4a96-4f4f-867d-087386640d50.png)

- Luego tenemos que ir al siguiente archivo `nano /etc/default/opendkim` y añadir al final del archivo la siguiente linea en la que especificamos el numero del puerto que utilizará.

![image](https://user-images.githubusercontent.com/73543470/166959725-ea571a18-a9fc-4b17-9be1-c0e33d3f6a47.png)

- Después debemos configurar postfix para utilizar el milter `nano /etc/postfix/main.cf`

 ![image](https://user-images.githubusercontent.com/73543470/166961443-44653682-85f8-4e7c-a7a0-00adcbfac3d2.png)
 
🚦 _**Milter**, es una extensión utilizada para el procesamiento de correos. Permite a los administradores agregar filtros de correo_

#### ESTRUCTURA DE DIRECTORIOS/ARCHIVOS
- Una vez configurados estos parametros debemos crear una estructura de directorios que contendra los host de confianza, las tablas de las claves, las tablas de las firmas y las claves criptográficas.
```sh
mkdir /etc/dkim
```
- Dentro del siguiente directorio procederemos a crear las diferentes partes que conforman nuestro DKIM.
 **1.** En primer lugar crearemos el fichero `hosts.txt` en el que indicaremos el parametro local host y nuestra IP.
 ```sh
 touch hosts.txt
 ```
  ![image](https://user-images.githubusercontent.com/73543470/166975862-96d47448-d57f-473f-a987-2d33cc6aa89f.png)
  
  **2.** A continuación crearemos archivo `dkimTable` que contenga una tabla de claves con el dominio y la ruta a su clave privada.
 
  ![image](https://user-images.githubusercontent.com/73543470/166976612-0c8c3573-7ba2-4586-892e-64f43b06b179.png)

  **3.** Crearemos el archivo `dkimSigningTable` que tiene la función de declarar los dominios/direcciones de correo y sus selectores
  
  ![image](https://user-images.githubusercontent.com/73543470/166978332-58dac3bb-620c-438f-9d7c-8e7e41a76e64.png)

#### GENERAR CLAVE PÚBLICA/PRIVADA
  **4.** Una vez realizadas estas configuraciones tenemos que generar las claves publicas y privadas. Para generar nuestras claves efecutaremos la siguiente comanda:
 ```sh
 opendkim-genkey -s mail -d cosmosdesign.es
 ```
   **5.** Esta comanda creará dos archivos ya que `-s` especifica el selector que debe utilizará y la `-d` el dominio en cuestión. Los dos archivos creados son `cosmosdesign.es.private` y `cosmosdesign.es.txt`
   
 ![image](https://user-images.githubusercontent.com/73543470/166979958-c490b643-d4e3-47f5-9a07-eccf8b45d233.png)
 
  **6.** Una vez realizados estos cambios debemos agregar la clave publica a nuestro registro DNS generado `/etc/dkim/cosmosdesign.es.txt` y añadirla en el `/etc/bind/dbs/cosmosdesign.es`
  
 ![image](https://user-images.githubusercontent.com/73543470/166981051-e75d5090-6f66-40c9-b672-56634904696e.png)

  **7.** Finalmente debemos reiniciar Postfix y OpenDKIM
```sh
service postfix restart
service opendkim restart
```

Una vez llegados ha este punto ya tendriamos configurado completamente nuestro servicio DNS en el cloud.

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
-  Cortafuegos que aun no se configurar

-  Posteriormente instalaremos `curl`, y efectuaremos la comanda para descargar icanhazip 
```sh
apt install curl
curl -4 icanhazip.com
```
#### ESTRUCTURA DE DIRECTORIOS/PERMISOS
Una vez instalado debemos proceder a configurar el VirtualHost del servicio web. En debian ya se encuentra un directorio previamente definido para realizar la creación de directorios relacionado con las webs. Por tanto crearemos el directorio  `/var/www/cosmosdesign.es` con el nombre de nuestro dominio.

Crearemos una estructura de directorios que sea compatible con el SW Panel ya que, aunque no lo estemos utilizando, nos interesa tenerlo configurado para poder visualizar en el apartado de gestion de ficheros, los ficheros principales de la web de un modo más gráfico.

- Para ello crearemos la siguiente estructura  dentro de cosmosdesign.es. Esta primera carpeta tendra /cache, /datos/data, /datos/web, /logs mediante los siguientes comandos
```sh
mkdir - p /var/www/cosmosdesign.es/cache
mkdir - p /var/www/cosmosdesign.es/datos
mkdir - p /var/www/cosmosdesign.es/datos/data
mkdir  -p /var/www/cosmosdesign.es/datos/web
mkdir  -p /var/www/cosmosdesign.es/logs
```

- Una vez creados todos los directorios toca dar permisos a estos, en este caso daremos permisos al usuario creado en el SW Panel al contratar el servicio. Este usuario puede conectarse al Panel de control de SW Hosting y configurar de una manera mas grafica el directorio `/var/www/datos//web` y restringiremos los permisos de `RWX` 
```sh
chown -R  AL...78:AL...78 /var/www/cosmosdesign.es/datos
chmod -R 755 /var/www/cosmosdesign.es/datos
```
_Mediante `-R` especificamos que se realize de manera recursiva. De esta manera este usuario no puede acceder al resto del servidor solo a dichas carpetas, posteriormente configuraremos el servicio FTP._

- Crearemos  el archivo `index.html` en el directorio `/var/www/cosmosdesign.es/datos/web` con el siguiente codigo para que Apache pueda servir el contenido.
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
  
_Al iniciar el Apache, este inicia una serie de processos que se ejecutan con el usuario www-data y el grupo www-data. En el caso de `/logs` hemos indicado que el usuario es www-data que forma parte del grupo root y el único que puede RWX és el usuario www-data_

- Lo siguiente es modificar el archivo de configuración de apache para nuestro uso. En primer lugar crearemos el directorio `swhosting/vhosts/` para que el SWPanel sepa encontrar el archvio de vhosts. Dentro de este directorio crearemos el archivo `cosmosdesign.es.conf`
```sh
mkdir /etc/apache2/swhosting/vhost
nano /etc/apache2/swhosting/vhost/cosmosdesign.es.conf
```
#### CONFIGURACIÓN VIRTUAL HOST
- Debemos configurar nuestro Virtual Host para que quede de la siguiente manera definiendo cada uno de los parametros
 
![image](https://user-images.githubusercontent.com/73543470/167114188-f0e9cdfb-cd7f-4526-a078-fb589a70066a.png)

En primer lugar definimos mediante `<VirtualHost*:8080>`que ese será el puerto por el que operará. Tanto `ServerName` como `ServerAlias` establecen que el dominio base que debe coincidir con esta definicion de host virtual. Con `DocumentRoot` indicamos el path donde se encuentran los archivos que dan contenido a la página web.

Con el parametros `Custom Logs` configuraremos el directorio y el nombre del archivo donde se guardaran nuestros registros Logs de Apache. En este caso, le aplicamos la plantilla common donde incluirá los principales paràmetros de los logs. Crearemos dos archivos, uno en el que el servidor almacena en el registro de acceso información sobre todas las peticiones que procesa.

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
Llegados a este punto podemos mencionar que la configuración de Apache no se lleva a cabo en un solo archivo, sino que ocurre a traves de un diseño donde se pueden agregar y modificar nuevos archivos.

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
  
  En nuestro caso tenemos los siguientes `IncludeOptional`, que cargan los modulos de configuración `*.conf` de los directorios indicados. Nosotros al crear un directorio personalizado para el vhost lo tenemos que inlcuir de esta manera:
  
  ![image](https://user-images.githubusercontent.com/73543470/167170043-dc062011-d1f8-4ba5-a2a1-05ade42c0a1f.png)

Además de el resto de includes genericos de Apache:
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
  
  Las diferentes reglas establecidas en los diferentes directorios són:
  - `Require`--> restringir o abrir el acceso a diferentes recursos de su servidor.
  - `AllowOverride`--> Se usa para decidir si el archivo `.htacces` puede anular la configuración si se coloca en el directorio del contenido.
- `FollowSymLinks` --> Afirmamos y permitimos que Apache siga los enlaces simbolicos del directorio.
- `-Index` --> Denegamos que un diretorio se pueda mostrar como una lista si no hay una pagina index.
 - `+MultiViews` --> Permite que si existe un archivo llamado configuration.php en la raiz siempre sea elegido aunque modifiques el archivo .htacces para que realize la busqueda en otro directorio.

### PHP
_____________
Es el componente que procesará el codigo permitiendonos asi ejecutar scripts, conectarnos a las bases de datos MariaDB para obtener información y entregar el contenido a el servidor web.

```sh
apt install php libapache2-mod-php phpmysql
```
A continuación modificaremos nuestro Apache ya que este ahora mismo 
 
### MARIA DB
_____________
Para realizar la instalación de este paquete debemos efectuar la siguiente comanda:
```sh
apt install mariadb-server
```

-  A continuación ejecutaremos un script de seguridad e MariaDB.
```sh
mysql_secure_installation
```

 NOLOSE DE MOMENTO, creo que apache literal configura y lleva a cabo la resolucion de la pagina por internet, y nginx lo hace a nivel de servidor y este acuta como proxy del host(?).
  
 
## 3. INSTALACIÓN CERTIFICADO SSL
El certificado SSL que he instalado en esta ocasión es Lets Encrypt. Ya que este es gratuito, ademas de autorenovable por tanto "infinito".
La funcion de este certificado es generar una clave publica para el dominio cosmosdesign.es que te identifique como administrador de tu dominio. Estas claves se generan a traves de la instalación y activación del certificado, y nos permitiran hacer conexiones cifradas entre usuarios y nuestro servidor.

#### SNAP, CORE Y CERTBOT
- El metodo de instalación que utilizaremos es **cerbot**, pero antes debemos tener instalado el complemento **snapd** que es un daemon necesario para administrar snaps(instantaneas). Recuerda presionar `YES`+ `ENTER` para instalar todas sus dependencias tambien.
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
Cuando ya haya finalizado la instalación tenemos que comprobar la configuración de apache ya que  Certbot necesita poder encontrar el Virtual Host en su configuración de apache para configurar automaticamente el SSL asi que previamente debemos tener hecho estos pasos "INSTALAR APACHE"

De todas maneras comprobaremos que tenemos `ServerName`configurado con el nombre del dominio en `/etc/apache2/sites-available/cosmosdesign.es.conf`
![image](https://user-images.githubusercontent.com/73543470/167049886-df606684-64c5-44d2-a955-482bf30764f6.png)

Con el siguiente comando nos fijaremos que no haya ningun error de sintaxix
```sh
apache2ctl configtest
```
Y recibirás un mensaje como este en caso de que todo sea correcto:
![image](https://user-images.githubusercontent.com/73543470/167050097-ae1360e0-0368-4d01-9bb8-4d23c05512c1.png)

explicar firewall complicado con iptables

### OBTENER CERTIFICADO SSL

Realizando la siguiente comanda instalaremos el certificado SSL, mediante `--apache` permitimos que certbot reconfigure apache y recargue la configuración cuando sea necesario.
Indicamos mediante las dos `-d` que queremos que el certificado sea valido para ambos DNS.
```sh
sudo certbot --apache -d cosmosdesign.es -d www.cosmosdeisng.es
```

En el caso de ser la primera vez que inicia cerbot en el servidor, este le pedira que ingreses una dirección de corre electronico y acepte los terminos del servicio.
A continuación certbot se comunicará cone l servidor Lets encrypt y ejecutara el desafio para verificar que eres tu el que controla el dominio por el cual se esta solicitando el certificado.

Una vez terminado el desafio y observado el mensaje final podemos acceder a nuestro navegador, introducir nuestra URL y observaremos que esta tendrá un candado y en mas información veremos el nombre del Lets Encrypt

![image](https://user-images.githubusercontent.com/73543470/167051490-5499d805-7c65-4ffb-b230-bd5a3200e868.png)

#### RENOVACIÓN AUTOMÁTICA
Para olvidarnos del certificado por completo podemos realizar ela siguiente comanda para que Certbot renueve el SSL cuando este vaya a caducar
```sh
certbot renew --dry-run
```

## 4. INSTALACIÓN NGINX
Cuando alguien hace una solicitud para abrir una página web, el navegador se comunica con el servidor de ese sitio web. Luego, el servidor busca los archivos solicitados para la página y se los envía al navegador.
Funcina como servidor proxy de correo electrónico SMPT, POP3, IMAP.

## 5. INSTALACIÓN POSTFIX + DOVECOT
A continuación configuraremos el servidor de correo Postfix MTA(transferencia),


## CREACIÓN Y CONFIGURACIÓN DEL SERVICIO DE HOSTING
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



## 4. INSTALACIÓN/CONFIGURACIÓN DE WORDPRESS
Previamente debemos tener instalado la pila LAMP y que nuestro dominio se encuetre bajo un certificado SSL. También necesitamos un domini, adquirido y un

  

### Crear BD y usuario en MARIADB
- 

### INSTALACIÓN DEL ENTORNO

### CONFIGURAR INTERFICIE WORDPRESS
Como los DNS todavia no se encuentran propagados he modificado mi archivo de host en Winodws para que mi PC apunte al dominio en cuestión con la IP asignada. Para así poder iniciar sesión en Wordpress y poder comenzar a adminstrarlo.

 _Si quieres saber en que punto de propagación se encuentran tus DNS detu dominio puedes utilizar www.whatsmydns.net ._
 
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

  Problemas extras!
  
  Yo me encontre el siguiente:
  Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.




