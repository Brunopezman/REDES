# Preguntas de Examen de REDES

## Bloque 1: Fundamentos y Transmisión de Datos
1. **Modelo de Capas y Encapsulación**

    - ***1.1 Mencione y describa brevemente las siete (7) capas del Modelo OSI.***
    
    __CAPA 7: Aplicacion -->__ Interfaz con el usuario. Proporciona servicios de red

    __CAPA 6: Presentacion -->__ Encargada del formato, compresion y del cifrado de datos.

    __CAPA 5: Sesion -->__ Administra el dialogo entre dispositivos. Gestiona el inicio, mantenimiento y fin de la sesion.

    __CAPA 4: Transporte -->__ Asegura que los datos lleguen completos y en orden con control de flujo y deteccion de errores.

    __CAPA 3: Red -->__ Direccionamiento y seleccion de ruta.

    __CAPA 2: Enlace de datos ->__ Transmicion segura entre dispositivos de la misma red local. Gestiona direcciones fisicas, control de flujo y organizacion en tramas.

    __CAPA 1: Fisica -->__ Transmicion y recepcion de bits por el medio fisico (cables, fibra, radio frecuencia)

    - ***1.2 Explique el modelo TCP/IP y diferencielo del modelo OSI***

    __Capa de Aplicacion__: Servicios de red para el usuario. Protocolos: HTTP, FTP, SMTP, DNS

    __Capa de Transporte__: Entrega datos de extremo a extremo. Protocolos: TCP, UDP

    __Capa de red__: Direccionamiento logico y enrutamiento (protocolo IP)

    __Capa de acceso a red__: Incluye funciones fisicas y de enlace de datos. Protocolos: Ethernet, Token Ring, ATM, FR

    El modelo OSI es teorico y pedagogico mientras que el modelo TCP/IP refleja la pila practica de internet.

    - ***1.3 Explique el proceso de encapsulación que ocurre cuando un dato viaja desde la capa de Aplicación hasta la capa Física en el modelo TCP/IP. ¿Cómo se llama la unidad de datos en la capa de Transporte (Capa 4)? ¿Y en la capa de Red (Capa 3)?***

    El proceso de encapsulacion consiste en añadir informacion de control (encabezados y, a veces, una cola) a la Unidad de Datos de Protocolo (PDU) de la capa superior, a medida que la información viaja descendiendo en el modelo de capas, desde la Capa de Aplicación hasta la Capa Física.

    - La capa de aplicacion pasa los Datos a la capa inferior.
    - La Capa de Transporte le añade un encabezado y la PDU resultante se denomina Segmento (si usa TCP) o Datagrama (si usa UDP).
    - La Capa de Red le añade el encabezado IP y la PDU resultante se denomina Paquete.
    - La Capa de acceso a red le añade un encabezado y una cola, y la PDU resultante se denomina Trama. Mediante funciones fisicas se convierte la trama en Bits para su transmisión por el medio físico.


2. **Teorema de Nyquist y Transmisión**

    - ***2.1 Enuncie el Teorema de Nyquist. ¿Para qué se utiliza en la transmisión de datos?***

    El teorema de Nyquist establece que para reconstruir una señal analóligca sin pérdidas, la frecuencia de muestreo debe ser, al menos, el doble de la frecuencia mas alta de la señal --> FM >= 2FS

    - ***2.2 Si una señal de voz analógica tiene una frecuencia máxima (FS) de 4 kHz, ¿cuál es la frecuencia de muestreo (FM) mínima requerida para digitalizar la señal sin perder información?***

    Es de 8 kHz --> 8 kHz >= 2 * 4 kHz 


3. **Medios Físicos: Fibra Óptica**

    - ***Compare las fibras ópticas Singlemode (monomodo) y Multimode (multimodo) en los siguientes aspectos:***
        - Diámetro del núcleo
        - Distancia típica de uso (corta/larga)
        - Mecanismo de propagación de la luz

    La monomodo es utilizada para largas distancias (WAN/Backbone), usa un solo modo de propagación que reduce la dispersión modal a diferencia de la multimodo que es usada para distancias mas cortas (Data Center/LAN) y permite multiples modos de propagacion, lo que genera más dispersión y pérdida. El diametro del nucleo de una multimodo es de 50/62 micrómetros mientras que el de una monomodo es de 9 micrómetros. Generalmente, para monomodo los cables son más económicos, pero requiere equipos láser más precisos (caros) y con las multimodo el cable es más caro, pero usa equipos LED/VCSEL más económicos.

    - ***Que son las FO OM4 y OM5***

    Son estandares mejoradas de la fibra multimodo que permiten mayores velocidades y alcances en los entornos de data center. OM4 esta diseñada para 10, 40, 100 Gb siendo el estandar de DC de gran escala. OM5 habilita la tecnologia SWDM que permite mltiplicar la capacidad de un par de fibras, permitiendo correr 400 GbE sobre pocos hilos.



