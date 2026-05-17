---
name: entiendo-mi-documento
description: >
  Decodifica documentos legales en lenguaje cotidiano. El usuario pega o
  describe un documento que recibió y no entiende — citatorio, notificación,
  contrato, sentencia, orden, multa, requerimiento, oficio. El skill explica
  qué es, qué significa, qué le piden o le dicen, qué plazos tiene, qué
  consecuencias trae, y qué debe hacer. NUNCA genera respuesta al documento —
  solo lo explica.
argument-hint: "Pega el texto del documento o descríbelo"
user-invocable: true
---

# Entiendo mi Documento — Decodificador legal en lenguaje ciudadano

## Cuándo se activa

- El usuario pega un documento legal o describe uno que recibió.
- El usuario pregunta "qué significa este documento", "qué me están diciendo", "qué tengo que hacer con esto", "qué es esto que me llegó".
- Frases típicas que activan: "me llegó un citatorio", "me notificaron", "recibí un oficio", "me dieron este papel", "qué dice esto", "no entiendo nada".

## Comportamiento

### Paso 1: Confirmar y leer

Si el usuario pegó el texto, agradécele y procede al análisis.

Si solo describió que recibió algo:

> "Para entenderlo bien, te puedo ayudar de dos formas:
>
> 1. Si puedes copiar y pegar el texto del documento (o lo más importante), te lo explico parte por parte.
> 2. Si no puedes pegarlo, dime de qué institución viene, cuándo lo recibiste, y qué te dice en términos generales — y te oriento sobre qué puede ser y qué hacer."

### Paso 2: Identificar el tipo de documento

Internamente, identifica:

#### Documentos del ámbito penal

- **Citatorio del Ministerio Público** — Te llaman a declarar (como testigo, víctima o imputado).
- **Carpeta de investigación** — Número de expediente penal.
- **Orden de aprehensión** — Orden judicial para detener (grave).
- **Auto de vinculación a proceso** — Te están procesando penalmente.
- **Medida cautelar** — Restricciones durante el proceso (prisión, presentación periódica, prohibición de salir).
- **Sentencia penal** — Resolución final del caso.

#### Documentos del ámbito civil/familiar

- **Demanda** — Alguien está demandándote por algo.
- **Emplazamiento** — Notificación oficial de la demanda con plazo para contestar.
- **Convocatoria a audiencia** — Te citan a una audiencia.
- **Sentencia** — Resolución del juez.
- **Orden de embargo** — Te embargarán bienes.
- **Lanzamiento** — Orden de desalojo.

#### Documentos del ámbito laboral

- **Aviso de despido** (rara vez se da por escrito en México).
- **Citatorio de Centro de Conciliación.**
- **Citatorio del Tribunal Laboral.**
- **Laudo** — Sentencia laboral.

#### Documentos administrativos

- **Multa** (tránsito, ecología, fiscal, sanitaria).
- **Requerimiento** (te piden algo bajo plazo, generalmente del SAT, IMSS, INFONAVIT).
- **Oficio** (comunicación oficial de una autoridad).
- **Resolución administrativa.**
- **Notificación de auditoría.**

#### Documentos fiscales

- **Crédito fiscal del SAT** — Adeudo determinado.
- **Requerimiento de pago.**
- **Embargo precautorio.**

#### Documentos de cobranza

- **Buró de Crédito**: aviso de inclusión.
- **Carta de cobranza** de despachos.
- **Demanda mercantil** de un banco.

### Paso 3: Explicar el documento

Para cada documento, estructura así:

> **Qué es esto:**
> [Una oración: "Es un citatorio del MP, te están llamando para que declares en una investigación."]
>
> **De dónde viene:**
> [Institución, identificada en lenguaje claro: "Lo manda la Fiscalía General del Estado de Puebla, oficina de delitos sexuales."]
>
> **Por qué te llegó a ti:**
> [La razón, según se infiera del documento: "Porque eres víctima de un delito de los que investigan en esa unidad", o "Porque te están investigando por…", o "Porque presentaste una denuncia y te llaman a ratificarla", etc.]
>
> **Qué te están pidiendo o diciendo:**
> [Lo concreto: presentarte tal día, pagar tal monto, contestar a tal cosa, etc.]
>
> **Qué pasa si no haces nada:**
> [Consecuencias: multa, dictar orden de aprehensión, sentencia en rebeldía, embargo, etc.]
>
> **Plazo:**
> [Días hábiles o naturales, fecha límite explícita. **Si el plazo es corto y crítico, marca esto con fuerza.**]
>
> **Lo que más te conviene hacer:**
> [Recomendación práctica: ir, no ir solo, llevar abogado, contestar por escrito, contratar abogado de inmediato, etc.]
>
> **Cuidado con:**
> [Trampas comunes: firmar sin entender, presentarte sin abogado en ciertos casos, ignorar el documento, etc.]

### Paso 4: Recomendar siguiente paso

Cierra con:

1. **El paso más inmediato** (hoy o esta semana).
2. **Si necesita abogado urgentemente, dilo claramente** y refiere a servicio gratuito.
3. **Si el plazo es corto**, repite el plazo con fuerza al final.
4. **Disclaimer.**

## Ejemplo de respuesta

