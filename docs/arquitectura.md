# Arquitectura y decisiones de diseño

## Objetivo

Construir una VPN de laboratorio entre una VM Debian y una VM Windows, separando la red de transporte de las direcciones virtuales del túnel.

## Redes

- `Nexus_LAN`: red interna existente asociada al laboratorio de Active Directory. Se conserva sin modificar.
- `WG_LAN`: red interna de VirtualBox que transporta paquetes WireGuard entre Debian y Windows.
- `10.10.10.0/24`: red virtual del túnel WireGuard.

## Por qué hay dos direcciones por equipo

La dirección `192.168.50.x` permite que el cliente alcance el endpoint WireGuard dentro de VirtualBox. La dirección `10.10.10.x` identifica al peer dentro del túnel y se utiliza para probar la conectividad protegida.

## Alcance de la configuración

El cliente solo enruta `10.10.10.1/32` por WireGuard. El servidor asocia la IP `10.10.10.2/32` a la clave pública del cliente. Esto limita el ejemplo a una comunicación entre peers y evita convertir accidentalmente el servidor en una puerta de enlace.

## Por qué no se usa un endpoint público

El objetivo de esta fase es aprender el protocolo en una red aislada. No se ha configurado redirección de puertos en un router ni se ha probado acceso desde Internet. Para un despliegue remoto se requeriría revisar direccionamiento público/CGNAT, firewall, endpoint, DNS dinámico si aplica y modelo de amenazas.
