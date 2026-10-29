# Plan de mejoras

## Fase 1 — Reproducibilidad y persistencia
- [ ] Documentar versión de Debian, VirtualBox y WireGuard.
- [ ] Hacer persistente la IP de `enp0s8` con el gestor de red adecuado.
- [ ] Reiniciar Debian y validar `systemctl status wg-quick@wg0`.
- [ ] Verificar `sudo wg show` y repetir el ping.

## Fase 2 — Segundo cliente
- [ ] Añadir el PC anfitrión como peer separado.
- [ ] Generar claves propias para ese cliente; nunca reutilizar claves privadas.
- [ ] Asignar otra IP del túnel, por ejemplo `10.10.10.3/32`.
- [ ] Documentar revocación de un peer.

## Fase 3 — Controles de acceso
- [ ] Definir explícitamente qué destinos necesita cada peer.
- [ ] Crear una matriz de flujo permitido/bloqueado.
- [ ] Probar reglas de firewall en entorno aislado.
- [ ] Evitar el reenvío entre redes salvo que sea necesario.

## Fase 4 — Acceso remoto (proyecto separado)
- [ ] Diseñar la conectividad WAN y revisar CGNAT.
- [ ] Proteger el endpoint público y documentar exposición de UDP.
- [ ] Añadir DNS dinámico solo si se necesita.
- [ ] Probar un cliente externo sin exponer servicios de administración.
- [ ] Si se estudia túnel completo, documentar forwarding, NAT, DNS e IPv6.

Cada fase debe incluir objetivo, diagrama, pasos reproducibles, pruebas, resultado y limitaciones.
