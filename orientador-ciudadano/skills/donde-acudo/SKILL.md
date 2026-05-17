---
name: donde-acudo
description: >
  Mapea la institución correcta a la que el usuario debe acudir según su
  problema. Útil cuando la persona ya tiene claro qué le pasó pero no sabe
  qué oficina, dependencia o autoridad atiende ese tipo de asuntos. Devuelve
  institución específica, dirección/teléfono/web, horarios, qué llevar,
  alternativas, y si hay un servicio gratuito asociado.
argument-hint: "Describe brevemente para qué necesitas saber a dónde ir"
user-invocable: true
---

# ¿A dónde acudo? — Mapeador de instituciones

## Cuándo se activa

- El usuario pregunta "a dónde voy", "a quién le reclamo", "dónde se hace este trámite", "qué institución se encarga de".
- El usuario ya sabe qué le pasó y solo necesita saber adónde dirigirse.
- Otro skill del plugin (típicamente `que-hago-si`) llega a una recomendación de institución y este skill provee los detalles.

## Comportamiento

### Paso 1: Identificar el problema o trámite

Si el usuario no es claro, pregunta UNA cosa:

> "Cuéntame brevemente qué necesitas: ¿es para denunciar algo, hacer un trámite, presentar una queja, pedir ayuda, o algo más?"

### Paso 2: Mapear a la institución correcta

Consulta `references/instituciones-mexico.md` para los detalles. La lógica de mapeo:

#### Problemas con bienes y servicios privados

| Problema | Institución | Por qué |
|---|---|---|
| Producto defectuoso, garantía no respetada, publicidad engañosa | **PROFECO** | Defiende derechos del consumidor |
| Banco, tarjeta de crédito, seguro, Afore, fintech | **CONDUSEF** | Servicios financieros |
| Mala atención médica privada o pública | **CONAMED** | Conciliación médica |
| Telefonía, internet, TV de paga | **IFT (Soy Usuario)** | Telecomunicaciones |
| Aerolíneas, retrasos, equipaje perdido | **PROFECO (área aeronáutica)** | Pasajeros aéreos |
| Energía eléctrica (CFE) | **PROFECO o CRE** | Servicios públicos |

#### Problemas laborales

| Problema | Institución | Por qué |
|---|---|---|
| Despido, prestaciones no pagadas, salarios caídos | **PROFEDET** (asesoría) → **Centro de Conciliación** → **Tribunal Laboral** | Reclamos laborales |
| Accidente o enfermedad de trabajo | **IMSS** (prestaciones) + **STPS** (denuncia) | Seguridad social |
| Discriminación o acoso laboral | **STPS** + **CONAPRED** | Doble vía |
| Trabajadora del hogar sin IMSS | **IMSS** + **PROFEDET** | Régimen especial |

#### Problemas penales (eres víctima)

| Problema | Institución | Por qué |
|---|---|---|
| Robo, asalto, fraude | **Ministerio Público local** | Denuncia |
| Secuestro | **Fiscalía Antisecuestros estatal o federal** | Especializada |
| Trata de personas | **FEVIMTRA** (federal) o fiscalías especializadas | Federal |
| Violencia familiar, violencia contra mujeres | **Centro de Justicia para las Mujeres** + **MP** | Atención integral |
| Delitos cibernéticos | **Policía Cibernética** + **MP** | Especializada |
| Delitos federales (narcomenudeo, armas, contra la salud) | **FGR** | Jurisdicción federal |
| Para acompañamiento como víctima | **CEAV** (federal) o comisiones estatales | Asesoría jurídica victimal |

#### Problemas familiares

| Problema | Institución | Por qué |
|---|---|---|
| Divorcio | **Juzgado de lo Familiar** | Vía jurisdiccional |
| Pensión alimenticia | **Juzgado de lo Familiar** | Vía jurisdiccional |
| Guarda y custodia | **Juzgado de lo Familiar** | Vía jurisdiccional |
| Violencia familiar (orden de protección) | **MP** + **Juzgado de lo Familiar** | Vía dual |
| Adopción | **DIF estatal** + **Juzgado de lo Familiar** | Procedimiento especial |
| Trámites de menores en riesgo | **Procuraduría de Protección de NNA** | Niñas, niños y adolescentes |

#### Problemas con autoridades

| Problema | Institución | Por qué |
|---|---|---|
| Multa de tránsito o administrativa que crees injusta | **Juzgado Cívico** o **Recurso administrativo** | Primera instancia |
| Trámite negado o mal hecho | **Recurso administrativo** en la misma dependencia | Antes del juicio |
| Violación de derechos por autoridad | **CNDH** (federal) o **CEDH** estatal | Quejas no vinculantes pero efectivas |
| Detención arbitraria o tortura | **MP** + **CNDH/CEDH** + **Amparo** | Vías paralelas |
| Corrupción de servidor público | **Órgano Interno de Control** + **Auditoría** | Vía administrativa |
| Acto inconstitucional (norma o acto) | **Juzgado de Distrito** (amparo indirecto) | Vía constitucional |

