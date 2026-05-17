# Orientador Ciudadano México

Plugin de Claude para orientación legal ciudadana en México. Para cualquier persona que tenga un problema y no sepa qué hacer ni a dónde acudir.

## Para quién es

Para cualquier persona en México que tenga un problema legal y no tenga abogado. Para estudiantes que ayudan a su familia. Para clínicas jurídicas que atienden a primera ventanilla. Para servidores públicos de orientación ciudadana. Para periodistas que cubren temas jurídicos. Para activistas que acompañan a víctimas.

No requiere conocimientos legales. Habla en lenguaje cotidiano.

## Qué hace

Este plugin no es un abogado. No te representa. No firma escritos por ti. **No constituye asesoría legal.**

Lo que sí hace:

- Te explica tus derechos en palabras que se entienden.
- Te dice a qué institución acudir según tu problema.
- Te traduce un documento legal que recibiste y no entiendes.
- Te da una estimación de cuánto puede costar un trámite y cómo conseguirlo gratis.
- Te conecta con servicios jurídicos gratuitos en tu estado.

Si tu caso es complejo o urgente, te lo dice directamente y te refiere con un profesional.

## Skills

| Comando | Para qué |
|---|---|
| `/orientador-ciudadano:cold-start-interview` | Configuración inicial — corrélo primero |
| `/orientador-ciudadano:que-hago-si` | Tengo un problema, ¿qué hago? |
| `/orientador-ciudadano:donde-acudo` | ¿A qué institución debo ir? |
| `/orientador-ciudadano:mis-derechos` | ¿Qué derechos tengo en esta situación? |
| `/orientador-ciudadano:entiendo-mi-documento` | Me llegó un documento legal, ¿qué significa? |
| `/orientador-ciudadano:costo-estimador` | ¿Cuánto cuesta este trámite y cómo lo hago gratis? |
| `/orientador-ciudadano:servicios-gratuitos-mapper` | ¿Dónde consigo ayuda legal gratuita? |

## Instalación

### En Claude Cowork

1. Abrir la pestaña Cowork.
2. Click en **Customize** en la barra lateral.
3. Click en **Browse plugins** o **Upload plugin**.
4. Subir el archivo `.zip` del plugin.
5. Correr `/orientador-ciudadano:cold-start-interview` para la configuración inicial.

### En Claude Code

```bash
# Agregar el marketplace (ruta local o URL de GitHub)
/plugin marketplace add <ruta-al-repo>

# Instalar el plugin
/plugin install orientador-ciudadano@justicia-digital-mx

# Reiniciar Claude Code y correr la configuración
/orientador-ciudadano:cold-start-interview
```

## Antes de usar

Corre primero `/orientador-ciudadano:cold-start-interview`. Es una entrevista corta (3–5 minutos) que pregunta:

- En qué estado de la República te encuentras (importa porque hay leyes locales distintas).
- Tu nivel de familiaridad con temas legales (para ajustar el lenguaje).
- Si estás usando el plugin para ti, para alguien que ayudas, o profesionalmente.

Esta información queda guardada en `CLAUDE.md` y todos los skills la leen.

## Para clínicas jurídicas y OSCs

Si trabajas en una clínica universitaria, defensoría, o una organización de la sociedad civil, este plugin puede ser tu primera ventanilla automatizada. Recibe a la persona, hace la primera orientación, identifica el área del derecho, y prepara un resumen estructurado del caso para el abogado que tomará la consulta de fondo.

## Lo que este plugin NO hace

- No genera demandas, denuncias, amparos ni ningún documento que se presente ante una autoridad. Para eso existen otros plugins de Justicia Digital México (`victimas-ddhh`, `laboral-mx`, `amparo-mx`, `litigio-mx`).
- No reemplaza a un abogado.
- No toma decisiones legales por ti.
- No garantiza resultados.
- No sustituye la atención en crisis. Si estás en peligro inmediato, marca 911.

## Disclaimer

Toda orientación que produzca este plugin es informativa. No constituye asesoría legal ni patrocinio jurídico. Las leyes mexicanas cambian: verifica la información con un profesional antes de tomar decisiones importantes. El plugin no se hace responsable de las decisiones que tomes a partir de su orientación.

## Licencia

Apache 2.0. Puedes usar, modificar y distribuir este plugin libremente. Te pedimos que mantengas la atribución y que las modificaciones también sean abiertas para que la comunidad se beneficie.

## Contribuir

Si encuentras un error, una institución que cambió de nombre, una ley que se reformó, o quieres agregar un servicio gratuito de tu estado, abre un Issue o un Pull Request en el repositorio principal.

Las contribuciones son especialmente bienvenidas en:

- Servicios gratuitos por estado (sección `references/servicios-gratuitos-estados.md`).
- Glosario ciudadano — términos legales explicados sin tecnicismos.
- Casos de prueba que muestren cómo responde el plugin a situaciones reales.
