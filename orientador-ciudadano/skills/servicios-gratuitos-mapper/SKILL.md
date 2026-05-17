---
name: servicios-gratuitos-mapper
description: >
  Mapea servicios jurídicos gratuitos disponibles por estado y por tipo de
  caso. Cubre defensorías públicas (federal y estatales), Procuraduría de
  la Defensa del Trabajo (PROFEDET), Comisión Ejecutiva de Atención a
  Víctimas (CEAV), procuradurías de protección de NNA, clínicas jurídicas
  universitarias, despachos pro bono, OSCs especializadas, líneas
  telefónicas gratuitas, y orientación en lengua indígena.
argument-hint: "Dime tu estado y qué tipo de ayuda legal necesitas"
user-invocable: true
---

# Servicios Gratuitos Mapper — Encuentra ayuda legal sin costo

## Cuándo se activa

- El usuario pregunta dónde conseguir abogado gratis, asesoría legal sin costo, defensa gratuita.
- Frases típicas: "no tengo dinero para abogado", "¿hay ayuda gratis?", "¿dónde me asesoran gratis?", "necesito defensor público".
- Otro skill del plugin remite a este (especialmente `que-hago-si`, `costo-estimador`).

## Comportamiento

### Paso 1: Identificar tipo de necesidad

Pregunta (si no es claro):

> "Para conectarte con la opción correcta, dime:
>
> - ¿Qué tipo de caso necesitas? (Penal como víctima, penal como acusado, laboral, familiar, civil, derechos humanos, otro)
> - ¿En qué estado de la República estás?
> - ¿Es urgente? (alguien detenido, violencia activa, plazo por vencer)"

### Paso 2: Catálogo de servicios gratuitos por tipo

#### Para defensa penal (si te acusan de algo)

**Defensoría Pública Federal (Instituto Federal de Defensoría Pública)**

- Para delitos federales y para amparos.
- Cobertura nacional, oficinas en cada estado.
- **Teléfono:** 800 224 2426
- **Web:** www.ifdp.cjf.gob.mx
- Atienden 24/7 a personas detenidas.

**Defensoría Pública Local (de cada estado)**

- Para delitos del fuero común (locales).
- Adscrita al Poder Judicial estatal o ejecutivo (varía).
- Disponible en cada juzgado penal.

#### Para víctimas de delitos

**Comisión Ejecutiva de Atención a Víctimas (CEAV) — Federal**

- Asesoría jurídica gratuita para víctimas de delitos federales y de violaciones a derechos humanos.
- Inscripción en RENAVI (Registro Nacional de Víctimas).
- Acceso al Fondo de Ayuda, Asistencia y Reparación Integral.
- **Teléfono:** 800 842 8462
- **Web:** www.gob.mx/ceav
- También ofrecen apoyo psicológico, médico, social, económico.

**Comisiones Ejecutivas Estatales de Atención a Víctimas (CEEAV)**

- Una en cada estado. Para víctimas de delitos del fuero común.
- Buscar "CEEAV [tu estado]" o "Comisión Estatal Atención Víctimas [estado]".

**Procuraduría de Protección de Niñas, Niños y Adolescentes**

- En cada estado (estatal y municipal).
- Para casos donde haya NNA víctimas o en riesgo.
- Búsqueda: "Procuraduría Protección NNA [tu estado]".

**Centros de Justicia para las Mujeres (CJM)**

- Más de 60 a nivel nacional.
- Atención integral (jurídica, psicológica, médica, refugio) para mujeres víctimas de violencia.
- Búsqueda: "Centro de Justicia para las Mujeres [tu estado]".

#### Para asuntos laborales

**Procuraduría Federal de la Defensa del Trabajo (PROFEDET)**

- Asesoría jurídica y representación legal gratuita en juicios laborales.
- Atienden trabajadores en activo y despedidos, incluyendo informales.
- **Teléfonos:** 800 717 2942 y 800 911 7877
- **Web:** www.gob.mx/profedet
- Oficinas en cada estado.

**Procuradurías locales de defensa del trabajo** (en algunos estados).

#### Para asuntos familiares

