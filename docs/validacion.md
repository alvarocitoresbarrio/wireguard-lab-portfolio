# Validación y evidencias

## Pruebas ejecutadas

| Prueba | Comando/acción | Resultado observado |
|---|---|---|
| Interfaces Debian | `ip -br addr` | `enp0s3` en NAT y `enp0s8` en `WG_LAN` |
| Transporte WG_LAN | `ping -c 4 192.168.50.20` desde Debian | Comunicación validada |
| WireGuard instalado | `wg --version` | `wireguard-tools v1.0.20210914` |
| Estado inicial | `sudo wg show` | Sin interfaz activa antes de configurar `wg0` |
| Interfaz del servidor | `sudo wg-quick up wg0` | Interfaz `wg0` levantada sin error |
| Peer registrado | `sudo wg show` | Clave pública del cliente y `AllowedIPs` visibles |
| Handshake | `sudo wg show` | `latest handshake` reciente |
| Tráfico por túnel | `ping 10.10.10.1` desde Windows | 4 enviados, 4 recibidos, 0 % perdidos |

## Interpretación

El handshake valida que los peers pudieron autenticarse criptográficamente. El ping a `10.10.10.1` demuestra que se transporta tráfico IP por el túnel.

## Lo que estas pruebas no demuestran

- Acceso a la VPN desde Internet.
- Que el tráfico web salga por la VPN.
- Acceso a `Nexus_LAN` o a Active Directory a través del túnel.
- Reglas de firewall de producción o resistencia frente a todos los ataques.
- Persistencia tras reinicio, hasta realizar una prueba específica de reinicio.

## Evidencias que añadir

Añade capturas redactadas de `ip -br addr`, `wg show` y el resultado de `ping`. Oculta claves, endpoints públicos sensibles, nombres de usuario si procede y cualquier dato personal. Nunca publiques claves privadas.
