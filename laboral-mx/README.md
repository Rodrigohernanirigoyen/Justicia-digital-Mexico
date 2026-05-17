# Laboral MX — Plugin de derechos laborales para trabajadores en México

Plugin de Claude para orientación laboral, cálculo de liquidaciones, y preparación de demandas ante tribunales laborales. Para trabajadores que no saben qué les corresponde y para abogados que necesitan herramientas de cálculo rápido.

## Para quién es

Para cualquier trabajador en México (formal o informal) que enfrente un problema laboral: despido, falta de pago de prestaciones, accidente de trabajo, discriminación, o simplemente quiere saber qué derechos tiene.

También para abogados laboralistas, estudiantes en prácticas, y personal de PROFEDET y procuradurías locales que necesiten herramientas de cálculo y triage.

## Qué hace

| Comando | Para qué |
|---|---|
| `/laboral-mx:cold-start-interview` | Configuración inicial |
| `/laboral-mx:calculadora-liquidacion` | Calcula liquidación/indemnización por despido con valores 2026 |
| `/laboral-mx:despido-injustificado-triage` | Evalúa si el despido fue justificado o injustificado |
| `/laboral-mx:demanda-laboral-drafter` | Genera borrador de demanda ante Tribunal Laboral |
| `/laboral-mx:conciliacion-prejudicial` | Prepara solicitud de conciliación (obligatoria antes de demandar) |
| `/laboral-mx:derechos-trabajador-qa` | Q&A de derechos laborales |
| `/laboral-mx:trabajador-hogar` | Régimen especial de personas trabajadoras del hogar |
| `/laboral-mx:plataformas-digitales` | Derechos de repartidores y trabajadores de apps (reforma 2025-2026) |
| `/laboral-mx:accidente-trabajo` | Ruta para reportar riesgo de trabajo ante IMSS |

## Valores actualizados (2026)

- Salario mínimo general: $315.04 MXN/día.
- Salario mínimo Zona Libre de la Frontera Norte: $440.87 MXN/día.
- UMA diaria (desde 1 de febrero 2026): $117.31 MXN.
- Vacaciones primer año: 12 días (reforma 2023).
- Prima vacacional mínima: 25%.
- Aguinaldo mínimo: 15 días.

## Advertencia importante sobre la calculadora

La calculadora de liquidación produce **estimaciones** basadas en la información que proporciona el usuario. El cálculo final puede variar por:

- Componentes variables del salario (comisiones, propinas, bonos).
- Prestaciones superiores a las de ley (convenios colectivos, contratos individuales mejorados).
- Salarios caídos que dependen de la duración del proceso.
- Interpretaciones judiciales locales.

**El resultado de la calculadora NO sustituye un cálculo profesional.** Siempre debe ser verificado por un abogado laboralista o por PROFEDET antes de usarse en un procedimiento legal.

## Advertencia sobre la demanda laboral

El skill `demanda-laboral-drafter` genera un **borrador** orientativo. Este borrador:

- **NO está listo para presentarse** ante un tribunal sin revisión profesional.
- Requiere verificación de hechos, cálculos, y fundamentos por un abogado.
- Debe adaptarse a las particularidades del caso concreto.
- Tiene un gate de revisión obligatorio antes de su entrega al usuario.

Si no tienes abogado, PROFEDET (800 717 2942) puede revisar y presentar la demanda por ti, gratuitamente.

## Instalación

Ver instrucciones generales en el [README principal](../README.md).

## Disclaimer

Este plugin es informativo. No constituye asesoría legal laboral. Las leyes y criterios judiciales cambian. Verifica con un abogado laboralista o con PROFEDET antes de tomar decisiones.

## Licencia

Apache 2.0
