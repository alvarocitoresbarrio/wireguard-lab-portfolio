# Validación y resultados

## 1. Red de transporte
Desde Windows:
```powershell
ping 192.168.50.10
```
Resultado observado: 4 respuestas de 4 paquetes enviados.

## 2. Estado en Debian
```bash
sudo systemctl status wg-quick@wg0
sudo wg show
```
La interfaz `wg0` se levantó correctamente. `wg show` mostró el peer cliente, un handshake reciente y contadores de transferencia.

## 3. Conectividad por el túnel
Desde Windows, con el túnel activo:
```powershell
ping 10.10.10.1
```
Resultado observado: 4 respuestas de 4 paquetes enviados.

## 4. Inicio automático
```bash
sudo systemctl enable wg-quick@wg0
```

## Capturas recomendadas
Guarda capturas reales en `docs/images/`: `wireguard-windows.png`, `wg-show.png` y `ping-tunnel.png`. Oculta claves, contraseñas y datos sensibles antes de publicarlas.
