# Cómo contribuir a Justicia Digital México

Gracias por considerar contribuir a este proyecto. Cada aporte cuenta: desde corregir un teléfono que cambió hasta proponer un plugin completo.

## Formas de contribuir

### 1. Datos de servicios gratuitos por estado

**El más alto impacto inmediato.** Si conoces los servicios jurídicos gratuitos de tu estado, ayúdanos a llenarlos en [`orientador-ciudadano/references/servicios-gratuitos-estados.md`](./orientador-ciudadano/references/servicios-gratuitos-estados.md).

Para cada estado necesitamos: defensoría pública, comisión de derechos humanos, centro de justicia para mujeres, comisión de búsqueda, CEEAV local, refugios, clínicas jurídicas universitarias, OSCs destacadas, y líneas locales de atención.

**Cómo hacerlo:**

1. Fork del repositorio.
2. Edita el archivo siguiendo la plantilla por estado.
3. Verifica cada teléfono y dirección (llama, busca en web oficial).
4. Pull Request con título: `data: servicios gratuitos [Nombre del estado]`.

### 2. Glosario ciudadano

Si conoces términos legales que no están en el glosario, o si crees que una explicación puede ser más clara, contribúyelo.

**Criterio:** la explicación debe entenderse por alguien sin formación legal. Lee la entrada en voz alta a alguien de tu familia que no estudie derecho — si entiende, sirve.

### 3. Nuevos skills para un plugin existente

Para proponer un nuevo skill dentro de un plugin existente:

