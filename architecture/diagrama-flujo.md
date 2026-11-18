# Diagrama de Flujo — Sistema de Agentes Taranis Black

```mermaid
flowchart LR
    subgraph Base["Base de Conocimiento"]
        Tono[Manual de Tono de Voz v1.0]
        Brief[Briefing de Marca v1.0]
    end

    subgraph Agentes["Gems / Skills"]
        A1[Auditor de Tono]
        A2[Multiplicador de Contenido]
        A3[Estratega SEO]
        A4[Director Creativo]
    end

    subgraph Salida["Salida + Control"]
        HITL[Human-in-the-Loop]
        Pub[Publicación Multicanal]
    end

    Tono --> A1
    Tono --> A2
    Tono --> A3
    Tono --> A4
    Brief --> A1
    Brief --> A2
    Brief --> A3
    Brief --> A4

    A1 --> HITL
    A2 --> HITL
    A3 --> HITL
    A4 --> HITL
    HITL --> Pub
```

## Flujo recomendado de trabajo diario

1. **Estrategia** → Gem SEO genera estructura / calendario
2. **Producción** → Gem Multiplicador genera piezas desde contenido semilla
3. **Calidad** → Gem Auditor revisa y ajusta tono
4. **Visual** → Gem Director Creativo genera assets
5. **Publicación** → Revisión humana final + publicación
