# Arquitectura del proyecto

> Cómo está construido Justicia Digital México y por qué.

## Filosofía técnica

### Markdown sobre código

Todo el ecosistema está escrito en **Markdown y JSON**. No hay código compilado, no hay build step, no hay frameworks de desarrollo. Esto es deliberado:

- **Cualquier abogado o estudiante** puede leer, entender y modificar un skill sin saber programar.
- **Las correcciones legales** son urgentes y no deben esperar a un ciclo de desarrollo.
- **La transparencia** es total: lo que ves en el SKILL.md es exactamente lo que Claude lee.
- **La portabilidad** es máxima: el ecosistema puede correr en cualquier instancia de Claude.

### Construir sobre claude-for-legal

El proyecto adopta la arquitectura del repositorio open source [`anthropics/claude-for-legal`](https://github.com/anthropics/claude-for-legal). Eso significa:

- Compatibilidad con la infraestructura existente (Claude Code, Claude Cowork, marketplace de plugins).
- Aprovechamiento de patrones probados (cold-start interview, agentes programados, conectores MCP).
- Posibilidad de integración futura al `legal-builder-hub` (el marketplace comunitario).

### Plugins como verticales independientes

Cada plugin es una **carpeta autocontenida** que se puede instalar, desinstalar y actualizar sin afectar a otros. Esto permite:

- **Adopción granular** — una clínica puede usar solo `clinica-juridica-mx`, una OSC solo `victimas-ddhh`, etc.
- **Mantenimiento distribuido** — cada plugin puede tener mantenedores distintos.
- **Especialización clara** — cada plugin tiene una audiencia y un objetivo definidos.

## Anatomía de un plugin

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json              ← Manifiesto: nombre, versión, skills, descripción
├── README.md                    ← Documentación pública del plugin
├── CLAUDE.md                    ← Perfil de práctica (se llena con cold-start-interview)
├── skills/
│   ├── cold-start-interview/
│   │   └── SKILL.md             ← Configuración inicial del plugin
│   ├── skill-1/
│   │   └── SKILL.md
│   ├── skill-2/
│   │   └── SKILL.md
│   └── ...
├── references/                  ← Corpus normativo y de datos
│   ├── glosario.md
│   ├── instituciones.md
│   └── ...
├── agents/                      ← Agentes programados (opcional)
│   └── agent-name.md
└── hooks/                       ← Hooks pre/post tool (opcional, raro)
    └── ...
```

### Manifest (`plugin.json`)

Define metadatos del plugin: nombre, versión, descripción, audiencia, jurisdicción, lista de skills y referencias. Lo lee Claude para registrar los comandos slash y la configuración general.

### Perfil de práctica (`CLAUDE.md`)

Es **el documento clave del plugin**. Define:

- Quién es el usuario (datos, perfil, estado).
- Cómo debe comportarse el plugin (estilo, registro, guardrails).
- Qué fuentes consultar.
- Qué nunca hacer.

Todos los skills del plugin **leen este archivo** antes de responder. Es la "personalidad" del plugin.

Se llena dinámicamente con el skill `cold-start-interview`. El usuario puede editarlo manualmente cuando algo cambie.

### Skills (`skills/*/SKILL.md`)

Cada skill es un archivo Markdown con frontmatter YAML. Define:

- **Frontmatter** (metadatos):
  - `name` — Identificador.
  - `description` — Descripción para Claude (cuándo activar).
  - `argument-hint` — Sugerencia al usuario.
  - `user-invocable` — Si se puede llamar con `/comando`.
- **Cuerpo** (instrucciones):
  - Cuándo se activa.
  - Cómo se comporta paso a paso.
  - Reglas duras (guardrails).
  - Fuentes que consulta.
  - Disclaimer apropiado.

Los skills son **invocados** por Claude automáticamente cuando detecta que aplican, o explícitamente por el usuario con un comando slash (`/plugin-name:skill-name`).

### References

Archivos Markdown con datos que los skills consultan: glosarios, catálogos de instituciones, fuentes normativas resumidas, números de emergencia, etc.

La regla es: si una información va a ser consultada por **más de un skill**, vive en `references/`. Si es específica de un solo skill, puede vivir en el cuerpo del SKILL.md.

### Agentes (opcional)

Workflows automáticos que corren en segundo plano. Por ejemplo:

- Un vigilante del DOF que avisa cuando se publica un cambio normativo.
- Un tracker de plazos procesales que recuerda cuando vence un término.
- Un monitor de nuevas tesis en el SJF.

Los agentes se despliegan separadamente (no son comandos invocables por el usuario directamente).

## Flujo típico de uso

```
Usuario instala plugin
        ↓
Corre /plugin:cold-start-interview
        ↓
Plugin pregunta datos → escribe CLAUDE.md
        ↓
Usuario describe su problema
        ↓
Claude lee CLAUDE.md + identifica skill aplicable
        ↓
Skill se ejecuta:
    1. Lee CLAUDE.md para contexto
    2. Lee references/ relevantes
    3. Aplica guardrails (emergencia, jurisdicción)
    4. Genera respuesta
        ↓
Respuesta al usuario con disclaimer
```

## Integración entre plugins

Los plugins pueden:

- **Sugerirse mutuamente**: `orientador-ciudadano` puede decir "si quieres preparar la denuncia, instala `victimas-ddhh`".
- **Compartir referencias**: si dos plugins necesitan el mismo glosario, vive a nivel del proyecto.
- **Trabajar en pipeline**: `orientador-ciudadano` clasifica → `victimas-ddhh` toma el caso identificado y profundiza.

Lo que NO hacen:

- **Modificarse entre sí**: cada plugin es soberano.
- **Compartir estado**: la información sensible no se traspasa automáticamente.

## Decisiones de diseño con justificación

### ¿Por qué Markdown y no JSON estructurado?

Los SKILL.md son instrucciones en lenguaje natural que Claude lee. Markdown permite que un abogado las lea como si fueran un manual de procedimiento, agregue ejemplos, mantenga formato. JSON sería más rígido y menos legible para quien no programa.

### ¿Por qué el CLAUDE.md está separado del manifest?

Porque el manifest es estable (lo escribe el desarrollador del plugin) y el CLAUDE.md es dinámico (lo llena el usuario con la entrevista inicial y lo edita conforme cambia su contexto).

### ¿Por qué `references/` y no inline en cada skill?

Para que múltiples skills compartan corpus sin duplicarlo. Y para que las actualizaciones de información (un teléfono que cambió) impacten en todos los skills que lo usan, no en uno solo.

### ¿Por qué no usar una base de datos para la jurisprudencia?

Por dos razones:

1. **Simplicidad operacional** — un repositorio Git con Markdown se mantiene y distribuye trivialmente.
2. **Conector MCP futuro** — la búsqueda dinámica de jurisprudencia (vía `sjf-connector`) será una capa encima del corpus local, no su reemplazo.

### ¿Por qué no integrar todo en un solo plugin?

Por tres razones:

1. **Audiencias distintas** — una víctima no usa el mismo plugin que un litigante.
2. **Mantenimiento distribuido** — distintas comunidades pueden mantener distintos plugins.
3. **Adopción granular** — instituciones pueden adoptar lo que les sirve.

## Cómo escalará el proyecto

### Hoy (Alpha)

- 1 plugin funcional.
- Mantenimiento centralizado.
- Pruebas en pequeño grupo.

### Año 1

- 4–5 plugins funcionales.
- 1–2 conectores MCP básicos.
- Comunidad de 5–10 contribuidores.
- Adopción en 2–3 clínicas jurídicas.

### Año 2

- 8–10 plugins funcionales.
- Conectores MCP críticos (SJF, DOF).
- Comunidad de 20+ contribuidores.
- Adopción en OSCs nacionales.
- Integración formal al ecosistema de Claude for Legal.

### Año 3+

- Ecosistema maduro y sustentable.
- Posibles forks regionales (otros países latinoamericanos).
- Investigación académica derivada del uso.

## Limitaciones conocidas

### De la arquitectura

- **Dependencia de Claude** — si Anthropic cambia las APIs de plugins, hay que adaptar.
- **No funciona offline** — requiere conexión.
- **Sin estado persistente entre sesiones** — más allá del CLAUDE.md, cada conversación empieza de cero.

### Del enfoque legal

- **No es asesoría** — limitamos deliberadamente lo que el plugin puede hacer para no sustituir abogados.
- **No genera documentos accionables sin gates** — para evitar daños por automatización irreflexiva.
- **Citas no verificadas** sin conector al SJF — marcadas como `[verificar]`.

### De la lengua

- Por ahora, todo está en español (México).
- Lenguas indígenas son objetivo futuro (requiere colaboración con hablantes nativos).

## Para profundizar

- [`CONTRIBUTING.md`](../CONTRIBUTING.md) — cómo contribuir.
- [`CONNECTORS.md`](../CONNECTORS.md) — conectores MCP.
- [`ROADMAP.md`](../ROADMAP.md) — hacia dónde vamos.
- [`SCENARIOS.md`](../SCENARIOS.md) — cómo probamos los plugins.
