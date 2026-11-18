# Taranis Black Gems  
**Challenge One G11 — AI for Business**  
**Ruta 2: IA para Marketing y Contenidos**

Repositorio con todos los entregables del challenge aplicado a **Taranis Black** (mobiliario corporativo de ergonomía activa – líneas ErgoPro, SmartDesk y Silence).

> **Nota importante sobre la migración Gems → Skills (a partir del 17/11):**  
> De forma progresiva, las Gems de Google Gemini están migrando a **Skills**. Esto permitirá conectar varias Gems entre sí y trabajar directamente desde Gemini combinando capacidades.  
> A la fecha de este repositorio las Gems siguen vigentes. Los permisos otorgados para utilizarlas continuarán sin perjuicio de la migración.

---

## 📋 Orden real de creación (paso a paso)

1. **Primero se realizaron los 3 AI Canvas en StartSe**  
   Para entender la problemática y analizar los distintos puntos de cada caso de uso.  
   Cada Canvas contiene los **6 puntos clave**:

   | # | Punto del Canvas              | Descripción breve |
   |---|-------------------------------|-------------------|
   | 1 | **Problema**                  | Problema central del negocio |
   | 2 | **Como resolver SEM AI**      | Proceso actual (manual) |
   | 3 | **Como resolver COM AI**      | Solución AI by design |
   | 4 | **Para quem?**                | Personas / destinatarios |
   | 5 | **Dados**                     | Datos e fuentes |
   | 6 | **Ferramentas + Indicadores** | Herramientas e indicadores de sucesso |

   **Problema central (del documento de entrega):**  
   El equipo de marketing de Taranis Black (4 personas) gestiona simultáneamente LinkedIn, Instagram, TikTok y el blog. El tono de voz pierde consistencia, las imágenes dependen de freelancers que tardan en entregarlas y las respuestas en redes demoran más de 24 horas. Todo esto bajo un crecimiento anual >35%.

2. **Luego se crearon los Manuales de base de conocimiento**  
   - `docs/taranis_black_tono_de_voz_es_txt.txt` → Manual de Identidad Verbal y Tono de Voz v1.0  
   - `docs/taranis_black_briefing_de_marca_es_txt.txt` → Briefing de Marca Corporativo v1.0  

   Estos dos documentos son la **fuente de verdad (RAG)** que alimenta a todas las Gems.  
   En el Manual de Tono se usó la técnica de **few-shot prompting** (ejemplos de “Antes / Después”) para guiar al modelo.

3. **Se configuraron las 4 Gems** con los prompts de sistema (carpeta `prompts/`).

4. **Se generaron ejemplos reales** de uso de las Gems (carpeta `examples/`) y assets visuales (carpeta `assets/`).

---

## 🏗️ Arquitectura del sistema

```mermaid
flowchart TD
    A[3 AI Canvas StartSe] --> B[Manual de Tono + Briefing]
    B --> C[Base de Conocimiento RAG]
    
    C --> D[Gem 1: Auditor de Tono]
    C --> E[Gem 2: Multiplicador de Contenido]
    C --> F[Gem 3: Estratega SEO + Deep Research]
    C --> G[Gem 4: Director Creativo Visual]
    
    D --> H[Revisión Human-in-the-Loop]
    E --> H
    F --> H
    G --> H
    
    H --> I[Publicación Multicanal]
```

### Agentes implementados

