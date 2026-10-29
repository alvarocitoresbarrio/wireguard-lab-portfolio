# Arquitectura del laboratorio

## Objetivo
Establecer un túnel WireGuard entre Debian Server y Windows Client01 en VirtualBox, manteniendo separada la red de transporte `WG_LAN` de la red preexistente `Nexus_LAN`.

## Componentes
- Debian: servidor WireGuard, `wg0`, `10.10.10.1/24`, UDP `51820`.
- Windows Client01: peer cliente, `10.10.10.2/24`.
- `WG_LAN`: red interna de transporte, `192.168.50.0/24`.
- `Nexus_LAN`: red existente de Active Directory, conservada sin cambios.
- NAT VirtualBox: conectividad de salida/administración de Debian.

## Decisión de diseño
Se eligió un túnel dividido. En el cliente, `AllowedIPs = 10.10.10.1/32` dirige por WireGuard solo el tráfico destinado a la dirección del servidor dentro del túnel. No se enruta todo Internet ni se anuncia `Nexus_LAN`.

## Direccionamiento observado

| Interfaz | Dirección |
|---|---|
| Debian `enp0s3` | `10.0.2.15/24` |
| Debian `enp0s8` | `192.168.50.10/24` |
| Debian `wg0` | `10.10.10.1/24` |
| Windows `Nexus_LAN` | `192.168.10.101` |
| Windows `WG_LAN` | `192.168.50.20/24` |
| Windows WireGuard | `10.10.10.2/24` |

Las direcciones asignadas por DHCP pueden cambiar.