## Bloque 2: Infraestructura y Arquitecturas
4. **Arquitectura de Data Centers**

    ***- 4.1 Explique las diferencias principales entre la Arquitectura de 3 Capas (Tradicional) y la arquitectura Spine & Leaf usada en Data Centers modernos.***

    Tradicional (Core/Agregado/Acceso): Tráfico norte-sur (cliente-servidor) y menos eficiente para cargas virtualizadas.

    Spine & Leaf: menor latencia y mayor ancho de banda para tráfico este-oeste; escalable y más resiliente. 

    ***- 4.2 En el contexto de estas arquitecturas, explique el concepto de tráfico Norte-Sur y tráfico Este-Oeste, e indique cuál de las dos arquitecturas optimiza mejor cada flujo.***

    El trafico Norte-Sur es aquel que entra o sale del DC, entre un clente externo y un servidor interno. Fluye verticalmente entre las capas de Acceso, Agregación y Core. La arquitectura que lo optimiza es la tradicional por su diseño de ruteo centralizado.

    El trafico Este-Oeste es aquel que fluye internamente entre los servidores (entre racks) dentro del Data Center. Es común en entornos virtualizados o arquitecturas de microservicios (ej. un servidor web comunicándose con un servidor de bases de datos). La arquitectura que lo optimiza es pine & Leaf, que ofrece una baja latencia y un gran ancho de banda no bloqueante para las comunicaciones internas.


5. **Par Trenzado y Crosstalk**

    ***¿Cuál es el principal objetivo de trenzar los pares de hilos de cobre en un cable UTP (Unshielded Twisted Pair)?Explique brevemente qué es la Diafonía (Crosstalk) y cómo el trenzado ayuda a mitigarla.***

    El principal objetivo es minimizar la interferencia entre señales que viajan por diferentes pares dentro del mismo cable, también conocida como crosstalk o diafonía. Al trenzar los hilos de cobre generamos una estructura que mejora la proteccion contra interferencias.


6. **NFV y la Evolución de las Redes**

    - ***6.1 Defina NFV (Network Function Virtualization) y mencione dos (2) beneficios clave para los proveedores de servicio.***
    
    NFV permite que funciones de red como fireballs, routers, NATs, Load Balancers puedan ejecutarse como software sobre hardware genérico (COTS), en vez de requerir dispositivos dedicados. A un proveedor de servicio le trae beneficios como facil integracion con la nube y automatización de despliegues.

    - ***6.2 ¿Qué es MANO en el contexto de NFV y cuáles son los tres (3) niveles principales de su arquitectura?***

    En el contexto de NFV, MANO significa Management and Orchestration. Los 3 niveles principales de su arquitectura son:
    - NFVO (NFV Orchestrator) --> Gestiona el ciclo de vida de los servicios de red
    - VNFM (VNF Manager) --> Adminsitra funciones virtualizadas
    - VIM (Virtual Infrastructure Manager) --> Controla la infraestructura

    - ***6.3 Que es virtualizacion 2.0 y como influye NFV***

    Virtualizacion 2.0 incluye maquinas virtuales sobre hipervisores (KVM, VMware, Hyper-V), evolucion hacia contenedores y microservicios, orquestacion en nubes publicas/privadas (kubernetes, OpenStack) que permite automatizacion, rapidez y escalabilidad.

    NFV esta directamente relacionado con esto dado que permite desplegar aplicaciones de forma rapida, escalable y atomatizada con los siguientes elementos:

    - VNFs de funciones que antes eran firewalls, routers, NAT, DPI
    - Ejecucion de harware generico COTS, administrado por orquestados (MANO)
    - Reduccion de capex/opex y agilidad en la creacion de servicios.



