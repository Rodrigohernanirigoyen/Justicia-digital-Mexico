# Justicia Digital México

**Orientación legal gratuita por WhatsApp, impulsada por inteligencia artificial.**

Justicia Digital México es un ecosistema open source de plugins de Claude (Anthropic) adaptados al derecho mexicano. El proyecto permite que organizaciones de la sociedad civil (OSCs), clínicas jurídicas universitarias y colectivos de derechos humanos ofrezcan orientación legal gratuita y automatizada a través de WhatsApp — el canal que ya usan entre 78 y 89 millones de personas en México.

Una persona escribe a un número de WhatsApp, describe su problema y recibe orientación inmediata: qué derechos tiene, a dónde acudir, qué pasos seguir, y a quién llamar. Todo en español claro, sin tecnicismos, las 24 horas del día.

---

## El problema

En México, **más del 90% de los delitos no se denuncian** (ENVIPE, INEGI). Entre las razones que llevan a este dato, tenemos que la gente no sabe qué, dónde, y cómo hacerlo, o no tiene acceso a un abogado asequible. Los servicios gratuitos de orientación legal existen (CEAV, PROFEDET, CNDH), pero tienen horarios limitados, saturación, y barreras de acceso para comunidades rurales, indígenas y migrantes.

El costo de una consulta legal privada en México oscila entre $500 a $3,000 MXN. **10,000 consultas mensuales equivaldrían a $5-20 millones de pesos en honorarios,** pero este sistema propone realizarlas **sin costo alguno para el usuario**.

## La solución

Un bot de WhatsApp conectado al API de Claude que carga los plugins de Justicia Digital México -entrenados en legislación mexicana- como sistema de instrucciones. La persona escribe al número de la OSC, el sistema identifica el tipo de problema, activa el plugin correspondiente, y responde con orientación precisa, actualizada y sensible al contexto.

El bot no sustituye a un abogado — orienta, informa, y refiere. Cuando el caso lo requiere, escala a un ser humano.

---

## Plugins disponibles

### ✅ Orientador Ciudadano (`orientador-ciudadano`)

El plugin de entrada. Para cualquier persona que tiene un problema legal y no sabe por dónde empezar.

Identifica el tipo de problema (laboral, penal, familiar, consumidor, administrativo, DDHH) y canaliza a la institución correcta o al plugin especializado. Incluye directorio nacional de servicios jurídicos gratuitos, glosario ciudadano, protocolo de emergencias, y estimador de costos.

**6 skills:** que-hago-si, donde-acudo, mis-derechos, entiendo-mi-documento, costo-estimador, servicios-gratuitos-mapper.

### ✅ Laboral MX (`laboral-mx`)

Para trabajadores que enfrentan despidos, falta de pago, accidentes de trabajo, o simplemente quieren saber qué les corresponde.

Incluye una calculadora de liquidación con fórmulas completas (SDI, factores de integración por antigüedad, prima de antigüedad con tope, dos escenarios de salarios caídos), triage de despido injustificado basado en las causales del artículo 47 LFT, preparación de conciliación prejudicial, y borrador de demanda laboral con gate de revisión obligatorio. Valores actualizados 2026: salario mínimo $315.04, UMA $117.31.

**9 skills:** cold-start-interview, calculadora-liquidacion, despido-injustificado-triage, conciliacion-prejudicial, demanda-laboral-drafter, derechos-trabajador-qa, trabajador-hogar, plataformas-digitales, accidente-trabajo.

### ✅ Víctimas DDHH (`victimas-ddhh`)

Para víctimas de delitos y violaciones a derechos humanos: desaparición forzada, violencia de género, tortura, feminicidio, desplazamiento forzado.

Diseñado con enfoque de trauma informado: prioriza la seguridad, no revictimiza, respeta la autonomía de la víctima, y siempre refiere a acompañamiento psicológico además de legal. Incluye la regla crítica de desaparición ("NO esperar 72 horas — la búsqueda debe iniciar de inmediato"), rutas completas para violencia de género con órdenes de protección, registro en RENAVI, reparación integral con los 5 componentes de la Corte IDH, y vías internacionales (CIDH, CED, Corte IDH).

**9 skills:** cold-start-interview, que-hago-si, desaparicion-forzada, violencia-genero, registro-victimas, denuncia-penal, reparacion-integral, amparo-victimas, medidas-proteccion.

### 🚧 Emprendedor MX (`emprendedor-mx`) — En desarrollo

Para emprendedores y pequeños negocios: constitución de sociedades, alta en SAT/RFC, IMSS patronal, permisos municipales, propiedad intelectual (IMPI), contratos comerciales, y opciones de financiamiento.

---

## Arquitectura técnica

```
USUARIO                    WHATSAPP             SERVIDOR OSC             CLAUDE API
(celular)                  (Meta Cloud)         (Python/Flask)           (Anthropic)

Escribe mensaje  ───►  WhatsApp Cloud API  ───►  Webhook  ───►  API /v1/messages
                                                                 + plugins como
                       Recibe respuesta   ◄───  Responde  ◄───   system prompt
                       en su celular             vía API          (prompt caching)
```

