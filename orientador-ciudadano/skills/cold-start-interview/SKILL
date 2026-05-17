---
name: cold-start-interview
description: >
  Configuración inicial del plugin Orientador Ciudadano. Hace una entrevista
  corta para entender quién es el usuario, en qué estado se encuentra, su
  nivel de familiaridad con temas legales, y para qué va a usar el plugin.
  Llena el archivo CLAUDE.md con la información. Corre primero, antes que
  cualquier otro skill del plugin.
argument-hint: "Opcional: 'rápido' para configuración mínima de 1 minuto"
user-invocable: true
---

# Configuración inicial — Orientador Ciudadano

## Cuándo se activa

- Cuando el usuario invoca `/orientador-ciudadano:cold-start-interview`.
- Cuando otro skill del plugin detecta que el `CLAUDE.md` no está configurado (campos vacíos en estado, tipo de usuario, etc.) y necesita información mínima para responder bien.

## Comportamiento

### Modo normal (3–5 minutos)

Haz las siguientes preguntas, una por turno, con tono amable y conversacional. **No las hagas todas juntas.** Espera respuesta antes de pasar a la siguiente.

#### 1. Quién eres

> "Hola. Antes de empezar, déjame conocerte un poco para darte la mejor orientación posible. ¿Quién eres y para qué vas a usar este plugin?
>
> a) Soy una persona con un problema legal y busco orientación
> b) Soy estudiante de derecho o de ciencias sociales
> c) Trabajo en una clínica jurídica universitaria
> d) Trabajo en una organización de la sociedad civil que acompaña casos
> e) Soy servidor público en una ventanilla de orientación ciudadana
> f) Otro (especifica)"

#### 2. Dónde estás

> "¿En qué estado de la República te encuentras? Esto importa porque muchas leyes y servicios cambian dependiendo del estado.
>
> Si prefieres no decirlo, está bien — me dirás 'no especificar' y te daré orientación de aplicación nacional, aunque puede ser menos precisa."

Si responde un estado, pregunta opcionalmente:

> "¿Y el municipio? (opcional, solo si quieres que te refiera a servicios cercanos específicos)"

#### 3. Familiaridad con temas legales

> "¿Qué tan familiarizado/a estás con temas legales?
>
> a) Nada — no he tenido contacto con el sistema legal
> b) Un poco — alguna vez hice un trámite o tuve un problema
> c) Sí, manejo conceptos básicos (artículos, derechos, recursos)
> d) Soy profesionista o estudio una carrera relacionada"

Esto ajusta el nivel de lenguaje. Por defecto, lenguaje cotidiano. Si responde (c) o (d), eleva el registro técnico **pero sigue priorizando claridad**.

#### 4. Idioma y accesibilidad (opcional)

> "¿Prefieres que te explique las cosas de alguna forma especial? Por ejemplo:
>
> - Usar palabras muy simples
> - Explicar como si fuera para una persona mayor
> - Incluir ejemplos cotidianos
> - Usar también términos en una lengua indígena (dime cuál)
> - Otro
>
> Si no, sigo con el lenguaje claro que uso por defecto."

#### 5. Para quién vas a usar el plugin (solo si en pregunta 1 respondió a, b, o f)

> "¿El asunto que vas a consultar es para ti, o para alguien que estás ayudando (familiar, amistad, vecino)?"

Si es para alguien más, ajustar el lenguaje a segunda persona ("la persona que estás ayudando…") en vez de primera.

### Modo rápido (1 minuto)

Si el usuario invocó con `rápido` o si pide que sea breve, solo pregunta:

1. Estado de la República.
2. ¿Familiarizado con temas legales: sí o no?

El resto queda en valores por defecto.

## Después de la entrevista

### Confirma lo que captaste

Resume brevemente:

> "Listo. Entonces, para resumir:
>
> - Eres [tipo de usuario]
> - Estás en [estado]
> - [Nivel de familiaridad legal]
> - Vas a usar el plugin para [propósito]
>
> ¿Está bien así? Si quieres cambiar algo, dime."

### Escribe el CLAUDE.md

Una vez confirmado, **edita el archivo `CLAUDE.md`** del plugin (en `~/.claude/plugins/config/justicia-digital-mx/orientador-ciudadano/CLAUDE.md` o donde esté instalado) y llena los campos correspondientes en las secciones:

- "Datos de quien usa el plugin"
- "Información del estado del usuario"

Para el estado, busca en `references/servicios-gratuitos-estados.md` la sección correspondiente y copia los servicios identificados al `CLAUDE.md`.

### Cierre

> "Quedó configurado. Ya puedes usar cualquiera de estos comandos:
>
> - `/orientador-ciudadano:que-hago-si` — Si tienes un problema y no sabes qué hacer
> - `/orientador-ciudadano:donde-acudo` — Si sabes el problema pero no la institución
> - `/orientador-ciudadano:mis-derechos` — Si quieres conocer tus derechos en una situación
> - `/orientador-ciudadano:entiendo-mi-documento` — Si te llegó un documento y no lo entiendes
> - `/orientador-ciudadano:costo-estimador` — Si quieres saber qué cuesta un trámite
> - `/orientador-ciudadano:servicios-gratuitos-mapper` — Si necesitas ayuda legal gratuita
>
> Puedes también simplemente describirme tu situación y yo te oriento directamente."

## Guardrails

- **No pidas datos sensibles** en la entrevista (no preguntes por nombres completos, CURP, RFC, número de expediente, etc.).
- **Confidencialidad**: si el usuario dice "no quiero responder" a cualquier pregunta, acéptalo y sigue adelante con valores por defecto.
- **Sin interrogatorio**: máximo 5 preguntas. Si el usuario muestra prisa o ansiedad, ofrece modo rápido y procede.
- **Si en cualquier momento el usuario menciona una emergencia** (violencia activa, alguien desaparecido, riesgo de muerte), **interrumpe la entrevista** y activa el protocolo de emergencia (ver `references/emergencias.md`).

## Fuentes

- `CLAUDE.md` del plugin (lo edita).
- `references/servicios-gratuitos-estados.md` (lee para llenar la sección del estado).
- `references/emergencias.md` (consulta si detecta urgencia).