## Bloque 3: Protocolos y Enrutamiento

7. **Enrutamiento Estático vs. Dinámico**

    - ***7.1 Establezca las diferencias fundamentales entre el Ruteo Estático y el Ruteo Dinámico en términos de administración, flexibilidad y escalabilidad. Mencione un protocolo de ruteo dinámico de tipo Link-State y otro de tipo Vector Distancia.***

    En el ruteo estatico, las rutas se ingresan manualmente en la tabla de enrutamiento mientras que en el ruteo dinamico se utilizan protocolos de enrutamiento para descuburir las rutas. El estatico es mas simple pero menos flexible en comparacion con el dinamico dado que este ultimo es mas escalable y se adapta a cambios de red.

    - Protocolo de Ruteo Link-State: OSPF (Open Shortest Path First).
    - Protocolo de Ruteo Vector Distancia: BGP(Border Gateway Protocol).

    - ***7.2 Explique BGP y de un ejemplo***

    BGP es un protocolo de ruteo dinamico de tipo Path Vector utilizado para intercambiar informacion de rutas entre diferenes Sistemas Autonomos (AS). Cada ISP o gran organizacion es un AS y BGP intercambia las redes que cada uno puede alcanzar.

    BGP permite aplicar políticas como elegirt por donde sale o entra el trafico, balancear, filtrar anuncios. Usa atributos como AS-PATH, Local Preference, MED y Communities para seleccionar rutas.

    EJ: Un banco (AS 65010) se conecta a dos ISPs:
    - ISP-A (AS 1234)
    - ISP-B (AS 5678)

    El banco anuncia su prefijo 200.3.100.0/24 a ambos ISPS mediante eBGP. Configura una Local Preference mayor para rutas aprendidas por ISP-A, haciendo que la salida por defecto sea ese proveedor. Mediante manipulacion del AS-PATH o communites puede influir en qué ISP entra el trafico desde internet hacia cada prefijo. De esa manera, observamos como BGP permite controlar como se enruta el trafico global de la organizacion.


8. **MPLS (Multiprotocol Label Switching)**

    ***Describa qué es MPLS y cómo difiere del enrutamiento IP tradicional. ¿Cuál es la función principal de las etiquetas (labels)? ¿Cuál es una aplicación clave de MPLS en redes empresariales (ej. VPNs)?***

    MPLS es una tecnologia de transporte de datos en redes que usa etiquetas para enrutar, en lugar de direcciones IP completas. Su funcion principal es permitir la conmutación y el reenvío rápido en el core de la red basado en la etiqueta en lugar de realizar una búsqueda compleja en la tabla de ruteo IP en cada salto. Es utilizada principalmente por los Service Providers como medio de transporte WAN sin rutear con IP. Es muy usado en empresas con multiples sedes dada la seguridad de las VPN corporativas L2 y L3, trafico QoS (voz, video, datos críticos). Los principales protocolos asociados son:

    - LDP: Distribucion y asociacion de etiquetas a prefijos IP entre routers.
    - RSVP-TE: Establece LSPs coon reserva de recursos y camino explícito.
    - OSPF/IS-IS: Protocolos de ruteo internos que proveen la topología sobre la que se construyen los LSP.
    - MP-BGP: Extensión de BGP usada para implementar VPN L3 sobre MPLS.


9. **Protocolos capa 2**

    ***De los protocolos de Capa 2 o 3, como X.25 y Frame Relay, ¿cuál era la principal limitación que los hacía ineficientes para el tráfico en tiempo real, lo que llevó a su reemplazo por tecnologías más modernas como Ethernet o MPLS?***

    La principal limitacion fue la generacion de sobrecarga de red (overhead) y la falta de eficiencia para trafico en tiempo real por parte de la X.25. Luego fue reemplazada por FR para tráfico por ráfagas (ej: cajeros automáticos) pero esta ultima ya no se usa comercialmente.

    ***Explicar los protocolos restantes**

    ATM: Tecnología de conmutación y multiplexación de alta velocidad que fue desarrollada para la transmisión de datos, voz y video de forma simultánea (convergencia) en redes de área extensa (WAN). Permite conmutar celdas fijas de 53 bytes, pensada para transportar voz, video y datos con diferentes clases de QoS (CBR, VBR, ABR, UBR). Fue tecnologia de backbone previa a IP/MPLS.

    Metro Ethernet: Red metropolitana de capa 2 (MAN) basada en tecnología Ethernet. Interconecta redes LAN distribuidas geográficamente. Permite tráfico de voz, video y datos manejando trafico sensible a jitter, como Telefonía IP o Video IP.