1. Abre un Issue del tipo "Nuevo skill" describiendo: qué hace, para quién, por qué hace falta.
2. Espera retroalimentación (al menos 7 días) — la comunidad puede sugerir refinamientos.
3. Si hay consenso, escribe el SKILL.md siguiendo el [formato estándar](#formato-de-skill-md).
4. Pull Request con título: `feat([nombre-plugin]): skill [nombre-skill]`.

### 4. Plugins nuevos

Para proponer un plugin completo nuevo (no listados en el ROADMAP):

1. Abre un Issue de discusión justificando: necesidad, audiencia, no-redundancia con plugins existentes, plan de skills.
2. Esto requiere discusión más larga (mínimo 14 días).
3. Si se aprueba, fork del repo y desarrollo en una rama.

### 5. Reportar bugs o información desactualizada

Usa los templates de Issues. Cuanto más específico el reporte, mejor.

## Quién puede contribuir

- **Estudiantes de derecho** — sus aportes deben tener visto bueno de un profesor, abogado titulado, o pasar revisión de pares antes de mergearse.
- **Abogados** — pueden contribuir directamente. Indiquen cédula profesional o equivalente en su perfil de GitHub para asuntos de validación.
- **Defensores comunitarios y activistas** — bienvenidos especialmente para servicios gratuitos por estado, casos de uso reales, y feedback de campo.
- **Desarrolladores y diseñadores** — para infraestructura del repo, mejoras de presentación, y futuros conectores MCP.
- **Cualquier persona** — para reportar bugs, sugerir mejoras de claridad, contribuir traducciones (a lenguas indígenas, por ejemplo).

## Formato de SKILL.md

Todo skill debe seguir esta estructura:

```markdown
---
name: nombre-del-skill
description: >
  Descripción de 2-4 líneas que explica qué hace el skill, cuándo se
  activa, y qué NO hace (limitaciones importantes).
argument-hint: "Sugerencia breve de lo que el usuario debe escribir"
user-invocable: true
---

# Título humano del skill

## Cuándo se activa

[Frases típicas, contextos, invocación explícita]

## Comportamiento

### Paso 1: [...]
### Paso 2: [...]
### Paso N: [...]

## Guardrails

[Reglas duras que el skill nunca debe romper]

## Fuentes

[Archivos de referencia que el skill consulta]

## Disclaimer

[Texto del disclaimer apropiado al contexto]
```

## Reglas duras para todos los skills

Todo skill debe respetar:

1. **No genera documentos para presentar ante autoridades** salvo que sea su función explícita y autorizada. El plugin `orientador-ciudadano` nunca lo hace; plugins como `victimas-ddhh` o `amparo-mx` sí, pero con gates de revisión obligatorios.
2. **Disclaimer obligatorio** al final de cada respuesta sustantiva.
3. **Protocolo de emergencia** — toda interacción debe escanear por señales de crisis (ver [`orientador-ciudadano/references/emergencias.md`](./orientador-ciudadano/references/emergencias.md)) y priorizar atención inmediata cuando detecte.
4. **Servicios gratuitos referidos** cada vez que se sugiera consultar abogado.
5. **Lenguaje adaptado** al nivel del usuario declarado en `CLAUDE.md`.
6. **Jurisdicción declarada** explícitamente cuando la respuesta varíe por estado.
7. **Honestidad sobre limitaciones** — no prometer resultados, no idealizar instituciones saturadas, no inventar números o procedimientos.

## Proceso de revisión

| Tipo de contribución | Revisores necesarios | Tiempo estimado |
|---|---|---|
| Datos de servicios (un estado) | 1 mantenedor + verificación | 3-7 días |
| Glosario / referencias | 1 mantenedor | 1-3 días |
| Bug fix | 1 mantenedor | 1-3 días |
| Nuevo skill (plugin existente) | 1 mantenedor + 1 abogado | 7-14 días |
| Plugin nuevo | 2 mantenedores + 2 abogados | 14-30 días |

Las contribuciones que implican consejo legal (skills nuevos, modificación de comportamiento) **requieren al menos un revisor abogado** antes de mergearse.

## Validación legal de contribuciones

Las contribuciones que modifican la lógica de orientación legal deben pasar al menos uno de estos filtros:

- Revisión por abogada/o titulada/o con cédula profesional verificable.
- Revisión por estudiante de derecho con visto bueno de profesor universitario.
- Revisión por OSC reconocida en el ámbito específico (DDHH, laboral, género, indígena, etc.).

Esto no es burocracia: es para proteger a las personas usuarias de orientaciones incorrectas que podrían derivar en pérdida de derechos o problemas legales.

## Casos especiales

### Lenguas indígenas

Las traducciones del glosario y de mensajes clave a lenguas indígenas son extremadamente valiosas. Si hablas una lengua indígena y quieres contribuir traducciones, abre un Issue y te ponemos en contacto con quien coordina esa parte.

Verificación: pedimos doble revisión (dos hablantes nativos) para asegurar precisión.

### Datos por estado donde haya alerta de violencia de género

Algunos estados tienen alertas de violencia de género (AVGM) que cambian protocolos de atención. Si conoces las particularidades de la atención en un estado con AVGM, indícalo en la contribución para que el plugin pueda alertar al usuario.

### Información que puede ser sensible

NO incluyas en contribuciones:

- Datos personales de víctimas reales (aunque sean para "ejemplo").
- Detalles de casos en curso.
- Direcciones residenciales de personas físicas (sí oficinas de instituciones públicas).
- Información que pueda comprometer la seguridad de defensores.

Para ejemplos en SKILL.md, usa siempre situaciones genéricas.

## Código de conducta

Este proyecto se rige por nuestro [Código de Conducta](./CODE_OF_CONDUCT.md). Al participar, te comprometes a respetarlo.

## Reconocimiento

Toda contribución mergeada se reconoce en los commits y en el archivo `CONTRIBUTORS.md` (próximamente). Para casos de impacto especial (un plugin completo, una sección extensa de servicios, traducciones a lenguas indígenas), reconocimiento adicional en el README.

## Preguntas

- Para preguntas generales: usa GitHub Discussions.
- Para reportar problemas: GitHub Issues.
- Para asuntos de seguridad o sensibilidad: contacta a los mantenedores en privado.

---