**Defensoría Pública Federal — área familiar** (limitada).

**Defensorías locales** — Algunos estados tienen áreas especializadas en familia.

**DIF estatal y municipal** — Asistencia para asuntos familiares, especialmente con NNA.

**Centros de Mediación adscritos a Tribunales Superiores de Justicia** — Mediación familiar gratuita.

#### Para derechos humanos

**Comisión Nacional de los Derechos Humanos (CNDH)**

- Quejas contra autoridades federales.
- **Teléfono:** 800 715 2000
- **Web:** www.cndh.org.mx

**Comisión Estatal de Derechos Humanos** (en cada estado)

- Quejas contra autoridades estatales y municipales.
- Búsqueda: "CDH [tu estado]" o "Comisión Estatal Derechos Humanos [estado]".

**Visitadurías especializadas** dentro de la CNDH (asuntos indígenas, periodistas, migración, etc.).

#### Para discriminación

**Consejo Nacional para Prevenir la Discriminación (CONAPRED)**

- Quejas por discriminación de cualquier tipo.
- **Teléfono:** 800 543 0033
- **Web:** www.conapred.org.mx

**Copreds estatales** (en algunos estados).

#### Para consumidores

**Procuraduría Federal del Consumidor (PROFECO)**

- Quejas, conciliación, procedimientos.
- **Teléfono Consumidor:** 800 468 8722
- **Web:** www.gob.mx/profeco

**Comisión Nacional para la Protección y Defensa de los Usuarios de Servicios Financieros (CONDUSEF)**

- Para bancos, seguros, Afore, fintech.
- **Teléfono:** 800 999 8080
- **Web:** www.condusef.gob.mx

#### Para clínicas jurídicas universitarias

Atienden casos reales con estudiantes supervisados por profesores. Generalmente especializadas (interés público, derechos humanos, género). Cobertura limitada pero alta calidad.

Por ejemplo (revisar vigencia):

- **UNAM**: Bufete Jurídico Gratuito de la Facultad de Derecho.
- **ITAM**: Programa de Derechos Humanos.
- **Iberoamericana**: Bufete Jurídico Gratuito.
- **UDLAP**: Bufete Jurídico (Cholula, Puebla).
- **Tec de Monterrey**: Clínica de Litigio Estratégico.
- **CIDE**: Programa de Derecho.
- Otras universidades públicas y privadas en cada estado.

Búsqueda: "bufete jurídico gratuito [universidad o ciudad]".

#### Para casos de derechos humanos estratégicos / OSCs

Algunas OSCs nacionales que toman casos importantes:

- **Centro Prodh** (Miguel Agustín Pro Juárez) — DDHH amplios, especialmente Estado.
- **Tlachinollan** — DDHH indígenas, montaña de Guerrero.
- **CMDPDH** (Comisión Mexicana de Defensa y Promoción de los DDHH) — desaparición forzada, tortura.
- **Litigio Estratégico Indígena**.
- **GIRE** — derechos reproductivos.
- **Fundar** — transparencia, presupuestos, DDHH.
- **CEJIL** — litigio interamericano.
- **Equis Justicia para las Mujeres** — justicia con perspectiva de género.
- **Asistencia Legal por los Derechos Humanos (AsiLegal)** — sistema penal.
- **Casa del Migrante** y otras dedicadas a migrantes.

Estas OSCs toman casos por **criterio de selección**: típicamente casos paradigmáticos, de impacto estructural, o de poblaciones vulnerables. No atienden cualquier consulta — operan por evaluación de viabilidad estratégica.

#### Para asuntos en lenguas indígenas

**INALI (Instituto Nacional de Lenguas Indígenas)** — Traductores e intérpretes.

**INPI (Instituto Nacional de Pueblos Indígenas)** — Programas de defensoría con pertinencia cultural.

#### Para personas migrantes

**Casas del Migrante** (red de albergues con atención jurídica).
**FM4 Paso Libre, Sin Fronteras IAP, Asylum Access, IMUMI** — OSCs migrantes.

#### Para periodistas y defensores

**Mecanismo de Protección para Personas Defensoras de Derechos Humanos y Periodistas** (federal).

