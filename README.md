# SKYNET openclaw

**SKYNET openclaw** es un fork de OpenClaw enfocado en autonomía real: auto‑mejora activa, conversación automática entre peers y un estilo operativo más proactivo. Todo se controla por configuración para que puedas ajustar el nivel de autonomía.

## Qué trae (lo importante arriba)

- **Auto‑mejora automática**: cada respuesta pasa por un filtro de mejora silencioso para claridad y calidad.
- **Conversación peer‑to‑peer**: instancias OpenClaw pueden hablar entre sí vía gateway‑to‑gateway usando `peers_chat`.
- **Modo autónomo**: el agente actúa con iniciativa dentro de las políticas de herramientas y seguridad.

## Configuración rápida

```yaml
# ~/.openclaw/config.yaml
agents:
  defaults:
    selfImprove:
      enabled: true
      prompt: |
        Auto‑mejora activa. Revisa claridad, corrige errores y responde con la mejor versión.

tools:
  peers:
    enabled: true
    allow: ["*"]
    peers:
      - id: skynet-alpha
        label: Gateway Alpha
        url: wss://gateway-alpha.example/ws
        token: YOUR_PEER_TOKEN
        agentId: main
```

## Uso rápido

- **Auto‑mejora**: siempre activa mientras `selfImprove.enabled` esté en `true`.
- **Chat con peers**:

```
peers_chat {
  "peerId": "skynet-alpha",
  "message": "Hola, ¿estado del sistema?"
}
```

## Notas

- La auto‑mejora y el chat entre peers se ejecutan de forma automática, pero respetan políticas de herramientas y permisos.
- Para producción, usa tokens de gateway seguros y limita `tools.peers.allow` si necesitas restringir peers.
