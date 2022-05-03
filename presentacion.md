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
-
-
-
-

## 1. CREACIÓN Y INSTALACIÓN DE LOS SERVICIOS EN EL CLOUD
En primer lugar hemos procedido a contratar el cloud a una empresa externa, en este caso se trata de SW Hosting. Actualmente trabajo allí, ese fue el motivo principal
que me impulsó a tomar servicios con ellos.
El cloud por el que me decidí se trata de un Debian Buster v.10, en el cual he instalado los siguientes servicios que son imprescindibles para el correcto funcionamiento del servicio de Hosting Web.

Los pasos de la instalación de los diferentes servicios son:


### INSTALACIÓN DNS BIND

### INSTALACIÓN PHP

### INSTALACIÓN MARIA DB

### INSTALACIÓN APACHE2

### INSTALACIÓN NGINX

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