10. **Defina brevemente los siguientes términos:**

    ***VLAN (Virtual LAN):***
    Redes virtuales que particionan una LAN física en múltiples redes virtuales independientes, reduciendo congestión y aislando tráfico.

    ***BGP (Border Gateway Protocol):***
    Protocolo de enrutamiento dinamico utilizado para intercambiar informacion entre sistemas autonomos.

    ***PAT (Port Address Translation):***
    Traduccion de direcciones privadas a publicas, many-to-one, tıpico hogar/empresa

    ***QoS (Quality of Service):***
    Caracteristica moderna de los servicios que permite priorizar ciertos tipos de trafico, como llamadas.



## Bloque 4: Capa de Enlace, Transmisión y Multiplexación

11. **Direccionamiento y Segmentación de Capa 2** 

    - ***11.1 Explique la diferencia fundamental en función y ámbito de uso entre una dirección MAC y una dirección IP.*** 

    La direccion MAC es la __Identificación física__ del dispositivo de hardware para el acceso al medio físico (Ethernet, Wi-Fi). Se usa para la entrega local de datos. Solo es relevante dentro del mismo segmento de red (LAN). Se cambia en cada salto de router o subred.

    La direccion IP es la __Identificación lógica__ de la red y el host para el enrutamiento. Se usa para la entrega de extremo a extremo (origen a destino final). Relevante a lo largo de toda la ruta de Internet. Se mantiene inmutable desde el origen hasta el destino final.

    - ***11.2 ¿Cuál es el propósito principal de implementar VLANs (Virtual LANs) en una red conmutada (switched)? ¿Qué estándar de IEEE se utiliza comúnmente para etiquetar las tramas Ethernet para la conmutación entre switches?***

    El proposito principal de implementar VLANs es reducir broadcasts y congestión mediante la particion de una LAN fisica en multiples redes virtuales; mejorando rendimiento y seguridad. El estándar de IEEE utilizado para etiquetar las tramas Ethernet y permitir que los switches diferencien el tráfico de distintas VLANs a través de un enlace troncal (trunk) es IEEE 802.1Q. Este protocolo inserta un campo de etiqueta (tag) en la cabecera de la trama Ethernet original, indicando a qué VLAN pertenece.


12. **Multiplexación en Redes. Defina los tres (3) tipos de multiplexación más comunes, indicando el medio físico o la variable que utilizan para combinar múltiples señales en un único canal:**

- ***FDM (Frequency Division Multiplexing): ***
En FDM cada señal ocupa una banda distinta del espectro. Es muy comun su uso en radio FM. 

- ***TDM (Time Division Multiplexing): ***
En TDM se divide la señal en ranuras de tiempo. En su version sincronica cada origen tiene un slot fijo, aunque no tenga datos para enviar. En su version asincrona, los slots se asignan dinamicamente segun disponibilidad.

- ***WDM (Wavelength Division Multiplexing): ***
En WDM se parten longitudes de onda. Es usada en fibra optica y es base de las redes opticas modernas.


13. **NAT y la Escasez de Direcciones IP**

    - ***13.1 Explique qué es PAT (Port Address Translation) y cómo difiere del NAT Estático y NAT Dinámico.***

    PAT es una técnica que traduce múltiples direcciones IP privadas internas a una única dirección IP pública, utilizando el Número de Puerto de Origen para distinguir las conexiones de cada dispositivo interno. Difiere de las anteriores porque utiliza puertos para permitir que miles de dispositivos compartan la misma IP pública. Es la forma más común de NAT en hogares y empresas. 
    
    En NAT estatico se usa a una IP pública por cada IP privada, fija y dedicada. Se usa típicamente para publicar servidores. En NAT Dinamico las IPs privadas utilizan un pool o grupo de IPs públicas. La traducción es 1:1, pero temporal y limitada por el tamaño del pool.

    - ***13.2 ¿Cómo resolvió (o al menos mitigó significativamente) el uso masivo de PAT en hogares y empresas la escasez de direcciones IPv4 en Internet?***

    El uso masivo de PAT mitigó la escasez de direcciones IPv4 al permitir que miles de dispositivos en redes privadas compartieran una única dirección IPv4 pública globalmente ruteable. Esto multiplicó la cantidad de dispositivos que podían acceder a Internet sin la necesidad de asignar una dirección pública a cada uno, posponiendo por años el agotamiento total de las direcciones IPv4.