El servidor carga los archivos del plugin (CLAUDE.md, skills, references) como system prompt de Claude. Usa prompt caching para reducir costos un 90% en llamadas recurrentes. Redis mantiene el historial de conversación por usuario (TTL 24 horas, datos hasheados). Un módulo de seguridad detecta emergencias antes de llamar a Claude y activa el protocolo de crisis inmediatamente.

### Costos estimados de operación

| Escenario | Costo mensual | Con descuento Nonprofits (75% off) |
|---|---|---|
| OSC mediana: 1,000 consultas/mes | $37 USD (~$740 MXN) | ~$15 USD (~$300 MXN) |
| OSC grande: 10,000 consultas/mes | $350 USD (~$7,000 MXN) | ~$120 USD (~$2,400 MXN) |

Incluye: Claude API (Sonnet 4.6 con caching), hosting (Railway/Render), WhatsApp Cloud API, y Redis.

---

## Modelo de operación: OSC + WhatsApp

El proyecto está diseñado para ser operado por una organización de la sociedad civil (ONG/OSC) que funciona como la cara visible ante los usuarios. La OSC:

1. **Obtiene el número de WhatsApp Business** verificado por Meta a nombre de la organización.
2. **Despliega el servidor** con los plugins configurados para su contexto (estado, tipo de población atendida, servicios locales disponibles).
3. **Supervisa las conversaciones** mediante un panel de métricas anonimizadas y un protocolo de escalamiento a humano para casos complejos o de crisis.
4. **Mantiene actualizado** el contenido legal (valores salariales, reformas, datos institucionales locales).

El sistema no reemplaza el trabajo de la OSC — lo amplifica. Una organización con 3 abogados y horario de 9 a 5 puede, con este sistema, ofrecer orientación de primer nivel las 24 horas a miles de personas simultáneamente, reservando la atención humana para los casos que realmente la necesitan.

### Escalamiento a humano

El bot escala a un ser humano cuando detecta: emergencia activa (violencia, desaparición reciente), solicitud explícita del usuario, caso que excede la orientación de primer nivel, o frustración del usuario. La OSC recibe una notificación vía Slack/email con el resumen de la conversación.

### Privacidad

Las conversaciones se borran automáticamente después de 24 horas. Los números telefónicos se almacenan hasheados. No se guardan nombres ni datos personales. El API de Claude en planes pagos no usa datos de clientes para entrenar modelos. Cumple con la LFPDPPP (Ley Federal de Protección de Datos Personales en Posesión de los Particulares).

---

## Estructura del repositorio

```
justicia-digital-mx/
│
├── README.md                          ← Este archivo
├── LICENSE                            ← Apache 2.0
├── CONTRIBUTING.md                    ← Guía para contribuidores
├── CODE_OF_CONDUCT.md                 ← Código de conducta
├── ROADMAP.md                         ← Hoja de ruta del proyecto
│
├── orientador-ciudadano/              ← Plugin 1: orientación general
│   ├── .claude-plugin/plugin.json
│   ├── CLAUDE.md
│   ├── README.md
│   ├── skills/                        ← 6 skills
│   └── references/                    ← 4 archivos de referencia
│
├── laboral-mx/                        ← Plugin 2: derechos laborales
│   ├── .claude-plugin/plugin.json
│   ├── CLAUDE.md
│   ├── README.md
│   ├── skills/                        ← 9 skills
│   └── references/                    ← 2 archivos de referencia
│
├── victimas-ddhh/                     ← Plugin 3: víctimas y DDHH
│   ├── .claude-plugin/plugin.json
│   ├── CLAUDE.md
│   ├── README.md
│   ├── skills/                        ← 9 skills
│   └── references/                    ← 2 archivos de referencia
│
├── emprendedor-mx/                    ← Plugin 4: emprendedores (en desarrollo)
│
└── docs/
    ├── arquitectura.md                ← Arquitectura técnica detallada
    └── paper-1-outline.md             ← Outline del paper académico
```

---

## Hoja de ruta

### Fase 0 — Fundación (mayo-julio 2026) ← Estamos aquí

- [x] Diseño de arquitectura del ecosistema
- [x] Plugin `orientador-ciudadano` completo (14 archivos)
- [x] Plugin `laboral-mx` completo (14 archivos)
- [x] Plugin `victimas-ddhh` completo (14 archivos)
- [x] Repositorio público en GitHub
- [ ] Identificar OSC aliada para piloto (en proceso)
- [ ] Primeras pruebas con 20-30 usuarios cercanos
- [ ] Completar datos de servicios gratuitos para Puebla

### Fase 1 — Piloto (agosto-diciembre 2026)

