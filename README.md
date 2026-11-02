# XPE Sandbox

Entorno de ejecucion real para **XPE Agent**: terminal, archivos, Python (Jupyter),
VSCode, navegador con VNC y servidor MCP. Corre aislado en Docker en nuestra VPS.

Copyright (c) 2026 Yostin Martinez (XPE Agent). Configuracion propia sobre AIO Sandbox
(agent-infra/sandbox), publicado bajo licencia MIT. Aviso original en NOTICE.md.

## Arranque

    cp .env.example .env
    # define XPE_SANDBOX_KEY con una clave larga
    docker compose up -d

API: http://IP:8080/v1 · Docs: http://IP:8080/v1/docs · VNC: http://IP:8080/vnc/index.html?autoconnect=true
VSCode: http://IP:8080/code-server/ · MCP: http://IP:8080/mcp

Todas las rutas exigen la cabecera X-AIO-API-Key.

## Uso desde XPE Agent

En Render:

    XPE_SANDBOX_URL=http://IP:8080
    XPE_SANDBOX_KEY=<la misma clave>

La app manda los comandos a /api/sandbox/execute, que los ejecuta aqui dentro de
/home/oai/share/xpe/<uid>. Nada corre en el servidor web.

## Requisitos

4 GB de RAM o mas. La ARM Always Free de Oracle (2-4 nucleos, 12-24 GB) es el destino.
