# Justicia Digital México

> Herramientas de IA legal open source para democratizar el acceso a la justicia en México.

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Estado: Alpha](https://img.shields.io/badge/Estado-Alpha-orange)](#estado-del-proyecto)
[![Plugins: 2/10](https://img.shields.io/badge/Plugins-1%2F10-yellow)](#plugins-del-ecosistema)

## Qué es esto

Justicia Digital México es un ecosistema de plugins open source para [Claude](https://claude.ai), diseñados para llevar orientación y herramientas legales a las poblaciones de México históricamente excluidas del sistema de justicia: víctimas de violaciones a derechos humanos, trabajadores informales, emprendedores sin asesoría, comunidades indígenas, migrantes, y cualquier persona que tenga un problema legal y no tenga abogado.

Este proyecto **no pretende sustituir a los abogados**. Pretende que las personas que hoy no tienen acceso a ninguno puedan al menos entender sus derechos, conocer sus opciones, y conectarse con servicios jurídicos gratuitos.

## El problema que abordamos

México tiene una crisis de acceso a la justicia:

- Más del 90% de los delitos no se denuncian (ENVIPE, INEGI).
- México ocupa el lugar 116 de 142 en acceso a justicia civil (World Justice Project).
- Las barreras no son solo económicas: son de conocimiento, de lenguaje procesal, de distancia geográfica y de desconfianza estructural.

Las herramientas existentes están escritas para abogados, en lenguaje técnico, y rara vez consideran la realidad jurídica mexicana (la mayoría de la legal tech disponible está optimizada para el common law estadounidense). Este proyecto cambia eso.

## Plugins del ecosistema

| # | Plugin | Para quién | Estado |
|---|---|---|---|
| 1 | [`orientador-ciudadano`](./orientador-ciudadano/) | Público general — orientación legal en lenguaje cotidiano | ✅ Alpha |
| 2 | `victimas-ddhh` | Víctimas y sus familias | 🚧 En diseño |
| 3 | `laboral-mx` | Trabajadores | ✅ Alpha |
| 4 | `emprendedor-mx` | Emprendedores y PyMEs | 📋 Planeado |
| 5 | `litigio-mx` | Abogados litigantes | 📋 Planeado |
| 6 | `amparo-mx` | Especializado en juicio de amparo | 📋 Planeado |
| 7 | `internacional-ddhh` | Litigio en CIDH y órganos ONU | 📋 Planeado |
| 8 | `internacional-ompi` | Propiedad intelectual ante OMPI | 📋 Planeado |
| 9 | `clinica-juridica-mx` | Clínicas jurídicas universitarias | 📋 Planeado |
| 10 | `estudiante-derecho-mx` | Estudiantes de derecho | 📋 Planeado |

Ver [ROADMAP.md](./ROADMAP.md) para la hoja de ruta detallada.

## Empezar a usarlo

### Si eres una persona que tiene un problema legal

1. Necesitas acceso a [Claude](https://claude.ai) — con una cuenta gratuita es suficiente para empezar.
2. Instala el plugin `orientador-ciudadano` (instrucciones en su [README](./orientador-ciudadano/README.md)).
3. Corre `/orientador-ciudadano:cold-start-interview` para la configuración inicial.
4. Describe tu problema. El plugin te orientará.

### Si trabajas en una clínica jurídica u OSC

Tu organización puede acceder a Claude con tarifas reducidas a través del [programa Claude for Nonprofits](https://www.anthropic.com/pricing) de Anthropic. Una vez instalado, el plugin sirve como **primera ventanilla automatizada** que clasifica casos, identifica urgencias, y prepara resúmenes estructurados para los abogados que toman la consulta de fondo.

### Si eres desarrollador o abogado que quiere contribuir

Ver [CONTRIBUTING.md](./CONTRIBUTING.md).

## Arquitectura

Cada plugin es una carpeta autocontenida con:

```
plugin-name/
├── .claude-plugin/plugin.json   ← Manifiesto
├── README.md                    ← Documentación
├── CLAUDE.md                    ← Perfil de práctica (se llena con cold-start)
├── skills/                      ← Cada skill es un /comando invocable
│   └── skill-name/SKILL.md
└── references/                  ← Corpus normativo y de datos
    └── *.md
```

Todo es Markdown y JSON. No hay código compilado, no hay build step. Cualquier abogado, estudiante o ciudadano puede leer, modificar y mejorar un skill sin saber programar.

Ver [docs/arquitectura.md](./docs/arquitectura.md) para detalles técnicos.

## Estado del proyecto

🟡 **Alpha** — Mayo 2026.

- ✅ Primer plugin (`orientador-ciudadano`) completo y funcional.
- 🚧 Probándose con usuarios reales en Puebla.
- 🚧 Buscando contribuidores para servicios gratuitos por estado.
- 📋 Próximo: `victimas-ddhh` y `laboral-mx`.

## Principios del proyecto

1. **Democratización radical:** Si solo los abogados pueden usar nuestra herramienta, hemos fallado.
2. **Lenguaje ciudadano:** Si la persona no entiende la respuesta, la respuesta está mal.
3. **Servicios gratuitos como regla:** Cada vez que el plugin sugiera contratar abogado, debe mencionar también la opción gratuita correspondiente.
4. **Sin sustitución:** El plugin orienta, no representa. Conecta con abogados, no los reemplaza.
5. **Seguridad primero:** Si detectamos crisis (violencia, desaparición, suicidio, NNA en riesgo), interrumpimos el análisis legal y priorizamos atención inmediata.
6. **Honestidad sobre limitaciones:** No prometemos resultados. No idealizamos servicios saturados. Decimos lo que es.
7. **Comunidad antes que producto:** Open source, contribuciones bienvenidas, transparencia en decisiones de diseño.

## Cómo contribuir

Hay tres formas principales de contribuir:

1. **Datos por estado:** Llenar la información de servicios jurídicos gratuitos de tu estado en [`orientador-ciudadano/references/servicios-gratuitos-estados.md`](./orientador-ciudadano/references/servicios-gratuitos-estados.md).
2. **Nuevos skills o plugins:** Diseñar y proponer skills adicionales. Ver [CONTRIBUTING.md](./CONTRIBUTING.md).
3. **Casos de prueba:** Probar el plugin con situaciones reales y reportar dónde funciona y dónde falla. Ver [SCENARIOS.md](./SCENARIOS.md).

Las contribuciones legales requieren validación por al menos otro abogado o estudiante de derecho avanzado antes de aceptarse. Las contribuciones de servicios por estado se aceptan con verificación de datos.

## Reconocimientos

Este proyecto se construye sobre la arquitectura de [`claude-for-legal`](https://github.com/anthropics/claude-for-legal) de Anthropic (Apache 2.0), adaptada al sistema jurídico mexicano y al derecho internacional.

Inspirado por el trabajo de las organizaciones que día a día sostienen el acceso a la justicia en México: clínicas jurídicas universitarias, defensorías públicas, OSCs como Voz de los Desaparecidos, CMDPDH, Centro Prodh, Tlachinollan, GIRE, Article 19, AsiLegal, CEJIL, y muchas más.

## Disclaimer

Este software es informativo y no constituye asesoría legal. No se asume responsabilidad por decisiones tomadas a partir de la orientación proporcionada por los plugins. Las leyes y procedimientos cambian; verifica con un profesional antes de tomar decisiones importantes.

## Licencia

Apache License 2.0. Ver [LICENSE](./LICENSE).

Puedes usar, modificar y distribuir este proyecto libremente, incluso comercialmente. Te pedimos que mantengas la atribución y que las modificaciones también sean abiertas para que la comunidad se beneficie.

## Contacto

- **Issues:** Usa GitHub Issues para reportar bugs, sugerir mejoras o proponer skills.
- **Discusiones:** GitHub Discussions para conversaciones abiertas.
- **Mantenedor:** [Tu nombre / contacto]

---

*Este proyecto se construye con la convicción de que el acceso a la justicia no debería depender de tener dinero, conexiones o conocimiento técnico previo.*