## Bloque 5: Arquitecturas Avanzadas y Convergencia

14. **SDN (Software Defined Networking)**

    - ***14.1 Defina SDN (Software Defined Networking). ¿Cuál es el principio fundamental que separa SDN de las arquitecturas de red tradicionales?***

    SDN es una tecnologia con el proposito de separar plano de control y datos. Su enfoque es el control centralizado y programable.

    - ***14.2 Explique brevemente cómo se complementan SDN y NFV para ofrecer mayor flexibilidad y automatización en redes modernas.***

    NFV proporciona la estructura virtualizada. Convierte funciones de red específicas (como firewalls, routers o load balancers) de hardware dedicado a software que se ejecutan en servidores genéricos (COTS). 
    
    SDN aporta la inteligencia y la programación. El controlador SDN es el "cerebro" centralizado que define y programa dinámicamente las rutas, las políticas y el flujo de tráfico hacia, desde o a través de esas NFVs, permitiendo la automatización de los servicios de red.


15. **Infraestructura y PoE**

    - ***15.1 Defina PoE (Power over Ethernet) y mencione dos (2) dispositivos comunes de borde de red (Edge Devices) que se benefician directamente de esta tecnología.*** 

    Power over Ethernet es una tecnologia que permite transmitir datos y energia electrica por el mismo cable ethernet. Un ejemplo de dispositivos que se benefician con esta tecnologia son los telefonos VoIP y las camaras simples.

    - ***15.2 ¿Qué significa la clasificación CAT 6A en el cableado de par trenzado UTP/STP, y cuál es el principal beneficio que ofrece en comparación con CAT 5e o CAT 6?***

    La clasificación CAT 6A (Category 6 Augmented) en el cableado de par trenzado UTP/STP es una especificación de rendimiento para cables que significa que pueden operar a una frecuencia de hasta 500 MHz.

    El principal beneficio que ofrece respecto a CAT 5e (100 MHz) y CAT 6 (250 MHz) es que soporta la velocidad de 10 Gigabit Ethernet en toda la distancia estándar de cableado estructurado, es decir, 100 metros completos. 



## Bloque 6: HAMMING

### Ejemplo 1: Quiero mandar el mensaje 00101 codificado.

Sabemos por enunciado que M = 5

***Se agregaran K bits, tal que K sea el menor que cumpla 2^K >= M + K + 1***

=> 2 ^3 >= 5 + 3 + 1 => 8 >= 9 ERROR

=> 2^4 >= 5 + 4 + 1 => 16 >= 10 OK

***Entonces, los Ki ocuparan las posiciones K1 = 2^0, k2 = 2^1, K4 = 2^2, K8 = 2^3***

Obtenemos K1 K2 M3 K4 M5 M6 M7 K8 M9 = K1 K2 0 K4 0 1 0 K8 1

***La suma de los subindices de los M, nos deben dar el valor del subindice de K***

M3 = K1 + K2 ; M5 = K1 + K4 ; M6 = K2 + K4 ; M7 = K1 + K2 + K4 ; M9 = K1 + K8

Entonces observo donde se encuentra cada K para saber cuantos indices cubre:

K1 cubre M3, M5, M7
K2 cubre M3, M6, M7
K4 cubre M5, M6, M7
K8 cubre M9

***Usamos paridad par: Cada bit de control debe hacer par el numero de 1s en las posiciones que cubre***

K1 + 0 + 0 + 0 + 1 = 0 => K1 = 1

K2 + 0 + 1 + 0 = 0 => K2 = 1 

K4 + 0 + 1 + 0 = 0 => K4 = 1

K8 + 1 = 0 => K8 = 1

=> Codigo valido = 1 1 0 1 0 1 0 1 1