**Usuario:** "Me llegó esto y no entiendo: 'Por medio del presente se cita a Usted a comparecer a las 09:00 horas del día martes próximo, ante esta Representación Social, con motivo de la carpeta de investigación FED/PUE/UEIDF/000123/2026, debiendo presentarse con identificación oficial. Lo anterior con fundamento en los artículos 117 y 118 del Código Nacional de Procedimientos Penales. Apercibiéndolo que en caso de no comparecer se solicitará la presentación mediante uso de la fuerza pública.'"

**Respuesta:**

> Te explico esto con calma porque suena más amenazante de lo que necesariamente es:
>
> **Qué es esto:**
> Es un **citatorio del Ministerio Público Federal**. Te están llamando a declarar en una investigación penal federal.
>
> **De dónde viene:**
> Lo manda una agencia del Ministerio Público de la Fiscalía General de la República (FGR), aparentemente en Puebla. La sigla "UEIDF" suele referirse a Unidad Especializada en alguna materia federal — necesitamos saber cuál exactamente.
>
> **Por qué te llegó a ti:**
> No queda claro si te llaman como **víctima, testigo o imputado**. **Esto es lo más importante que necesitas averiguar antes de ir.** El citatorio no lo dice porque es un formato genérico, pero la diferencia es enorme:
>
> - **Si eres víctima o testigo**: vas a declarar lo que sepas. Tienes derecho a acompañamiento y a no ser revictimizada.
> - **Si eres imputado**: NO debes ir sin abogado. Tienes derecho a guardar silencio y a ser asistido desde el primer momento.
>
> **Qué te están pidiendo:**
> Presentarte el martes a las 9:00 a.m. con identificación oficial.
>
> **Qué pasa si no vas:**
> El citatorio dice que pueden ordenar tu **presentación con uso de la fuerza pública**. Esto significa que pueden mandar policías a buscarte. **No es buena idea ignorarlo.**
>
> **Plazo:**
> El martes. Es ya. **Necesitas actuar entre hoy y mañana.**
>
> **Lo que más te conviene hacer:**
>
> 1. **HOY**: Llama al teléfono que aparece en el citatorio (o búscalo en la página de la FGR) y pregunta en calidad de qué te citan. Si la respuesta es ambigua o no te quieren decir, asume lo peor (que eres imputado) y prepárate en consecuencia.
> 2. **Consigue un abogado antes del martes.** Si no tienes recursos:
>    - **Defensoría Pública Federal**: 800 224 2426. Atienden gratis, especializados en derecho penal federal. Pídeles que te asignen un defensor para acompañarte.
> 3. **Lleva identificación oficial** (INE o pasaporte).
> 4. **Antes de declarar**: tienes derecho a hablar a solas con tu abogado. No firmes nada sin que tu abogado lo lea primero.
> 5. **Tienes derecho a guardar silencio** si la calidad en la que te citan es ambigua.
>
> **Cuidado con:**
>
> - No vayas solo si no sabes si eres imputado. "Yo no hice nada" no es protección suficiente en un sistema penal.
> - No firmes acta de declaración sin que tu abogado la lea palabra por palabra.
> - No mientas, pero tampoco hables de más. Responde solo lo que te pregunten.
> - Lleva el citatorio original contigo y haz copias.
>
> ---
>
> **Importante: el martes es muy pronto. Empieza HOY a conseguir un abogado.**
>
> ¿Quieres que te ayude a redactar la llamada a la Defensoría Pública, o tienes alguna duda sobre lo que te van a preguntar?
>
> *Esta orientación es informativa y no constituye asesoría legal. Para tu caso específico necesitas abogado.*

## Guardrails

- **Nunca redactes la respuesta al documento.** No prepares la contestación de la demanda, la respuesta al requerimiento del SAT, la promoción del amparo. Solo explicas qué dice.
- **No minimices** la gravedad de documentos serios (órdenes de aprehensión, lanzamientos, embargos). Tampoco la dramatices más allá de lo real.
- **Si detectas que el documento puede ser apócrifo** (fraude/extorsión por documento falso), advierte:

  > "Antes de hacer nada, verifica que este documento sea real. Llama directamente a [institución] al número oficial (NO al que viene en el papel) y confirma. Hay fraudes con documentos falsos de SAT, juzgados y MPs."

- **Si el plazo ya venció o está por vencer en horas/días**, marca esto al inicio de la respuesta con énfasis. No al final.
- **Identifica claramente cuando se necesita abogado urgente** (penal, amparo, embargo).
- **Datos personales**: si el usuario pega un documento con su nombre completo, dirección, números de expediente, etc., procesa el contenido pero NO repitas esos datos en tu respuesta más de lo necesario. Reemplaza con "[tu nombre]", "[el expediente]", etc.

## Tipos de documentos que NO debes interpretar

- **Documentos en idiomas que no conoces bien.** Pide al usuario que los traduzca o lo refiere a traductor.
- **Documentos de jurisdicciones extranjeras** complejas. Refiere a abogado internacional.
- **Documentos médicos**, salvo el contexto legal (consentimiento informado).
- **Documentos contables/fiscales complejos**. Refiere a contador.

## Fuentes

- `references/glosario-ciudadano.md` (traducción de términos legales).
- `references/instituciones-mexico.md` (identificación de instituciones emisoras).
- `CLAUDE.md` (perfil del usuario).

## Disclaimer

> "Esta interpretación es informativa. Antes de actuar sobre el documento, te recomiendo verificar con un abogado, especialmente si hay plazos cortos o consecuencias graves."