- [ ] Plugin `emprendedor-mx` completo
- [ ] Prototipo funcional del bot de WhatsApp
- [ ] Piloto con OSC aliada (Puebla): 50-200 usuarios reales
- [ ] Protocolo de escalamiento a humano implementado
- [ ] Métricas de uso y satisfacción recopiladas
- [ ] Primer paper académico sometido
- [ ] Aplicación a Claude for Open Source (Anthropic)

### Fase 2 — Expansión (enero-julio 2027)

- [ ] Despliegue en producción con OSC(s)
- [ ] Adaptación a 3-5 estados (datos locales de servicios)
- [ ] Variante web (chat embebido en sitio de la OSC)
- [ ] Exploración de audio y lenguas indígenas
- [ ] Segunda publicación académica
- [ ] Presentación en conferencias (LASA, ALAS, o equivalente)

### Fase 3 — Consolidación (agosto 2027-julio 2028)

- [ ] Ecosistema completo: 4 plugins, múltiples OSCs operadoras
- [ ] Comunidad de 20+ contribuidores
- [ ] Kiosco físico piloto (tablet con WiFi en clínica jurídica o DIF)
- [ ] 3+ publicaciones académicas
- [ ] Exploración de conectores especializados (SJF, SIEM, Registro Público)

---

## Cómo contribuir

Buscamos contribuidores con experiencia en:

- **Derecho mexicano** (para validar y expandir el contenido legal de los plugins)
- **Derechos humanos y acompañamiento a víctimas** (para revisar el enfoque de trauma informado)
- **Desarrollo Python** (para construir el servidor de WhatsApp)
- **Comunidades y OSCs** (para pilotar el sistema con usuarios reales)
- **Investigación académica** (para co-autoría en publicaciones)

Lee [CONTRIBUTING.md](CONTRIBUTING.md) para los lineamientos. Todos los contribuidores se adhieren al [Código de Conducta](CODE_OF_CONDUCT.md).

---

## Para OSCs interesadas en operar el bot

Si tu organización atiende víctimas, trabaja con trabajadores, o brinda orientación legal en México, este sistema puede amplificar tu alcance. Lo que necesitas:

1. **Cuenta de Meta Business** verificada (gratuita).
2. **Número de WhatsApp Business** (Meta lo asigna).
3. **Servidor** en la nube (~$5-20 USD/mes en Railway o Render).
4. **API key de Claude** (Anthropic; con descuento de 75% para nonprofits vía Goodstack).
5. **Al menos una persona** que supervise el sistema y responda escalamientos.

El costo total de operación puede ser tan bajo como **$300 MXN al mes** para 1,000 consultas. Contacta al equipo del proyecto para acompañamiento en la implementación.

---

## Marco legal de referencia

Los plugins están construidos sobre el siguiente marco normativo (actualizado a mayo 2026):

- Constitución Política de los Estados Unidos Mexicanos (arts. 1, 17, 20C, 123)
- Ley Federal del Trabajo (reformas hasta 2026, incluyendo Vacaciones Dignas 2023, Ley Silla 2025, Plataformas Digitales 2025-2026, Desconexión Digital 2026)
- Ley General de Víctimas
- Ley General en Materia de Desaparición Forzada de Personas
- Ley General de Acceso de las Mujeres a una Vida Libre de Violencia
- Código Nacional de Procedimientos Penales
- Ley de Amparo
- Convención Americana sobre Derechos Humanos y jurisprudencia de la Corte IDH (Campo Algodonero, Radilla Pacheco, Alvarado Espinoza, Rosendo Cantú, entre otros)

---

## Advertencia importante

**Este proyecto es informativo y orientativo. No constituye asesoría legal.** Las rutas legales descritas son complejas y pueden variar según el caso, la jurisdicción, y las circunstancias. Los plugins orientan y refieren — la decisión final siempre es de la persona, acompañada idealmente por un profesional.

Instituciones de orientación legal gratuita en México:

- **PROFEDET** (laboral): 800 717 2942
- **CEAV** (víctimas): 800 842 8462
- **CNDH** (derechos humanos): 800 715 2000
- **Línea de la Vida** (violencia contra mujeres): 800 911 2511
- **Emergencias:** 911
- **Mecanismo de Protección** (defensores/periodistas): 800 712 0893

---

## Licencia

[Apache License 2.0](LICENSE)

Copyright 2026 Justicia Digital México contributors.

---

## Contexto del proyecto

Justicia Digital México nace como proyecto académico y cívico de un estudiante que quiere contribuir a la mejora del país. Se desarrolla sobre la infraestructura open source de [`anthropic/claude-for-legal`](https://github.com/anthropic/claude-for-legal) (Apache 2.0, lanzado en mayo 2026).

El proyecto se conecta con el trabajo de colectivos de búsqueda de personas desaparecidas, clínicas jurídicas universitarias, y organizaciones de derechos humanos en Puebla, México.

---

*Construido con Claude (Anthropic). Hecho en Puebla, México.*