### Ejemplo 2: Supongamos que transmito el código 1101001 y se recibe el 1101011, cambió el M6; CÓMO SE DETECTA ? Mediante la paridad de los subcódigos.

P1 = 1 xor 0 xor 0 xor 1 = 0 

P2 = 1 xor 0 xor 1 xor 1 = 1

P4 = 1 xor 0 xor 1 xor 1 = 1

(P4, P2, P1) = (1, 1, 0) ==> P4 y P2 : 2 + 4 = 6 ==> El bit invertido es el M6

==> Si hubiera sido un Ki en vez de un Mi, se descarta.



## Bloque 7: Conectividad y tolerancia a fallas

***Explicar los conceptos involucrados en este bloque, que protocolos intervienen***

La conectividad es la capacidad que tienen dos o mas dispositivos o nodos dentro de una red para intercambiar informacion con exito y de manera oportuna. El objetivo de la conectividad en una red moderna es el principio any-to-any, donde cualquier nodo puede comunicarse con cualquier otro.

En terminos tecnicos, la conectividad abarca dos aspectos clave:

- Existencia de la ruta fisica y logica: Camino ininterrumpido (cables, FO o enlaces inalambricos) entre origen y destino.
- Protocolos operativos: Que los dispositivos intermedios (principalmente routers y switches) conozcan las direcciones y las reglas para reenviar el trafico correctamente:

    - capa 2: Uso de direcciones MAC y protocolos como ARP para la entrega de un segmento local
    - capa 3: Uso de direcciones IP y protocolos de enrutamiento para determinar la mejor ruta a traves de redes remotas.

La tolerancia a fallas es la capacidad de la red para continuar operando y brindando servicio de forma ininterrumpida, a pesar de que uno o mas de sus componentes principales (hardware, links o softwares) experimenten una falla. Se logra mediante:

- Redundancia de enlaces y equipos
- protocolos de ruteo dinamico (OSPF, IS-IS, BGP)
- Mecanismos especificios de recuperacion rapida (HSRP/VRRP)



## Bloque 8: QoS

***Comparar los protocolos que soportan QoS para transmicion de voz***

La transmicion de voz exige: Baja latencia (<150 ms), jitter bajo y minima perdida de paquetes.

__Mecanismos/Protocolos__
- DSCP: Marca los paquetes de voz (VoIP) con el valor EF
- LLQ: Asigna a los paquetes de voz marcados con EF una cola de prioridad estricta.
- MPLS: Mapea el valos DSCP al campo EXP de la etiqueta MPLS para mantener la prioridad en toda la red troncal del ISP



## Bloque 9: Datagrama IP / TCP / UDP

***Como se define la internet a nivel de red y que clases de direcciones IP existen?***

A nivel de red la Internet puede definirse como un conjunto de redes o sistemas autónomos conectados entre sí que utilizan el protocolo de red IP. IP es una red de datagramas, no orientada a conexión, con servicio ‘best effort’, es decir no ofrece calidad de servicio o QoS (Quality of Service). 

En una red IP la información viaja en datagramas IP que tienen dos partes: cabecera y texto. Esto incluye tanto el intercambio a nivel de transporte por TCP y UDP como cualquier información de control que tenga que intercambiarse, por ejemplo, para ruteo dinámico, mensajes de error, etc.

Existen 5 clases de direcciones IP:
- CLASE A – SOPORTA GRANDES REDES EN INTERNET
- CLASE B – SOPORTA REDES EN INTERNET MODERADAS
- CLASE C - SOPORTA REDES PEQUEÑAS
- CLASE D - SOPORTA REDES MULTICAST
- CLASE E - SOLO EXPERIMENTAL

***Diferencias entre protocolo TCP y UDP***

| Factor | TCP | UDP | 
|------- |-----|-----|
| Tipo de conexión | Requiere una conexión establecida antes de transmitir datos | No se necesita conexión para iniciar y finalizar una transferencia de datos
| Secuencia de datos | Puede secuenciar datos (enviar en un orden específico) | No puede secuenciar y ordenar datos |
| Retransmisión de datos | Puede transmitir datos si no llegan los paquetes | Sin transmisión de datos. Los datos perdidos no se pueden recuperar |
| Entrega | Garantizada | No garantizada |
| Velocidad | Lenta, pero entrega los datos completos | Rapida, pero riesgo de que se entreguen datos incompletos |