| # | Agente | Función principal | Archivo de prompt | Enlace a la Gema |
|---|--------|-------------------|-------------------|------------------|
| 1 | **Auditor de Identidad Verbal** | Evalúa borradores (1-10), detecta palabras prohibidas, reescribe en tono Taranis. | `prompts/auditor-de-tono-de-voz.md` | [Abrir Gema](https://gemini.google.com/gem/1mgUNS7Rsu6Oj_IeBkj4USKk39R5wjgn6?usp=sharing) |
| 2 | **Multiplicador de Contenido Semilla** | Transforma 1 contenido semilla → formatos listos (Blog, Email, LinkedIn, Newsletter, Carrusel, TikTok) | `prompts/multiplicador-de-contenido.md` | [Abrir Gema](https://gemini.google.com/gem/1lh6k7eX1xQh4-m-gcddIqn_ofa93MVXP?usp=sharing) |
| 3 | **Estratega SEO & Campañas** | Investigación real en Google (tendencias + PAA) + estructuras SEO. **Doble uso**: Mode 3 genera el calendario editorial completo. | `prompts/seo-estrategico.md` | [Abrir Gema](https://gemini.google.com/gem/18XQNusWRCaE35wQVHqIdaK1CyIRkGaFn?usp=sharing) |
| 4 | **Director Creativo Visual** | Fichas de dirección de arte + prompts técnicos en inglés para generación de imágenes | `prompts/director-creativo.md` | [Abrir Gema](https://gemini.google.com/gem/1hw6INvrdKpGI1MkEZKgBzumH-I3k60kN?usp=sharing) |

> **Nota importante sobre el Agente SEO**:  
> Primero realiza investigación en tiempo real (tendencias de mercado, People Also Ask, artículos que rankean). Luego identifica los ángulos de mayor retorno.  
> El **Modo 3** se usa específicamente para armar el calendario de publicaciones y diagramar la campaña mensual completa (ver ejemplo en `examples/calendario-editorial-mensual.md`).

---

## 📁 Estructura del repositorio

```
taranis-black-gems/
├── README.md
├── docs/
│   ├── taranis_black_tono_de_voz_es_txt.txt
│   ├── taranis_black_briefing_de_marca_es_txt.txt
│   └── politica-gobernanza-etica.md
├── prompts/
│   ├── auditor-de-tono-de-voz.md
│   ├── multiplicador-de-contenido.md
│   ├── seo-estrategico.md
│   └── director-creativo.md
├── examples/
│   ├── contenido-semilla.md
│   ├── adaptaciones-multiplicador.md
│   ├── diagnosticos-auditor-tono.md
│   ├── calendario-editorial-mensual.md
│   └── prompts-imagenes-director-creativo.md
├── architecture/
│   └── diagrama-flujo.md
└── assets/
    ├── silla.jfif
    ├── escritorio.jfif
    └── cabina.jfif
```

---

## 🖼️ Assets visuales generados

### Imagen 1 (LinkedIn / 16:9)
**Silla ErgoPro Executive** en oficina minimalista con mesh negro y base de aluminio pulido.  
Archivo: [`assets/silla.jpg`](assets/silla.jpg)

### Imagen 2 (Instagram / 4:5)
**Escritorio elevable SmartDesk Pro Dual 160** con tapa de roble FSC y panel táctil LED en uso Sit-Stand.  
Archivo: [`assets/escritorio.jpg`](assets/escritorio.jpg)

### Imagen 3 (Horizontal / 16:9)
**Cabina acústica modular Taranis Silence Quad** con vidrio doble laminado y estructura en grafito mate.  
Archivo: [`assets/cabina.jph`](assets/cabina.jpg)

Documentación completa de los user prompts + responses de la Gema Director Creativo:  
[`examples/prompts-imagenes-director-creativo.md`](examples/prompts-imagenes-director-creativo.md)

---

## 🎯 Métricas de éxito definidas

| Iniciativa | Meta |
|------------|------|
| Auditor de Tono | 80% menos retrabajos · 100% de piezas alineadas a los 4 pilares |
| Multiplicador | 75% reducción tiempo de producción multicanal |
| SEO Estratégico | +30% tráfico orgánico calificado · 60% menos tiempo de investigación |

---

## 🔒 Gobernanza

- Uso **exclusivo** de entornos Enterprise (Google Gemini Enterprise)
- **Human-in-the-Loop** obligatorio antes de cualquier publicación
- Prohibido cargar datos personales sin anonimizar
- Cumplimiento de **Ley 25.326** (Argentina), **LGPD**, **RGPD**, derechos **ARCO**, transparencia y mitigación de sesgos (ver detalle completo en `docs/politica-gobernanza-etica.md`)

---

**Autora**: Noelia Natalia María Orsini  
Desarrolladora Backend - Abogada - Counselor 

---


