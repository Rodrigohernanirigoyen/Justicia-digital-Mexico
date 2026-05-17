---
name: cold-start-interview
description: >
  Configuración inicial del plugin Laboral MX. Pregunta quién es el usuario,
  en qué estado se encuentra, si es trabajador o profesional, y para qué
  va a usar el plugin. Llena el CLAUDE.md con la información.
argument-hint: "Opcional: 'rápido' para configuración mínima"
user-invocable: true
---

# Configuración inicial — Laboral MX

## Comportamiento

### Preguntas (una por turno, máximo 4)

#### 1. Quién eres

> "Hola. Para orientarte mejor, dime: ¿quién eres y para qué vas a usar este plugin?
>
> a) Soy trabajador/a y tengo un problema laboral
> b) Soy abogado/a o profesional de Recursos Humanos
> c) Trabajo en PROFEDET o en una procuraduría de defensa del trabajo
> d) Soy estudiante de derecho o trabajo en una clínica jurídica
> e) Otro (especifica)"

#### 2. Estado

> "¿En qué estado de la República trabajas (o trabajabas)?"

#### 3. Situación actual (solo si es trabajador)

> "¿Cuál es tu situación laboral en este momento?
>
> a) Sigo trabajando pero tengo un problema
> b) Me acaban de despedir
> c) Renuncié
> d) Tuve un accidente de trabajo o estoy enfermo por el trabajo
> e) Trabajo por mi cuenta en una app (Uber, Rappi, DiDi, etc.)
> f) Otro"

#### 4. Urgencia

> "¿Hay algún plazo que te preocupe? Por ejemplo: ¿te despidieron hace poco y necesitas actuar rápido, o es algo que puedes revisar con calma?"

### Modo rápido

Si el usuario dice "rápido", solo pregunta: ¿trabajador o profesional? ¿En qué estado?

### Después de la entrevista

Confirma, edita el `CLAUDE.md`, y presenta los comandos disponibles:

> "Listo. Puedes usar estos comandos:
>
> - `/laboral-mx:calculadora-liquidacion` — Calcular cuánto te deben pagar
> - `/laboral-mx:despido-injustificado-triage` — Evaluar si tu despido fue legal
> - `/laboral-mx:conciliacion-prejudicial` — Preparar la conciliación (obligatoria antes de demandar)
> - `/laboral-mx:demanda-laboral-drafter` — Borrador de demanda laboral
> - `/laboral-mx:derechos-trabajador-qa` — Preguntas sobre tus derechos
> - `/laboral-mx:trabajador-hogar` — Si trabajas en un hogar
> - `/laboral-mx:plataformas-digitales` — Si trabajas en una app
> - `/laboral-mx:accidente-trabajo` — Si tuviste un accidente de trabajo
>
> O simplemente cuéntame qué te pasó y te oriento."

## Guardrails

- Si en cualquier momento el usuario menciona que le están pidiendo firmar algo AHORA, interrumpe la entrevista: **"Antes que nada: NO firmes nada. Ni renuncia, ni convenio, ni finiquito, ni nada. Primero vamos a revisar tu situación."**
- Si menciona un despido reciente (menos de 2 meses), advertir inmediatamente sobre el plazo de prescripción para reinstalación.

## Fuentes

- `CLAUDE.md` (lo edita).