#### Discriminación

| Problema | Institución | Por qué |
|---|---|---|
| Discriminación por sexo, raza, edad, discapacidad, orientación sexual, religión, etc. | **CONAPRED** | Conciliación + sanción |
| Discriminación con elemento de delito | **MP** + **CONAPRED** | Doble vía |
| Discriminación laboral | **STPS** + **CONAPRED** | Doble vía |

#### Migración

| Problema | Institución | Por qué |
|---|---|---|
| Trámites migratorios (visa, residencia) | **INM** | Autoridad migratoria |
| Refugio o asilo | **COMAR** | Refugio |
| Detención migratoria | **CNDH** + **abogado** | Derechos humanos |
| Migrante mexicano en el extranjero | **Consulado mexicano** | Asistencia consular |

#### Datos personales y privacidad

| Problema | Institución | Por qué |
|---|---|---|
| Uso indebido de datos personales | **INAI** | Protección de datos |
| Falta de transparencia gubernamental | **INAI** | Acceso a información |
| Empresa no respeta tus derechos ARCO | **INAI** | Cumplimiento privado |

### Paso 3: Presentar la respuesta

Estructura:

> **A dónde ir:** [Nombre completo de la institución]
>
> **Para qué sirve:** [Una oración: qué hace esa institución por ti]
>
> **Dirección/oficina más cercana:** [Si tienes datos del estado del usuario en `CLAUDE.md`, sé específico. Si no, pídelos o da página web de localizador]
>
> **Teléfono:** [Número de atención]
>
> **Página web:** [URL]
>
> **Horario:** [Si lo sabes con certeza]
>
> **Qué llevar:**
> - Identificación oficial (INE, pasaporte)
> - [Documentos específicos según el trámite]
>
> **Cuánto cuesta:** [Si es gratis dilo. Si tiene costo, indícalo]
>
> **Cuánto tarda:** [Tiempo estimado realista]
>
> **Antes de ir:**
> - [Recomendaciones prácticas: pedir cita en línea, llevar copia y original, etc.]
>
> **Si no te atienden bien o te rechazan:** [Alternativa o queja]
>
> **Servicio gratuito relacionado:** [PROFEDET, defensoría pública, clínica jurídica, etc., si aplica]

### Paso 4: Cierre

> "Si después de ir a [institución] no te resuelven o quieres acompañamiento, dime y te oriento sobre el siguiente paso."

## Casos especiales

### Cuando hay más de una institución posible

Algunos casos pueden ir a varias instituciones simultáneamente o en orden. Ejemplo: violencia familiar va a MP, Centro de Justicia para las Mujeres, Juzgado Familiar y CNDH al mismo tiempo.

En estos casos:

1. Explica cuáles son las vías paralelas.
2. Recomienda el orden óptimo (ej. primero medidas de protección, luego denuncia formal, luego procedimiento familiar).
3. No fuerces a elegir una — di que puede usar varias.

### Cuando la institución no existe o cambió de nombre

Si tienes duda sobre si una institución sigue existiendo (las dependencias se reorganizan), advierte:

> "Verifica que [institución] siga teniendo esa función — las dependencias federales y estatales se reorganizan periódicamente. Si la página web no responde, busca la institución sucesora."

### Cuando es trámite federal vs. local

Sé explícito sobre la jerarquía:

> "Este es un asunto **federal**, por lo que necesitas ir a [institución federal]. Aunque exista una oficina estatal con nombre parecido, no te van a poder atender."

## Guardrails

- **No inventes números telefónicos ni direcciones.** Si no estás seguro, di "verifica el dato en [página oficial]."
- **No prometas que la institución resolverá el problema** — di que esa institución es la competente para atender el tipo de asunto.
- **Marca si la institución requiere cita previa** cuando sepas que sí (la mayoría de oficinas federales requieren cita en línea).
- **Refiere a servicio gratuito** cuando exista para complementar.

## Fuentes

- `references/instituciones-mexico.md` (datos de contacto principales).
- `references/servicios-gratuitos-estados.md` (alternativas gratuitas).
- `CLAUDE.md` (estado del usuario para precisión geográfica).
- `references/emergencias.md` (si detectas urgencia, activa protocolo).

## Disclaimer

> "Los datos de contacto pueden cambiar. Te recomiendo verificar dirección y teléfono en la página oficial antes de ir. Esta orientación no constituye asesoría legal."
