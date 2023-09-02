# Telematics
<p><code>Fundamentos de Telemática</code></p>
<p>Creado por <code>GncDev</code> para explicar los fundamentos de los <code>Sistemas de comunicaciones</code> en los cursos de telemática y redes de computadores.</p>

# Practica de laboratorio 01 - Caracterización

## Objetivos 

### Objetivo General
Proporcionar el conocimiento y generar las habilidades necesarias en la configuración y gestión de dispositivos de redes.

### Objetivos Específicos:
- Conocer los números necesarios para configurar y caracterizar los diferentes dispositivos de red. :+1: 

---
## 1. [Configurar el entorno de trabajo](#) ✔
1. Instalar [VSCode][1_1]
2. Instalar [Git][1_2]
3. Crear una cuenta en [github][1_3]
4. Crear un [repositorio nuevo][1_4] en Github llamado <code>Redes-dos</code>
5. Instalar la [extension de github][1_5] para VScode
6. Agregar <code>Usuario</code> y <code>Correo</code> globalmente para Git.
7. Cerrar carpeta y clonar el repositorio remoto desde VScode.
8. Crear una carpeta en el repositorio Redes-dos llamada <code>Laboratorio-uno</code>.


```bash
# Para agregar Usuario y Contraseña a GIT
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

[1_1]:https://code.visualstudio.com/download
[1_2]:https://git-scm.com/download/win
[1_3]:https://github.com/
[1_4]:https://github.com/new
[1_5]:https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github


## 2. [Preguntas reflexivas de ambientación](#) ✔

<ol type="a">
<li>¿Cual es la dirección de red y de broadcast de un host que tiene una ip 192.168.10.10/30?.</li>
<li>¿Que información se puede inferir de un host con la dirección 169.254.255.200/26?.</li>
<li>¿Cuantas sub-redes puede lograr con la mascara 172.16.0.0/22?.</li>
<li>¿Cuantos clientes puede tener la sub red 172.16.0.0/22?.</li>
<li>¿Que clase y tipo de dirección es 10.10.10.0/24?.</li>
</ol>


<li>Respuestas</li>

a.// Dirección de red: 192.168.10.8, Dirección de transmisión: 192.168.10.11

b.// La dirección IP 169.254.255.200/26 es una dirección IP de tipo APIPA (Automatic Private Internet Protocol Addressing) Esta dirección se utiliza cuando un dispositivo no puede obtener una dirección IP válida de un servidor DHCP y se autoconfigura mediante el protocolo de direccionamiento APIPA. La máscara de subred /26 indica que los primeros 26 bits de la dirección IP son la red y los últimos 6 bits son el host. Por lo tanto, la cantidad de hosts que se pueden conectar a esta red es de **62**. Sin embargo, no se puede inferir ninguna información adicional sobre el host con esta dirección IP.

c.// El subred 172.16.0.0/22 ​​utiliza una máscara de subred de 22 bits, lo que significa que hay 22 bits reservados para la parte de red y (32-22) = 10 bits para la parte de host. Por lo tanto, clientes posibles = 2^10-2 = 1024-2 = 1022

d.// primero debemos calcularlo utilizando la fórmula (2^n-2), donde "n" es el número de bits disponibles para la parte de host en la subred.
Por lo tanto en el caso de la subred 172.16.0.0/22, tienes 22 bits reservados para la parte de red y 32 - 22 = 10 bits para la parte de host, entonces tenemos, clientes posibles = 2^10-2 = 1024-2 = 1022

e.// Clase A privada : La dirección IP 10.0.0.0 a 10.255.255.255 se reserva para su uso en redes privadas y no se utiliza en Internet público. Las direcciones en el rango 10.0.0.0 a 10.255.255.255 son conocidas como direcciones IP de Clase A privada.

Tipo de dirección : La notación "/24" indica que se utiliza una máscara de subred de 24 bits. Esto significa que los primeros 24 bits se utilizan para la parte de red, y los


## 3. [Caracterización de los adaptadores](#) ✔
|Parámetro||Valor|
|--|:--:|--:|
|Número de adaptadores Físicos|-->|4|
|Número de adaptadores Virtuales|-->|3|
|Tipo de Adaptador principal|-->|Wi-fi|
|Fabricante del Adaptador principal|-->|Qualcomm Corporation|
|Código MAC del fabricante|-->|C8-FF-28|
|MAC|-->| C8-FF-28-CE-01-E3|

>Nota: Para obtener los parámetros de la red, usaremos los comandos [ipconfig][10], [ifconfig][8], [getmac][9].

## 4. [Caracterización de la red](#) ✔
|Parámetro|Valor|
|--|--:|
|__Subnet__| 192.168.1.0/24|
|IPv4|192.168.1.43|
|Subnet Mask decimal|24|
|Subnet Mask octetos|255.255.255.0|
|Número de direcciones de Host|254|
|Rango de direcciones de Host| 192.168.1.1-254|
|IP Broadcast|192.168.254.255|
|Server DHCP|192.168.254.254|
|Server DNS|8.8.8.8|

>Nota: Para obtener los parámetros de la red, usaremos el comando [ipconfig][10] o [ifconfig][8].


## 5. [Caracterización de la puerta de enlace](#) ✔
|Parámetro|Valor|
|--|--:|
|Número de Entradas en la tabla ARP |24|
|IPv4 Gateway|190.217.254.254|
|MAC Gateway|c4-70-0b-09-14-00|
|ISP|Lumen|
|[IP Publica][5]|190.217.68.59|
|[Sistema Autónomo][6]|AS3549|


>Nota: Para obtener los parámetros de la red, usaremos el comando [arp][11] y algún servicio web/HTTP como [cual-es-mi-ip.net][5], [ipinfo.io][6] o [asrank.caida.org][9_1].


## 6. [Retardo de la red](#) ✔
|Servidor|IP|Tiempo promedio/ms|
|--|--|--|
|DNS Google|8.8.8.8|87|
|DNS Cloudflare|1.1.1.1|53|
|OpenDNS|208.67.222.222|164|
|Alternate DNS|76.76.19.19|-|
|DNS Quad9|9.9.9.9|79|
|AdGuard DNS|94.140.14.14|197|

>Nota: Para calcular el retardo de la red, usaremos el protocolo ICMP/[ping][12] con al menos 10 paquetes.


## 7. [Capacidad del canal](#) ✔
|Servidor|Ping/ms|Down/MB|Up/MB|
|--|:--:|--:|--:|
|[speed test][1]|44|2.29|9.54|
|[Netflix][2]|1.8|35|47|
|[Claro][3]|32|2.0|9.6|
|[nperf][4]|6.7|93.6|54.98|

>Nota: Para calcular el retardo de la red, usaremos el protocolo HTTP via servicio WEB.


## 8. [Distancia desde el host](#) ✔
|Servidor|Ping/ms|Numero de Saltos|
|--|:--:|--:|
|google.com|82|11|
|GMail.com|304|11|
|YouTube.com|91|11|
|dns.google|-|-|
|aws.amazon.com|26|15|
|portal.azure.com|26|12|
|login.live.com|130|23|
|Facebook.com|94|13|
|c.ns.WhatsApp.net|151|12|
|claro.com.co|151|12|
|platzi.com|122|11|
|rappi.com.co|184|30|

>Nota: Para calcular el retardo de la red, usaremos el comando ICMP/[tracert][13].

## 9. [Diagrama de Red](#) ✔
- Realice un diagrama topológico de la red que le ofrece conectividad a internet.
- Incluya todos los detalles de la red de area local a la que se encuentra conectado.
- Incluya los saltos conocidos incluyendo el equipo de borde de su ISP.

>Nota: Para conocer el tamaño y la topología de la red, usaremos la información previa y la pagina [ASRank][9_1].

## 10. [Preguntas de conocimiento](#) ✔
1. ¿Cuál es el retardo esperado para tu red según la tecnología contratada?
1. ¿Coincide el retardo medido con el esperado para tu red según la tecnología contratada? ¿Por qué?
1. ¿Por qué varia la capacidad del canal en las distintas pruebas realizadas?
1. ¿Cuál de los servicios DNS es mejor para configurar mi LAN?
1. ¿Como podría medir la disponibilidad de ni conexión a internet?


[1]:https://www.speedtest.net/es
[2]:https://fast.com/es/#
[3]:http://speedtest.claro.net.co/
[4]:https://www.nperf.com/es/
[5]:https://www.cual-es-mi-ip.net/
[6]:https://ipinfo.io/

[9_1]:https://asrank.caida.org/

[8]:https://man7.org/linux/man-pages/man8/ifconfig.8.html
[9]:https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/getmac
[10]:https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/ipconfig
[11]:https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/arp
[12]:https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/ping
[13]:https://learn.microsoft.com/es-es/windows-server/administration/windows-commands/tracert


---
## Mas Recursos
- [Protocolo Ipv4](https://es.wikipedia.org/wiki/IPv4) (Wikipedia)
- [Direccionamiento IP](https://es.wikipedia.org/wiki/Direcci%C3%B3n_IP) (Wikipedia)
- [Calculadora IP](https://www.calculator.net/ip-subnet-calculator.html) (Wikipedia)

---
## Evaluación y rúbrica
- Fecha máximo entrega: 05 de Mayo de 2023
- Hora de entrega: 11:59pm	
- Nota máxima: 5.0 
- Número de actividades: 10
- Valor de cada actividad: 0.5
- Ponderación: 20%
- $\color{#DD69DD}{\text{...Carpe Diem}}$