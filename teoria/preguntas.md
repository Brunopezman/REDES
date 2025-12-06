# Preguntas de Examen de REDES

## Bloque 1: Fundamentos y Transmisión de Datos
1. **Modelo de Capas y Encapsulación**
    - ***1.1 Mencione y describa brevemente las siete (7) capas del Modelo OSI.***
    
    CAPA 7: Aplicacion --> Interfaz con el usuario. Proporciona servicios de red

    CAPA 6: Presentacion--> Encargada del formato, compresion y formato.

    CAPA 5: Sesion --> Administra el dialogo entre dispositivos. Gestiona el inicio, mantenimiento y fin de la sesion.

    CAPA 4: Transporte --> Asegura que los datos lleguen completos y en orden con control de flujo y deteccion de errores.

    CAPA 3: Red --> Direccionamiento y seleccion de ruta.

    CAPA 2: Enlace de datos -> Transmicion segura entre dispositivos de la misma red local. Gestiona direcciones fisicas, control de flujo y organizacion en tramas.

    CAPA 1: Fisica --> Transmicion y recepcion de bits por el medio fisico (cables, fibra, radio frecuencia)

    - ***1.2 Explique el proceso de encapsulación que ocurre cuando un dato viaja desde la capa de Aplicación hasta la capa Física en el modelo TCP/IP. ¿Cómo se llama la unidad de datos en la capa de Transporte (Capa 4)? ¿Y en la capa de Red (Capa 3)?***

    El proceso de encapsulacion consiste en añadir informacion de control (encabezados y, a veces, una cola) a la a la Unidad de Datos de Protocolo (PDU) de la capa superior, a medida que la información viaja descendiendo en el modelo de capas, desde la Capa de Aplicación hasta la Capa Física.

    - La capa de aplicacion (L7) pasa los Datos a la capa inferior.
    - La Capa de Transporte (L4) le añade un encabezado y la PDU resultante se denomina Segmento (si usa TCP) o Datagrama (si usa UDP).
    - La Capa de Red (L3) le añade el encabezado IP y la PDU resultante se denomina Paquete.
    - La Capa de Enlace de Datos (L2) le añade un encabezado y una cola, y la PDU resultante se denomina Trama.
    - La Capa Física (L1) convierte la trama en Bits para su transmisión por el medio físico.

2. **Teorema de Nyquist y Transmisión**

    - ***2.1 Enuncie el Teorema de Nyquist. ¿Para qué se utiliza en la transmisión de datos?***

    El teorema de Nyquist establece que hay que para reconstruir una señal analóligca sin pérdidas, la frecuencia de muestreo debe ser, al menos, el doble de la frecuencia mas alta de la señal --> FM >= 2FS

    - ***2.2 Si una señal de voz analógica tiene una frecuencia máxima (FS) de 4 kHz, ¿cuál es la frecuencia de muestreo (FM) mínima requerida para digitalizar la señal sin perder información?***

    Es de 8 kHz --> 8 kHz >= 2 * 4 kHz 


3. **Medios Físicos: Fibra Óptica**
    ***Compare las fibras ópticas Singlemode (monomodo) y Multimode (multimodo) en los siguientes aspectos:***
    - Diámetro del núcleo
    - Distancia típica de uso (corta/larga)
    - Mecanismo de propagación de la luz

    La monomodo es utilizada para largas distancias (WAN/Backbone), usa un solo modo de propagación que reduce la dispersión modal a diferencia de la multimodo que es usada para distancias mas cortas (Data Center/LAN) y permite multiples modos de propagacion, lo que genera más dispersión y pérdida. El diametro del nucleo de una multimodo es de 50/62 micrómetros mientras que el de una monomodo es de 9 micrómetros. Generalmente, para monomodo los cables son más económicos, pero requiere equipos láser más precisos (caros) y con las multimodo el cable es más caro, pero usa equipos LED/VCSEL más económicos.

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

    En el contexto de NFV, MANO significa Management and Orchestration. los 3 niveles principales de su arquitectura son:
        - NFVO (NFV Orchestrator) --> Gestiona el ciclo de vida de los servicios de red

        - VNFM (VNF Manager) --> Adminsitra funciones virtualizadas

        - VIM (Virtual Infrastructure Manager) --> Controla la infraestructura

## Bloque 3: Protocolos y Enrutamiento

7. **Enrutamiento Estático vs. Dinámico**
    ***Establezca las diferencias fundamentales entre el Ruteo Estático y el Ruteo Dinámico en términos de administración, flexibilidad y escalabilidad. Mencione un protocolo de ruteo dinámico de tipo Link-State y otro de tipo Vector Distancia.***

    En el ruteo estatico, las rutas se ingresan manualmente en la tabla de enrutamiento mientras que en el ruteo dinamico se utilizan protocolos de enrutamiento para descuburir las rutas. El estatico es mas simple pero menos flexible en comparacion con el dinamico dado que este ultimo es mas escalable y se adapta a cambios de red.

    - Protocolo de Ruteo Link-State: OSPF (Open Shortest Path First).
    - Protocolo de Ruteo Vector Distancia: RIP (Routing Information Protocol).

8. **MPLS (Multiprotocol Label Switching)**
    ***Describa qué es MPLS y cómo difiere del enrutamiento IP tradicional. ¿Cuál es la función principal de las etiquetas (labels)? ¿Cuál es una aplicación clave de MPLS en redes empresariales (ej. VPNs)?***

    MPLS es una tecnologia de transporte de datos en redes que usa etiquetas para enrutar, en lugar de direcciones IP completas. Su funcion principal es permitir la conmutación y el reenvío rápido en el core de la red basado en la etiqueta en lugar de realizar una búsqueda compleja en la tabla de ruteo IP en cada salto. Los proveedores de servicios (ISPs) lo usan como transporte WAN. Es muy usado en empresas con multiples sedes dada la seguridad de las VPN.

9. **Protocolos Obsoletos/Legacy**
    ***De los protocolos de Capa 2 o 3, como X.25 y Frame Relay, ¿cuál era la principal limitación que los hacía ineficientes para el tráfico en tiempo real, lo que llevó a su reemplazo por tecnologías más modernas como Ethernet o MPLS?***

    La principal limitacion fue la generacion de sobrecarga de red (overhead) y la falta de eficiencia para trafico en tiempo real por parte de la X.25. Luego fue reemplazada por FR para tráfico por ráfagas (ej: cajeros automáticos) pero esta ultima ya no se usa comercialmente.

10. **Conceptos Clave**
    ***Defina brevemente los siguientes términos:***
    ***VLAN (Virtual LAN)***
    Redes virtuales que particionan una LAN física en múltiples redes virtuales independientes, reduciendo congestión y aislando tráfico.

    ***BGP (Border Gateway Protocol)***
    Protocolo de enrutamiento dinamico utilizado para intercambiar informacion entre sistemas autonomos.

    ***PAT (Port Address Translation)***
    Traduccion de direcciones privadas a publicas, many-to-one, tıpico hogar/empresa

    ***QoS (Quality of Service)***
    Caracteristica moderna de los servicios que permite priorizar ciertos tipos de trafico, como llamadas.