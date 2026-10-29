# Política de seguridad

Este repositorio documenta un laboratorio educativo local. No es una configuración de producción.

## Reportar problemas

No publiques claves privadas, contraseñas, tokens, archivos de configuración reales ni información personal en issues o commits. Si una clave real se expone, considérala comprometida y genera un nuevo par de claves.

## Prácticas seguras

- Las configuraciones del repositorio son plantillas con marcadores.
- Mantén las claves privadas fuera del repositorio.
- Protege `/etc/wireguard/wg0.conf` con permisos restrictivos (`0600`) y propiedad de `root`.
- No expongas el puerto de WireGuard a Internet sin revisar previamente el firewall y el diseño de acceso.
- No reutilices claves entre dispositivos.
- Revoca las claves de un peer que ya no deba tener acceso.
