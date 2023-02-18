# Laboratorio 1
## Ivan Gutierrez, Hector Diaz, Juan Deutsch

El presente documento presentará el desarrollo del laboratorio 1 de la asignatura Administración de redes, cuyo objetivo es construir redes LAN-WAN basadas en IPv4 utilizando subnetting-VLSM, Reconocer y  configurar el  protocolo  de  enrutamiento EIGRP/OSPF en  las  interfaces  requeridas  para  el enrutamiento de paquetes IP dentro las redes WAN. Así como simular y analizar el flujo de datos a través de la red empresarial.

#### Procedimiento:

En esta parte del procedimiento vamos a explicarlo en 4 diferentes partes y es el como organizamos la topología: Internet, DMZ, intranet BOG e Intranet MAD.

##### Internet:
Frente a la configuración de la parte de routers, se utilizó el protocolo de OSPF, iniciando con la configuración de los seriales cada cable con sus interfaces de manera que tengan la misma ip para que tengan una comunicación positiva, luego se procedió a configurar el OSPF dándole una dirección IP y remplazando la máscara de subred por la WildCard, que es lo contrario a la máscara de subred, para verificar el funcionamiento completo del protocolo se usó el comando show ip route ospf.


La configuración del protocolo OSPF se llevó a cabo de la siguiente manera: primero, se asignó una dirección IP a OSPF y se sustituyó la máscara de subred por la Wildcard. La Wildcard se utiliza para indicar qué parte de la dirección IP se debe ignorar durante el enrutamiento y es crucial para garantizar que la información de enrutamiento se envíe adecuadamente a través de la red. Por último, se utilizó el comando "show ip route ospf" para verificar el correcto funcionamiento del protocolo y comprobar que la tabla de enrutamiento muestre la mejor ruta para cada destino en la red.


Además, utilizamos el protocolo OSPF porque uno de sus objetivos principales es mejorar la eficiencia del enrutamiento en una red, permitiendo que los dispositivos seleccionen la ruta más rápida y fiable entre ellos. Para lograr esto, OSPF utiliza un algoritmo de enrutamiento basado en estado de enlace (LSA, Link State Algorithm) que permite a los dispositivos intercambiar información de topología de red actualizada, y calcular la ruta más corta y óptima entre dos puntos en función de esta información.