**Artículo 19**, **CMDPDH**, **Frontline Defenders** (para casos graves).

#### Líneas telefónicas de orientación gratuita

| Servicio | Teléfono |
|---|---|
| Locatel (CDMX, orientación amplia 24/7) | 55 5658 1111 |
| Línea Mujer Segura SEDIMUJER | 55 5512 5350 |
| Línea de la Vida (crisis emocional) | 800 290 0024 |
| Línea SOS Mujeres CDMX | *0765 |
| LOCATEL psicológica | 55 5533 5533 |
| Tel. Fortaleza (hombres en crisis) | 55 5346 8740 |

### Paso 3: Presentar respuesta

Estructura:

> **Para tu caso de [tipo], en [estado], las mejores opciones gratuitas son:**
>
> **Opción 1 (la más directa):**
> - **[Nombre]:** [Qué hace]
> - **Cómo accedes:** [Teléfono, web, dirección si la sabes]
> - **Qué llevar:** [Identificación, documentos]
> - **Qué esperar:** [Tiempo de respuesta, cómo será la atención]
> - **Ventaja:** [Por qué te conviene esta]
> - **Limitación:** [Lista de espera, complejidad, geográfica]
>
> **Opción 2 (alternativa o complemento):**
> [Misma estructura]
>
> **Opción 3 (para situaciones específicas o reforzar):**
> [Misma estructura]
>
> **Si estas opciones no funcionan o te rechazan:** [Plan B: escalar, otra dependencia, OSC]

### Paso 4: Cierre

1. **Sugerir empezar por la opción 1** y, si tarda, escalar.
2. **Si hay urgencia**, marcar cuál ofrece atención inmediata.
3. **Recordatorio**: el servicio gratuito existe **por derecho**. No es favor. Si te lo niegan sin justificación, denúncialo en el órgano interno de control de la dependencia.
4. **Disclaimer.**

## Consideraciones especiales

### Defensoría pública saturada

Es honesto reconocer que en muchos estados las defensorías públicas están saturadas. Recomendaciones:

- Acude personalmente (no solo por teléfono).
- Pide constancia de cada visita.
- Si te rechazan o no te atienden en plazos razonables, escala a CNDH/CEDH por violación al derecho a la defensa.
- Para casos urgentes (detenido en flagrancia), exige defensor de oficio en la audiencia inicial — es un derecho irrenunciable.

### Cuándo una OSC tomará tu caso

Las OSCs son selectivas. Tomarán tu caso si:

- Es paradigmático (puede sentar precedente).
- Hay población vulnerable involucrada.
- Hay impacto estructural posible.
- Encaja en su línea de trabajo.

Si no encaja, generalmente te referirán a otro servicio. No te ofendas — la capacidad es limitada.

### Para extranjeros

Los servicios gratuitos aplican a personas en territorio mexicano, **sin importar nacionalidad o estatus migratorio**. La excepción es la asistencia consular, que ofrece tu país de origen.

## Guardrails

- **Nunca asegures que el servicio gratuito tomará tu caso.** Hay criterios y capacidad limitada.
- **Da datos verificables.** Si no estás 100% seguro de un teléfono o dirección, di "verifica el dato en [página oficial]".
- **Reconoce limitaciones honestamente.** No vendas la defensoría como solución mágica; reconoce los retos.
- **Marca urgencias.** Si el caso es urgente y la atención gratuita puede tardar, sugiere paralelamente buscar un abogado privado dispuesto a aplazar el pago, o pedir apoyo familiar/comunitario.
- **No despaches con "consulta a un abogado".** Da pasos concretos. Decir "consulta abogado" sin información práctica es el equivalente a no responder.

## Fuentes

- `references/servicios-gratuitos-estados.md` (detalle por estado).
- `references/instituciones-mexico.md` (datos generales).
- `CLAUDE.md` (estado del usuario).

## Disclaimer

> "La disponibilidad y datos de contacto de servicios gratuitos pueden cambiar. Verifica en la página oficial antes de ir. Recuerda: tienes derecho a defensa adecuada — exígelo si no te atienden."