![image](https://user-images.githubusercontent.com/93561095/219804218-84c5a7e6-973c-4b86-bb42-264ce4958be9.png)

##### DMZ e INTRANET BOG:
Frente a la configuración del DMZ contestamos unas preguntas para guiarnos entre estas estaban: ¿Cuántos subnets necesitamos?, ¿Cuántos hosts se necesitan?, ¿ Que dispositivos/interfaces hacen parte de la subred?, ¿ Que partes de la red son públicas o privadas?. Después de esto, se realizan las configuraciones básicas a los diferentes switches que se encuentran entre el DMZ y la intranet BOG. Asimismo realizamos una tabla donde se evidencia el dispositivo, interfaz, Direccion IP, WildCard, Mascara de subred y puerta de enlace.

![image](https://user-images.githubusercontent.com/93561095/219804323-ccf55535-a646-4eb8-9fd9-dd2230c3b635.png)

La configuración se resume en qué hay dos servidores los cuales uno es para el servidor web, dónde se está alojando la página y la otra el DNS dónde se está alojando la direccion IP de la misma página web, el ISP_BOG se está encargando de ser parte de la comunicación de routers de la OSPF por el lado izquierdo de la topología. Asimismo, El servidor DNS es el encargado de almacenar la dirección IP del servidor web y proporcionar esta información a los clientes que desean acceder al sitio web. Los clientes envían una solicitud de DNS al servidor DNS, que responde con la dirección IP del servidor web correspondiente.

![image](https://user-images.githubusercontent.com/93561095/219817717-180130c2-2006-472b-b321-1de625808c25.png)

##### Intranet MAD:
En esta parte en teoría era la misma que el Intranet BOG ya que nos encontrábamos con una red compuesta por switches y pc’s. Por lo que la configuración era la de configurar los switches de manera normal sin embargo aquí los pc se configuraron para que tuvieran direcciones estáticas. Todo esto con el fin de que se pudiera conectar sin problema a los servidores que habíamos configurado antes y que se observaba que se ejecutaban de manera correcta.

![image](https://user-images.githubusercontent.com/93561095/219804379-9cd523e3-b028-4b48-b5b8-b685b8b489b7.png)

![image](https://user-images.githubusercontent.com/93561095/219817706-ddf558f3-64a6-4f79-816b-84f3473b4d4a.png)


##### Analisis:

![image](https://user-images.githubusercontent.com/93561095/219819206-f9f41e99-f247-470c-adb6-fc93a2dc4fb8.png)
![image](https://user-images.githubusercontent.com/93561095/219819213-3d218b39-a89d-4a8f-9c0a-c80a88553b68.png)
![image](https://user-images.githubusercontent.com/93561095/219819221-150771d6-0470-4cd6-bdf8-ae92c7c98677.png)
![image](https://user-images.githubusercontent.com/93561095/219819228-1c9129b5-860e-44d3-83d6-5e3201dc58f0.png)
![image](https://user-images.githubusercontent.com/93561095/219819235-e3bec1e8-470d-4ea8-8768-eafdcd8c38b0.png)
![image](https://user-images.githubusercontent.com/93561095/219819242-82407be8-e9ef-4e5e-8792-4dcfd675827f.png)
![image](https://user-images.githubusercontent.com/93561095/219819247-8590b54b-a977-423a-8125-13b89963c2e0.png)


##### Retos:
En el desarrollo del laboratorio nos encontramos con diversos retos entre estos el que mas se nos complico fue el de especificar el OSPF debido a que era un protocolo nuevo y que no sabíamos implementar. Esto nos conllevo a una búsqueda de videos y documentos para saber el como implementarlo de manera correcta debido a que había puntos donde lo implementábamos, pero ocurría un error en la conexión.

##### Conclusiones:
Una conclusión a la que llegamos mientras realizábamos el laboratorio fue el como enrutar paquetes entre la red y el internet y es de la siguiente manera Cuando un paquete sale de una red empresarial y está destinado a Internet, se reenvía a una puerta de enlace predeterminada. La puerta de enlace predeterminada es típicamente un router que está conectado a Internet y actúa como el punto de entrada para todos los paquetes que salen de la red empresarial. La puerta de enlace predeterminada realiza las mismas funciones de enrutamiento que cualquier otro router y reenvía el paquete al siguiente salto en su camino hacia su destino final. 
Finalmente, el proceso de enrutamiento se puede realizar de dos maneras, ya sea mediante rutas estáticas o rutas dinámicas. Por un lado, las rutas estáticas son manuales y deben ser actualizadas del mismo modo, mientras que las rutas dinámicas se actualizan en tiempo real y son más capaces de escoger un mejor camino para enviar los paquetes ya que tienen en cuenta muchos más criterios. Un ejemplo de protocolos de enrutamiento es: RIP, EIGRP y OSPF.

##### Link del video explicatorio:
https://youtu.be/rmbGNAsxYTc
##### Archivo .txt con las configuraciones:
[Configs_de_Lab_1.txt](https://github.com/Hdiaz0224/Lab1/files/10772414/Configs_de_Lab_1.txt)

##### Referencias:
Cisco. "Configuring IP Addressing and IP Services Features". Cisco. https://www.cisco.com/c/en/us/td/docs/routers/access/800M/software/800MSCG/IP_IP_Services.html?bookSearch=true (accedido el 16 de febrero de 2023).

Cisco. "Configure and Filter IP Access Lists". Cisco. https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html#req (accedido el 16 de febrero de 2023).
